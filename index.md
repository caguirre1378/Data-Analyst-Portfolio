---
layout: single
title: ""
classes: wide
---

<section class="section-white">
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
</section>

<div class="section-gray">
  <h2>Areas of Interest</h2>
  <p class="section-sub">Take a look at some of the things I love working on.</p>
  {% include feature_row feature_row=site.data.features.areas type="center" %}
</div>



<section class="section-white">
  <h2>My Latest Projects</h2>
  <p class="section-sub">Take a look at my recent work.</p>

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
</section>
