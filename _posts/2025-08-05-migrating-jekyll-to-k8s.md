---
layout: post
title: "Overengineering for Science: Migrating a Jekyll Blog to a Local Kubernetes Homelab"
date: 2025-08-05
categories: [homelab, kubernetes, jekyll, monitoring]
tags: [microk8s, grafana, git-worktree, debugging]
---

I am a security researcher, which means I have a natural tendency to take something simple and make it complex for the sake of learning how it breaks. 

My personal blog runs on Jekyll. The standard workflow is simple: run `jekyll serve`, check `localhost:4000`, and push to Git. But I wanted to start building a proper Kubernetes homelab. I decided to make my blog the "Hello World" of this infrastructure.

The goal? A local Kubernetes cluster that runs two versions of my site simultaneously (Main vs. Dev), accessible via custom domains, and fully monitored with Prometheus and Grafana.

Here is the log of how I got there, structured as a Q&A of the problems I faced along the way.

---

### Phase 1: The Inner Loop

**Q: How do I run a local instance in Kubernetes but see changes instantly (hot-reload) without rebuilding Docker images every time?**

The "proper" K8s way is to build a container image, push it to a registry, and update the Deployment. That is too slow for writing CSS or blog posts.

The solution is using a **HostPath Volume**. This punches a hole through the container isolation, mounting my local directory directly into `/srv/jekyll` inside the pod.

However, standard file watching (inotify) often breaks across virtualization boundaries. The trick is `force_polling`.

```yaml
# k8s-local-dev.yaml snippet
spec:
  containers:
  - image: jekyll/jekyll:latest
    command: ["jekyll", "serve", "--force_polling"] # <--- Critical for hot-reload
    volumeMounts:
    - name: source
      mountPath: /srv/jekyll
  volumes:
  - name: source
    hostPath:
      path: /home/user/projects/my-blog
      type: Directory
```
---

### Phase 2: Dual-Stack Deployment

**Q: I want to work on a feature branch while keeping the stable site running. How do I make Jekyll serve a different Git branch locally?**

Jekyll doesn't know about Git branches; it just builds the folder it lives in. To run two branches at once, I needed two physical folders.

Instead of cloning the repo twice (messy), I used Git Worktrees. This allows multiple working directories linked to the same .git history.
````Bash

# In the main repo folder (branch: main)
git worktree add ../my-blog-dev experimental-feature
````

Now I have two folders: my-blog (Main) and my-blog-dev (Dev). I created a Kubernetes manifest with two Deployments and two Services (jekyll-main and jekyll-dev), each mounting their respective hostPath.

---

### Phase 3: The "Dependency Hell" (Ruby & Alpine)

**Q: The pods are crashing with "Broken Pipe" or "Missing Dependency" errors. Why?**

This was the hardest part of the migration. The official jekyll/jekyll:latest image recently upgraded to Ruby 3.1, which introduced two breaking changes:

    Missing webrick: Ruby 3.0 removed webrick from the standard library, but Jekyll 4.2 still needs it to serve locally.

    Architecture Mismatch: My Ubuntu host uses glibc, but the container uses Alpine Linux (musl). The modern sass-embedded compiler tries to run a binary helper that crashes in this hybrid environment.

The Fix: I had to update my Gemfile to explicitly add webrick and downgrade the Sass converter to the pure-Ruby version (v2.0) to bypass the binary incompatibility.

````Ruby

# Gemfile
source "[https://rubygems.org](https://rubygems.org)"
gem "jekyll", "~> 4.2.2"
gem "minima", "~> 2.5" 
gem "webrick" # Fix for Ruby 3.0+
gem "jekyll-sass-converter", "~> 2.0" # Fix for Alpine/Musl crash
````

After deleting Gemfile.lock and restarting the pods, the sites came online.

---

### Phase 4: Networking & Ingress

**Q: I am tired of remembering localhost:30000 and localhost:30001. Can I use real domain names?**

Yes. I enabled the NGINX Ingress controller in MicroK8s (microk8s enable ingress) and updated my /etc/hosts file:

````Plaintext

127.0.0.1  blog.local dev.blog.local
````
Then, I created an Ingress resource to route traffic:
````YAML

apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: jekyll-ingress
spec:
  rules:
  - host: blog.local
    http:
      paths:
      - path: /
        backend: { service: { name: jekyll-main-svc, port: { number: 4000 } } }
  - host: dev.blog.local
    http:
      paths:
      - path: /
        backend: { service: { name: jekyll-dev-svc, port: { number: 4000 } } }
````

Now accessing http://blog.local hits the stable site, and http://dev.blog.local hits the worktree.

---

### Phase 5: Monitoring the Homelab

**Q: How do I visualize the health of these sites in Grafana?**

I enabled the observability addon in MicroK8s, which provides Prometheus and Grafana. However, standard monitoring only checks if the Pod is running, not if the Website is returning 200 OK.

I installed the Prometheus Blackbox Exporter to "ping" the internal services.

The "Deduplication" Gotcha: Initially, I tried to use a ServiceMonitor. However, Prometheus would scrape the Blackbox exporter, get results for both sites, and discard one because it thought they were duplicates (same job, same instance).

I had to switch to a Probe resource and explicitly force Prometheus to use the target URL as the instance label using metricRelabelings.

````YAML

apiVersion: [monitoring.coreos.com/v1](https://monitoring.coreos.com/v1)
kind: Probe
spec:
  prober:
    url: prometheus-blackbox-exporter.observability.svc.cluster.local:9115
  targets:
    staticConfig:
      static:
      - [http://jekyll-main-svc.default.svc.cluster.local:4000](http://jekyll-main-svc.default.svc.cluster.local:4000)
      - [http://jekyll-dev-svc.default.svc.cluster.local:4000](http://jekyll-dev-svc.default.svc.cluster.local:4000)
  metricRelabelings:
    # This prevents Grafana from merging the two sites into one line
    - sourceLabels: [__param_target]
      targetLabel: instance
````

---

### The Result

I now have a fully over-engineered, local development environment.

    Workflow: I edit files in VS Code.

    Pipeline: Kubernetes mounts the changes via hostPath.

    Engine: Jekyll hot-reloads inside the pod.

    Verification: I check dev.blog.local for changes.

    Monitoring: Grafana alerts me if I break the build (non-200 response)