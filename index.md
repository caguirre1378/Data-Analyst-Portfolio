---
layout: splash
title: "Christian Aguirre"
subtitle: "Data Analyst · SQL · Tableau · Python"
classes: wide      # we'll also force wide via CSS in step C
header:
  overlay_color: "#000"
  overlay_filter: "0.55"
  overlay_image: /assets/images/header-bg.jpg
  actions:
    - label: "MY PROJECTS"
      url: "/portfolio/"
      class: "btn--primary"

# Row 1 (3 cards)
areas_row1:
  - title: "Cloud Compute"
    excerpt: "Servers for storage, model training, and deployment."
    icon: "fas fa-cloud"
  - title: "NLP"
    excerpt: "Techniques to make sense of human text."
    icon: "fas fa-language"
  - title: "Machine Learning"
    excerpt: "Math, theory, implementation."
    icon: "fas fa-robot"

# Row 2 (3 cards)
areas_row2:
  - title: "Parallel Computing"
    excerpt: "Hadoop/Hive for large-scale data."
    icon: "fas fa-project-diagram"
  - title: "Model Deployment"
    excerpt: "Production ML via REST APIs and CI/CD."
    icon: "fas fa-rocket"
  - title: "Data Analytics"
    excerpt: "Clear, compelling stories with data."
    icon: "fas fa-chart-bar"

# Latest projects (image tiles)
latest:
  - title: "Telco Customer Churn"
    excerpt: "Modeling with SHAP explainability."
    image_path: /assets/images/Telco Splash.png
    url: /projects/telco-churn/
    btn_label: "Read case study"
    btn_class: "btn--primary"
  - title: "Cyclistic Rider Behavior"
    excerpt: "R + Tableau: usage patterns that drive conversion."
    image_path: /assets/images/Cyclist Splash.png
    url: /projects/cyclistic/
    btn_label: "Open project"
    btn_class: "btn--primary"
  - title: "Bellabeat Usage Analysis"
    excerpt: "Wellness insights from Fitbit data."
    image_path: /assets/images/Bellabeat Splash.png
    url: /projects/bellabeat/
    btn_label: "Open project"
    btn_class: "btn--primary"
---

Welcome! I analyze data to drive decisions. Explore my interests and recent work below.

## Areas of Interest
{% include feature_row id="areas_row1" type="icon" class="ai-grid" %}
{% include feature_row id="areas_row2" type="icon" class="ai-grid" %}

## My Latest Projects
{% assign latest = site.projects | sort: 'date' | reverse | slice: 0, 3 %}
<div class="grid__wrapper">
  {% for doc in latest %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>

