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
areas:
  - title: "Cloud Compute"
    excerpt: "I maintain servers for database storage, model training, and model deployment."
    icon: "fas fa-cloud"
  - title: "NLP"
    excerpt: "I apply NLP techniques to make sense of human interactions."
    icon: "fas fa-language"
  - title: "Machine Learning"
    excerpt: "More than an API call: I like the math, theory, and implementation."
    icon: "fas fa-robot"
  - title: "Parallel Computing"
    excerpt: "I extract data from Hadoop ecosystems using the HIVE framework."
    icon: "fas fa-project-diagram"
  - title: "Model Deployment"
    excerpt: "Production ML via REST APIs and CI/CD."
    icon: "fas fa-rocket"
  - title: "Data Analytics"
    excerpt: "Clear, compelling stories with data."
    icon: "fas fa-chart-bar"
  - title: "SQL & Databases"
    excerpt: "Modeling, cleaning, and performance-minded querying."
    icon: "fas fa-database"
  - title: "Visualization"
    excerpt: "Tableau/ggplot/Matplotlib for crisp, decision-ready visuals."
    icon: "fas fa-chart-line"

# --- Latest projects (3 big cards – you can add more)
latest:
  - title: "Telco Customer Churn"
    excerpt: "End-to-end modeling with SHAP explainability."
    image_path: 
    url: /projects/telco-churn/
    btn_label: "Read case study"
    btn_class: "btn--primary"
  - title: "Cyclistic Rider Behavior"
    excerpt: "R + Tableau: usage patterns that drive conversion."
    image_path: 
    url: /projects/cyclistic/
    btn_label: "Open project"
    btn_class: "btn--primary"
  - title: "Bellabeat Usage Analysis"
    excerpt: "Wellness insights from Fitbit data."
    image_path: 
    url: /projects/bellabeat/
    btn_label: "Open project"
    btn_class: "btn--primary"
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
