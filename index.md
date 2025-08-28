---
layout: splash
title: "Christian Aguirre"
header:
  overlay_color: "#000"
  overlay_filter: 0.65
  overlay_image: /assets/images/hero-bg.jpg
  actions:
    - label: "My Projects"
      url: "/projects/"
excerpt: "Conversational coder and analyst, inspired by tough problems."
---

<div class="intro-wrap">
  <div class="intro-left">
    <h2>I am</h2>
    <h1>Christian Aguirre</h1>
    <p>Conversational coder and analyst, inspired by tough problems.</p>
    <p><a class="btn btn--primary" href="/projects/">My projects</a></p>
  </div>
  <div class="intro-right">
    <img src="/assets/images/headshot.jpg" alt="Christian Aguirre" class="hero-avatar">
  </div>
</div>

{% raw %}{% include feature_row id="areas" type="center" %}{% endraw %}

## My Latest Projects

{% assign recent = site.projects | slice: 0, 3 %}
<div class="cards">
{% for item in recent %}
  <article class="card">
    <a href="{{ item.url | relative_url }}">
      {% if item.thumbnail %}
        <img src="{{ item.thumbnail | relative_url }}" alt="{{ item.title }}">
      {% endif %}
      <h3>{{ item.title }}</h3>
      <p>{{ item.excerpt | default: item.description }}</p>
    </a>
  </article>
{% endfor %}
</div>
