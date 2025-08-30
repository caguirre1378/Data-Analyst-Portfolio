---
layout: single
title: "Operational Performance: Manufacturing KPI Analysis"
excerpt: "Excel-based KPI analysis for a lawn equipment manufacturer: on-time delivery, transmission unit cost, and retention."
classes: wide
category: analytics
tags: [excel, hypothesis-testing, proportions, anova, manufacturing, kpi, retention]
permalink: /projects/ops-performance/
weight: 15
thumbnail: /assets/images/ops-performance-splash.png
---

> **Goal** — Diagnose and improve manufacturing performance across three KPIs.  
> **Stack** — **Excel** (data cleaning, KPI views, tests), **Word** (8-page executive report).

---

## Overview
In **Business Analytics II (Fall 2021)**, I analyzed a hypothetical lawn-equipment manufacturer to pinpoint where operations were lagging and what to change first. The workbook is organized by KPI with clean inputs, calculations, and formatted visuals stakeholders can use immediately. The accompanying Word brief summarizes results and actions.

---

## KPIs & methods

### 1) On-Time Delivery (OTD)
**Question.** Did delivery performance materially improve by 2018 vs. 2014?  
**Method.** One-sample **proportion test** (H₀: \(p_{2018}\le p_{2014}\)) with monthly OTD trend and seasonality checks.  
**Finding.** **Statistically significant improvement** in 2018; visuals show steadier performance and fewer low-OTD months.

---

### 2) Transmission Unit Cost (process options)
**Question.** Is an alternative transmission process cheaper on average?  
**Method.** **One-way ANOVA** across candidate processes; post-hoc comparison when needed.  
**Finding.** **Process A** is **marginally** cheaper. Given switching frictions, recommend piloting A in one line while tightening waste on the current process.

---

### 3) Employee Retention (gender × locality)
**Question.** Where are we losing people and what cohorts are stickier?  
**Method.** Cohort pivots by **gender** and **local/non-local**; monthly retention curves and rate deltas.  
**Finding.** **Local** staff and **male** cohort show **slightly higher** retention. Recommend shift scheduling tweaks, local recruiting, and targeted onboarding for higher-risk cohorts.

---

## Workbook structure
- **Raw** — source tables with data validation and filters.  
- **Calc** — clean joins, derived fields, KPI math, and test inputs.  
- **Charts** — formatted visuals aligned to each KPI tab: **OTD**, **Transmission Cost**, **Retention**.  
- Consistent slicers, conditional formatting, and notes for assumptions.

---

## How to use
1. Open the **Excel workbook**; start on the **Summary** (or KPI) tab.  
2. Use slicers (year, process, cohort) to explore.  
3. Recalculate stats by adjusting test inputs (e.g., baseline year, α).  
4. Export figures for slides or paste into the **8-page Word report** template.  
5. For scenario checks, tweak process costs or staffing in **Calc** and watch the dashboards update.

---

## Deliverables
- **Clean Excel workbook** with three KPI tabs and publication-ready charts.  
- **8-page report**: executive summary, methods, results, and recommended next steps.

---

## Links
- **Files & report** — <https://github.com/caguirre1378/Data-Analyst-Portfolio>

---

*Updated: December 1, 2021*
