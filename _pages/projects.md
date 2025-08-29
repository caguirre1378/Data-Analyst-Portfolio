---
permalink: /projects/
title: "Portfolio"
layout: single
classes: wide
---

<div class="section-white">
  <h2>Portfolio</h2>
  <p class="section-sub">Selected projects across analytics, SQL, optimization, and machine learning.</p>

  <!-- Quick “filters” (anchors) -->
  <p style="text-align:center;margin-bottom:1.5rem">
    <a class="pill" href="#ml">ML & Modeling</a>
    <a class="pill" href="#analytics">Analytics (R & Tableau)</a>
    <a class="pill" href="#sql">SQL & Databases</a>
    <a class="pill" href="#or">Optimization & OR</a>
  </p>

  <!-- ML & Modeling -->
  <h3 id="ml" style="text-align:center;margin-top:2rem;">ML & Modeling</h3>
  <div class="cards">
  {% assign items = site.projects | where: "category", "ML & Modeling" | sort: "weight" %}
  {% for item in items %}
    <article class="card">
      <a href="{{ item.url | relative_url }}">
        {% if item.thumbnail %}<img src="{{ item.thumbnail | relative_url }}" alt="{{ item.title }}">{% endif %}
        <h3>{{ item.title }}</h3>
        <p>{{ item.excerpt | default: item.description }}</p>
      </a>
    </article>
  {% endfor %}
  </div>

  <!-- Analytics (R & Tableau) -->
  <h3 id="analytics" style="text-align:center;margin-top:3rem;">Analytics (R & Tableau)</h3>
  <div class="cards">
  {% assign items = site.projects | where: "category", "Analytics (R & Tableau)" | sort: "weight" %}
  {% for item in items %}
    <article class="card">
      <a href="{{ item.url | relative_url }}">
        {% if item.thumbnail %}<img src="{{ item.thumbnail | relative_url }}" alt="{{ item.title }}">{% endif %}
        <h3>{{ item.title }}</h3>
        <p>{{ item.excerpt | default: item.description }}</p>
      </a>
    </article>
  {% endfor %}
  </div>

  <!-- SQL & Databases -->
  <h3 id="sql" style="text-align:center;margin-top:3rem;">SQL & Databases</h3>
  <div class="cards">
  {% assign items = site.projects | where: "category", "SQL & Databases" | sort: "weight" %}
  {% for item in items %}
    <article class="card">
      <a href="{{ item.url | relative_url }}">
        {% if item.thumbnail %}<img src="{{ item.thumbnail | relative_url }}" alt="{{ item.title }}">{% endif %}
        <h3>{{ item.title }}</h3>
        <p>{{ item.excerpt | default: item.description }}</p>
      </a>
    </article>
  {% endfor %}
  </div>

  <!-- Optimization & OR -->
  <h3 id="or" style="text-align:center;margin-top:3rem;">Optimization & OR</h3>
  <div class="cards">
  {% assign items = site.projects | where: "category", "Optimization & OR" | sort: "weight" %}
  {% for item in items %}
    <article class="card">
      <a href="{{ item.url | relative_url }}">
        {% if item.thumbnail %}<img src="{{ item.thumbnail | relative_url }}" alt="{{ item.title }}">{% endif %}
        <h3>{{ item.title }}</h3>
        <p>{{ item.excerpt | default: item.description }}</p>
      </a>
    </article>
  {% endfor %}
  </div>
</div>
