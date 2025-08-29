---
permalink: /about/
title: "About"
layout: single
classes: wide
---

<!-- HERO / INTRO -->
<section class="section-white">
  <h2>Hi — I'm Christian</h2>
  <p class="section-sub">
    I analyze data to drive decisions. I like clear stories, clean code, and shipping useful tools.
  </p>
  <p style="text-align:center; margin-top: 12px;">
    <a class="btn btn--primary" href="/projects/">View Projects</a>
    <a class="btn" href="/resume/">Resume</a>
    <a class="btn btn--inverse" href="mailto:your.email@example.com">Email</a>
  </p>
</section>

<!-- WHAT I FOCUS ON (same 2x3 cards as home) -->
<section class="section-gray">
  <h2>What I’m Focused On</h2>
  <p class="section-sub">Some of the areas I spend most of my time learning and applying.</p>

  <div class="topics">
    <article class="topic">
      <div class="topic__icon"><i class="fas fa-cloud"></i></div>
      <h3>Cloud Compute</h3>
      <p>Storage, model training, and deployment at scale.</p>
    </article>
    <article class="topic">
      <div class="topic__icon"><i class="fas fa-language"></i></div>
      <h3>NLP</h3>
      <p>Making sense of human text and conversations.</p>
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
      <p>Decision-ready visuals and clear storytelling.</p>
    </article>
  </div>
</section>

<!-- HOW I WORK -->
<section class="section-white">
  <h2>How I Work</h2>
  <ol>
    <li><strong>Frame the question:</strong> align with stakeholders on the decision we’re trying to make.</li>
    <li><strong>Collect & clean:</strong> build reliable datasets; document assumptions.</li>
    <li><strong>Explore & hypothesize:</strong> EDA, segmentation, feature ideas.</li>
    <li><strong>Model:</strong> baseline → iterate → stress test (data leakage, drift, fairness).</li>
    <li><strong>Ship:</strong> REST API / batch jobs, CI/CD, and observability.</li>
    <li><strong>Tell the story:</strong> compact visuals + direct recommendations.</li>
  </ol>
</section>

<!-- TOOLS (simple pill list) -->
<section class="section-gray">
  <h2>Tools I Reach For</h2>
  <p class="section-sub">The stack depends on the problem, but these are my go-tos.</p>

  <div style="max-width:1000px;margin:0 auto;">
    <p><strong>Data / SQL:</strong>
      <span class="pill">SQL</span>
      <span class="pill">BigQuery</span>
      <span class="pill">Postgres</span>
      <span class="pill">Hive</span>
      <span class="pill">Airflow</span>
    </p>
    <p><strong>Python / ML:</strong>
      <span class="pill">Pandas</span>
      <span class="pill">NumPy</span>
      <span class="pill">scikit-learn</span>
      <span class="pill">XGBoost</span>
      <span class="pill">NLTK / spaCy</span>
    </p>
    <p><strong>Cloud & DevOps:</strong>
      <span class="pill">GCP</span>
      <span class="pill">AWS</span>
      <span class="pill">Docker</span>
      <span class="pill">FastAPI</span>
      <span class="pill">Terraform (basics)</span>
    </p>
    <p><strong>Viz:</strong>
      <span class="pill">Matplotlib</span>
      <span class="pill">Plotly</span>
      <span class="pill">Looker Studio</span>
    </p>
  </div>
</section>

<!-- PROOF / HIGHLIGHTS -->
<section class="section-white">
  <h2>Selected Highlights</h2>
  <ul>
    <li>Built an end-to-end customer churn model with SHAP explanations to guide retention actions.</li>
    <li>Analyzed rider behavior to surface seasonality and cohort trends that informed pricing tests.</li>
    <li>Shipped NLP pipelines (cleaning, topic extraction, sentiment) to turn messy text into signals.</li>
  </ul>
</section>

<!-- PROJECT TEASERS (auto pulls your 3 most recent projects) -->
<section class="section-gray">
  <h2>Recent Work</h2>
  <p class="section-sub">A few projects I’ve been working on lately.</p>

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

  <p style="text-align:center; margin-top: 16px;">
    <a class="btn" href="/projects/">See all projects</a>
  </p>
</section>

<!-- CTA -->
<section class="section-white">
  <h2>Let’s Connect</h2>
  <p class="section-sub">Open to data/ML roles and interesting collaborations.</p>
  <p style="text-align:center;">
    <a class="btn btn--primary" href="/resume/">Resume</a>
    <a class="btn" href="/projects/">Portfolio</a>
    <a class="btn btn--inverse" href="mailto:your.email@example.com">Email</a>
  </p>
</section>
