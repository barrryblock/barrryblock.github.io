---
layout: default
title: Blog
permalink: /blog/
---

# Blog Posts

<p>Welcome to my blog, where I share insights on <strong>Cyber Threat Intelligence, Security Automation, Risk Mitigation</strong>, and my journey through <strong>MSc in Cyber Security Engineering</strong>. I also discuss the key modules I studied, my master's thesis, and the valuable lessons I learned throughout the program.</p>

<p>For more details about my background and research, visit the <a href="/about">About Me</a> page.</p>

<h2>MSc Blogs</h2>
<ul>
  {% for post in site.posts %}
    {% if post.categories contains "MSc" %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a> – {{ post.date | date: "%B %d, %Y" }}
      </li>
    {% endif %}
  {% endfor %}
</ul>

<h2>Other Blogs</h2>
<ul>
  {% for post in site.posts %}
    {% unless post.categories contains "MSc" %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a> – {{ post.date | date: "%B %d, %Y" }}
      </li>
    {% endunless %}
  {% endfor %}
</ul>
>



