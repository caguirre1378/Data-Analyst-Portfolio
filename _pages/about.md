---
permalink: /about/
title: "About"
layout: single
classes: wide
---

<style>
/* simple layout helpers just for this page */
.twocol { display:grid; grid-template-columns: 1fr 1fr; gap: 1.25rem; }
@media (max-width: 820px){ .twocol { grid-template-columns: 1fr; } }
.pill { display:inline-block; padding:.25rem .6rem; border-radius:999px; background:#f2f4f7; margin:.15rem .25rem .15rem 0; font-size:.9rem; }
.timeline { list-style:none; padding-left:0; }
.timeline .tl-date { font-size:.8rem; color:#666; margin-bottom:.25rem; }
.timeline .tl-card { background:#fff; border:1px solid #e6e8eb; border-radius:.5rem; padding:.6rem .8rem; }
</style>

I work on data problems close to operations. The goal is simple: shorten the loop from “question” to “decision.” I ship small, reliable tools—spreadsheets, SQL models, and lightweight scripts—that people can use today.

**Current — Facility Support Manager, GBA Associates (DHHQ).**  
Own the facility-support workflow end to end (intake → triage → vendor dispatch → close out) and turn ticket data into decisions. Built:
- An Excel/VBA multi-criteria search across large project and work order lists (lookup time dropped from minutes to seconds).
- Power Query pipelines that consolidate multi-year exports and vendor files into one clean model.
- Compact dashboards for SLA and volume trends, aging, and recurring issues.

**Previously — Pro Sales, Lowe’s.**  
Managed contractor accounts, kept inventory and procurement moving, and shipped the simplest solution people would actually use.

**Education**  
- **B.S., Management Information Systems — George Mason University (2021–2023)**  
- **A.S., Business Administration — Northern Virginia Community College (2019–2021)**

## How I work
- **Start with a Decision Brief.** What decision, by whom, by when, with what success metric and constraints.
- **Baseline first, then improve.** Establish the current number, define “good enough,” and iterate toward it.
- **Data hygiene before charts.** Pin down source of truth, keys, grains, and definitions. Keep a short data dictionary.
- **Make it refreshable.** One click or one query to refresh (Power Query, SQL views, or parameterized extracts).
- **Short feedback loops.** Ship a rough cut early, demo, collect edge cases, and fold them back in weekly.
- **Explainability over cleverness.** Prefer simple, testable logic with checks and back tests.
- **Clean hand off.** A README, owner, refresh steps, and a rollback plan.

## What I can help with
- **KPIs and dashboards.** Translate goals into measurable metrics and build lightweight dashboards in **Excel / Power Query / SQL / Tableau**.
- **Data cleaning and modeling.** De-dupe, standardize, normalize dates, and build tidy **staging tables** or star-schema views.
- **Operational analytics.** SLA tracking, cohort and retention, churn risk, simple forecasting.
- **Automation of ad hoc work.** Refreshable pipelines; Excel + VBA utilities for bulk lookups and exports.
- **Decision support.** One-page memos with context, options, trade-offs, recommendation, and next steps.
- **Enablement.** Short docs and templates so the team can maintain and extend the work.

## Selected work
- **[Telco churn]({{ site.baseurl }}/projects/telco-churn/):** model, drivers, and retention targets.  
- **[Cyclistic behavior]({{ site.baseurl }}/projects/cyclist/):** weekday vs. weekend use; membership levers.  
- **[Layoffs data clean]({{ site.baseurl }}/projects/world-layoffs/):** dedupe, standardize, type, and stage.

## Tools I reach for
<div>
  <span class="pill">SQL (MySQL/SSMS)</span>
  <span class="pill">Excel & VBA</span>
  <span class="pill">Power Query</span>
  <span class="pill">Tableau</span>
  <span class="pill">Power BI (basic)</span>
  <span class="pill">Python (pandas)</span>
  <span class="pill">R (tidyverse)</span>
  <span class="pill">Jupyter</span>
  <span class="pill">Git/GitHub</span>
  <span class="pill">LINGO</span>
  <span class="pill">NumPy</span>
  <span class="pill">scikit-learn</span>
  <span class="pill">Matplotlib</span>
  <span class="pill">Seaborn</span>
  <span class="pill">ggplot2</span>
</div>

## Milestones
<ul class="timeline">
  <li>
    <div class="tl-date">2025</div>
    <div class="tl-card">
      <strong>Google Data Analytics Professional Certificate — May 2025</strong><br>
      Coursework across cleaning, analysis, visualization, and practical stakeholder communication.
    </div>
  </li>
  <li>
    <div class="tl-date">2025</div>
    <div class="tl-card">
      <strong>Facility Support Manager — GBA Associates @ DHHQ (Mar 2025–present)</strong><br>
      Workflow ownership, vendor coordination, and ops reporting. Shipped Excel/VBA search, Power Query consolidation, and performance dashboards.
    </div>
  </li>
  <li>
    <div class="tl-date">2022–2025</div>
    <div class="tl-card">
      <strong>Pro Sales Associate — Lowe’s</strong><br>
      Managed contractor accounts, improved procurement flows, and delivered fast solutions.
    </div>
  </li>
  <li>
    <div class="tl-date">2021–2023</div>
    <div class="tl-card">
      <strong>B.S., Management Information Systems — George Mason University</strong>
    </div>
  </li>
  <li>
    <div class="tl-date">2019–2021</div>
    <div class="tl-card">
      <strong>A.S., Business Administration — Northern Virginia Community College</strong>
    </div>
  </li>
</ul>

## Now / Next
<div class="twocol">
  <div>
    <h3>Now</h3>
    <ul>
      <li><strong>Evaluation checklists</strong> — leakage, drift, fairness, and data-quality gates in PRs; quick sampling checks before release.</li>
      <li><strong>Decision-first write ups</strong> — one pager per analysis: decision → baseline → cost of error → recommendation → risks and next steps; link to a reproducible notebook.</li>
      <li><strong>Decision-quality metrics</strong> — calibration, lift vs. current policy, expected value and cost curves, time to insight.</li>
      <li><strong>From ad hoc to repeatable</strong> — turn scripts into refreshable pipelines; document data owners, keys, and SLAs.</li>
    </ul>
  </div>
  <div>
    <h3>Next</h3>
    <ul>
      <li><strong>Lightweight monitoring</strong> — freshness, volume, and schema checks with simple alerts and a short runbook.</li>
      <li><strong>Human in the loop</strong> — review queue for borderline predictions; thresholds and escalation rules; feedback loop for retraining.</li>
      <li><strong>Postmortems & playbooks</strong> — tight templates, common failure modes, rollback and verify checklist.</li>
      <li><strong>Data contracts & validation</strong> — schema constraints, allowed ranges, de-dupe keys, and backfill policy.</li>
    </ul>
  </div>
</div>

## Say hello
<p>
  <a class="btn btn--primary" href="{{ site.baseurl }}/resume/">Resume</a>
  <a class="btn" href="{{ site.baseurl }}/projects/">Portfolio</a>
  <a class="btn" href="mailto:christianaguirrepp@gmail.com">Email</a>
</p>
