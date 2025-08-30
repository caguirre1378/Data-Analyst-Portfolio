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
      <div class="topic__icon"><i class="fas fa-broom"></i></div>
      <h3>Data Cleaning & Preparation</h3>
      <p>Wrangled raw datasets using SQL, Excel, and Python to get them ready for analysis or dashboards.</p>
    </article>

    <article class="topic">
      <div class="topic__icon"><i class="fas fa-database"></i></div>
      <h3>SQL Querying</h3>
      <p>Built complex queries with joins, CTEs, and aggregations to power dashboards and reporting tools.</p>
    </article>

    <article class="topic">
      <div class="topic__icon"><i class="fas fa-code"></i></div>
      <h3>Python Analytics & Modeling</h3>
      <p>Used pandas, scikit-learn, and SHAP to model churn, explain predictions, and drive decisions.</p>
    </article>

    <article class="topic">
      <div class="topic__icon"><i class="fas fa-chart-line"></i></div>
      <h3>Tableau Dashboards</h3>
      <p>Created visualizations that highlight trends, monitor KPIs, and support operational strategy.</p>
    </article>

    <article class="topic">
      <div class="topic__icon"><i class="fas fa-file-excel"></i></div>
      <h3>Excel Automation</h3>
      <p>Developed trackers and reporting tools using formulas, VBA, and Power Query for recurring tasks.</p>
    </article>

    <article class="topic">
      <div class="topic__icon"><i class="fas fa-project-diagram"></i></div>
      <h3>End-to-End Projects</h3>
      <p>Led projects from data sourcing to model deployment — shared through GitHub and portfolio site.</p>
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
