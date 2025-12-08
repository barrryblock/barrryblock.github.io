---
layout: default
title: Blog Posts
permalink: /blog/
---

<p>Welcome to my blog, where I share insights on <strong>Cyber Threat Intelligence, Security Automation, Risk Mitigation</strong>, and my journey through <strong>MSc in Cyber Security Engineering</strong>. I also discuss the key modules I studied, my master's thesis, and the valuable lessons I learned throughout the program.</p>

<p>For more details about my background and research, visit the <a href="/about">About Me</a> page.</p>

<h2>Opinion Pieces</h2>
<ul>
  {% for post in site.posts %}
    {% if post.categories contains "Opinion" %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a> – {{ post.date | date: "%B %d, %Y" }}
      </li>
    {% endunless %}
  {% endfor %}
</ul>

<h2>Homelab Blogs</h2>
<ul>
  {% for post in site.posts %}
    {% if post.categories contains "homelab" %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a> – {{ post.date | date: "%B %d, %Y" }}
      </li>
    {% endunless %}
  {% endfor %}
</ul>

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




