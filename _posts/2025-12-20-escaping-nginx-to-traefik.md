---
title: "Escaping the Ingress Apocalypse: Why I Fled to Traefik"
date: 2025-12-20
categories: [homelab, kubernetes, jekyll, monitoring, load balancer]
tags: [microk8s, ingress, traefik, metallb]
---

# Escaping the Ingress Apocalypse: Why I Fled to Traefik

In my previous post, I successfully over-engineered my simple Jekyll blog into a dual-stack, hot-reloading Kubernetes cluster. I had Git Worktrees, I had Prometheus probes, and I had the industry-standard NGINX Ingress controller directing traffic. It was stable. It was functional.

And then I read the news.

The Kubernetes community dropped a bombshell: **Ingress NGINX is being retired in March 2026.** No more updates. No more bug fixes. No more security patches. Apparently, maintaining the backbone of the internet with two guys working nights and weekends isn't sustainable. Who knew?

As a security researcher, I heard "End of Life" and "Unpatched CVEs," and my fight-or-flight response kicked in. I didn't just want to migrate; I wanted to abandon ship before the "IngressNightmare" hit.

I looked at my options. I could switch to F5’s corporate NGINX, or HAProxy, Kong, but I wanted something shiny. I wanted "Cloud Native." I wanted **Traefik**.

While NGINX is like a classic car that's about to be banned from the road for emissions violations, Traefik is a Tesla. It watches the Kubernetes API and reconfigures itself instantly. No restarts. No blips. Just vibes.

So, purely for "security reasons" (and definitely not because I just wanted to play with new toys), I decided to migrate my entire infrastructure. Here is the chronicle of my survival.

## Step 1: The Eviction Notice

First, I had to remove the doomed NGINX controller. You can’t have two traffic cops standing in the same intersection—especially when one of them is scheduled for retirement.

```bash
microk8s disable ingress

```
Then, I welcomed the new guard:

```bash
microk8s enable traefik

```

## Step 2: The "Why is Everything Broken?" Phase (Enter MetalLB)

After enabling Traefik, I sat back, crossed my arms, and waited for my websites (`blog.local` and `dev.blog.local`) to load.

Nothing happened.

I checked the service status:

```bash
microk8s kubectl get svc -n traefik

```

**Status:** `Pending`.

See, NGINX "cheats." In MicroK8s, it binds to your host network (localhost) like a barnacle. Traefik behaves like a "proper" cloud Load Balancer—it sits there politely waiting for an external IP address. Since I’m running this on a server in my house and not on AWS, nobody was there to give it one.

I had to install **MetalLB** to act as the "IP Address Giver." My server sits at `192.168.1.183`, so I gave Kubernetes a little playground range of IPs (.240 to .250) to mess with.

```bash
microk8s enable metallb:192.168.1.240-192.168.1.250

```

Thirty seconds later, Traefik grabbed `192.168.1.240`. We were back in business.

## Step 3: Speaking Traefik's Language (IngressRoutes)

Traefik doesn't use standard "Ingress" yaml files; it prefers its own Custom Resource Definition (CRD) called `IngressRoute`. It sounds scary, but it’s actually cleaner.

### The Homepage

I created `proxy-homepage.yaml` to route `dashboard.local` to my internal service.

```yaml
apiVersion: traefik.containo.us/v1alpha1
kind: IngressRoute
metadata:
  name: homepage-dashboard
  namespace: default
spec:
  entryPoints:
    - web
  routes:
  - match: Host(`dashboard.local`)
    kind: Rule
    services:
    - name: homepage-svc
      port: 3000

```

### The Blogs (Main & Dev)

I migrated my main blog and the dev worktree I set up in the last post. Notice how readable this is? No annotation spaghetti.

```yaml
apiVersion: traefik.containo.us/v1alpha1
kind: IngressRoute
metadata:
  name: jekyll-routes
  namespace: default
spec:
  entryPoints:
    - web
  routes:
  - match: Host(`blog.local`)
    kind: Rule
    services:
    - name: jekyll-main-svc
      port: 4000
  - match: Host(`dev.blog.local`)
    kind: Rule
    services:
    - name: jekyll-dev-svc
      port: 4000

```

### The Bonus Dashboard

Traefik has its own dashboard built-in. Obviously, I enabled it immediately because I am addicted to graphs.

```yaml
apiVersion: traefik.containo.us/v1alpha1
kind: IngressRoute
metadata:
  name: traefik-dashboard
  namespace: kube-system
spec:
  entryPoints:
    - web
  routes:
  - match: Host(`traefik.local`)
    kind: Rule
    services:
    - name: api@internal
      kind: TraefikService

```

## Step 4: The "Oh God, Where is Grafana?" Incident

I applied all the YAMLs, felt like a genius, and then realized I had nuked access to my monitoring stack. Grafana was unreachable.

*Panic ensued.*

I forgot that Grafana lives in the `observability` namespace. Traefik can’t route traffic if it doesn't know where to look. I had to quickly whip up a `proxy-grafana.yaml`:

```yaml
apiVersion: traefik.containo.us/v1alpha1
kind: IngressRoute
metadata:
  name: grafana-route
  namespace: observability # <--- The critical part I forgot
spec:
  entryPoints:
    - web
  routes:
  - match: Host(`grafana.local`)
    kind: Rule
    services:
    - name: kube-prom-stack-grafana
      port: 80

```

## Step 5: The Poor Man's DNS (/etc/hosts)

Finally, because I don’t have a real enterprise DNS server at home (yet—give me a week), I had to tell my computer that these fancy domains live at the new MetalLB IP address (`192.168.1.240`), not localhost (`127.0.0.1`).

```bash
sudo nano /etc/hosts

```

I pasted this in, feeling like a hacker from the 90s:

```text
192.168.1.240   dashboard.local blog.local dev.blog.local traefik.local grafana.local

```

## The Verdict

Traefik is sleek, dynamic, and the dashboard makes me feel like I’m piloting a spaceship. The migration took a bit of YAML-fu and some networking troubleshooting, but my cluster is now officially "Cloud Native."

Now, if you'll excuse me, I'm going to go stare at the Traefik dashboard and watch the request count go up by 1 every time I hit refresh.

Next up: I’m still currently working on deploying a purposefully vulnerable website to properly test my security skills in this new cluster. Stay tuned.
