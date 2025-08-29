---
layout: single
title: "Portfolio"
permalink: /projects/
classes: wide
---

<p class="section-sub">Selected projects across analytics, SQL, optimization, and machine learning.</p>

{% assign groups = "ML & Modeling:ml|Analytics (R & Tableau):analytics|SQL & Databases:sql|Optimization & OR:or" | split: "|" %}

{% for g in groups %}
  {% assign parts = g | split: ":" %}
  {% assign label = parts[0] %}
  {% assign key = parts[1] %}

### {{ label }}

<div class="cards">
{% assign items = site.projects | where_exp: "p","p.category contains key" | sort: "weight" %}
{% for item in items %}
  <article class="card">
    <a href="{{ item.url | relative_url }}">
      {% if item.thumbnail %}
        <img src="{{ item.thumbnail | relative_url }}" alt="{{ item.title }}">
      {% endif %}
      <h3>{{ item.title }}</h3>
      <p>{{ item.goal | default:item.excerpt | markdownify | strip_html }}</p>
    </a>
  </article>
{% endfor %}
</div>

{% endfor %}
