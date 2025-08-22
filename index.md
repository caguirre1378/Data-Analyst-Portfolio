---
layout: splash
title: "Christian Aguirre"
subtitle: "Data Analyst · SQL · Tableau · Python"
header:
  overlay_color: "#000"
  overlay_filter: "0.55"
  overlay_image: /assets/images/header-bg.jpg   # or remove this line
  actions:
    - label: "MY PROJECTS"
      url: "/portfolio/"
      class: "btn--primary"

# --- 8 “Areas of Interest” items (icons + short text)

# Row 1 (3 items)
areas_row1:
  - title: "Cloud Compute"
    excerpt: "Servers for storage, model training, and deployment."
    icon: "fas fa-cloud"
  - title: "NLP"
    excerpt: "Techniques to make sense of human text."
    icon: "fas fa-language"
  - title: "Machine Learning"
    excerpt: "I like the math, theory, and implementation."
    icon: "fas fa-robot"

# Row 2 (3 items)
areas_row2:
  - title: "Parallel Computing"
    excerpt: "Hadoop/Hive experience for large-scale data."
    icon: "fas fa-project-diagram"
  - title: "Model Deployment"
    excerpt: "Production ML via REST APIs and CI/CD."
    icon: "fas fa-rocket"
  - title: "Data Analytics"
    excerpt: "Clear, compelling stories with data."
    icon: "fas fa-chart-bar"

---

<!-- Intro blurb under the hero -->
Welcome! I analyze data to drive decisions. Explore my interests and recent work below.

## Areas of Interest
{% comment %}
We render the 8 items as a clean icon grid using feature_row.
{% endcomment %}
{% include feature_row id="areas" type="icon" %}

## My Latest Projects
{% include feature_row id="latest" type="left" %}
