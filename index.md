---
layout: single
title: ""          # hide the big page title
classes: wide
---

<div class="intro-wrap">
  <div class="intro-left">
    <h2>I am</h2>
    <h1>Christian Aguirre</h1>
    <p>Conversational coder and analyst, inspired by tough problems.</p>
    <p><a class="btn btn--primary" href="/projects/">My Projects</a></p>
  </div>
  <div class="intro-right">
    <img src="/assets/images/headshot.jpg" alt="Christian Aguirre" class="hero-avatar">
  </div>
</div>

## Areas of Interest
{% include feature_row id="areas" type="center" %}

## My Latest Projects
{% assign recent = site.projects | slice: 0, 3 %}
<div class="cards">
{% for item in recent %}
  <article class="card">
    <a href="{{ item.url | relative_url }}">
      {% if item.thumbnail %}<img src="{{ item.thumbnail | relative_url }}" alt="{{ item.title }}">{% endif %}
      <h3>{{ item.title }}</h3>
      <p>{{ item.excerpt | default: item.description }}</p>
    </a>
  </article>
{% endfor %}
</div>
