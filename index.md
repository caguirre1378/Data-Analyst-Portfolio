---
layout: single
title: ""
classes: wide
---

<section class="section-white home-hero">
  <div class="intro-wrap">
    <div class="intro-left">
      <h1>Christian Aguirre</h1>
      <p>Data analyst focused on operations and decision support. I build dashboards, pipelines, and models that help teams act with clarity.</p>
      <p>
        <a class="btn btn--primary" href="/projects/">View Projects</a>
        <a class="btn" href="/resume/">Resume</a>
      </p>
    </div>
    <div class="intro-right">
      <img src="/assets/images/headsot.jpg" alt="Christian Aguirre" class="hero-avatar">
    </div>
  </div>
</section>



<section class="section-gray">
  <h2>Areas of Interest</h2>
  <p class="section-sub">Take a look at some of the things I love working on.</p>

  <div class="topics">
    <article class="topic">
      <div class="topic__icon"><i class="fas fa-cloud"></i></div>
      <h3>Cloud Compute</h3>
      <p>Servers for storage, model training, and deployment.</p>
    </article>

  <article class="topic">
      <div class="topic__icon"><i class="fas fa-language"></i></div>
      <h3>NLP</h3>
      <p>Techniques to make sense of human text and conversations.</p>
    </article>

  <article class="topic">
      <div class="topic__icon"><i class="fas fa-robot"></i></div>
      <h3>Machine Learning</h3>
      <p>From the math to practical modeling and evaluation.</p>
    </article>

   <article class="topic">
      <div class="topic__icon"><i class="fas fa-project-diagram"></i></div>
      <h3>Parallel Computing</h3>
      <p>Hadoop/Hive workflows for large-scale data processing.</p>
    </article>

   <article class="topic">
      <div class="topic__icon"><i class="fas fa-rocket"></i></div>
      <h3>Model Deployment</h3>
      <p>Shipping models with REST APIs, CI/CD, and monitoring.</p>
    </article>

  <article class="topic">
      <div class="topic__icon"><i class="fas fa-chart-line"></i></div>
      <h3>Data Analytics</h3>
      <p>Clear, decision-ready visuals and storytelling with data.</p>
    </article>
  </div>
</section>

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
