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

> **Goal** — Identify performance gaps and recommend solutions across three core KPIs.  
> **Stack** — Microsoft Excel (analysis, dashboards), Word (8-page report).  
> **Course** — Business Analytics II (Fall 2021), Senior Capstone

---

## Overview
This project analyzed the operations of a hypothetical lawn equipment manufacturer to uncover bottlenecks and propose data-driven improvements. Using historical data from 2014–2018, I assessed on-time delivery, transmission unit costs, and employee retention — all critical to sustainable performance.

The Excel workbook includes interactive KPI dashboards, embedded statistical analysis, and clean formatting for stakeholders. An 8-page Word report summarizes insights, methodology, and next steps for operational leaders.

---

## KPI Deep Dives

### 1) On-Time Delivery (OTD)
**Objective:** Determine if delivery performance significantly improved by 2018.  
**Method:** One-sample **proportion test** comparing 2018 vs. 2014  
**Insights:**
- Statistically significant improvement in 2018
- Monthly trends showed steadier performance and fewer seasonal dips  
**Recommendation:** Continue enforcing process improvements that led to 2018 gains. Use visual dashboards to monitor consistency.

---

### 2) Transmission Unit Cost (UTC)
**Objective:** Compare average unit costs across three alternative transmission processes.  
**Method:** **One-way ANOVA** with post-hoc checks  
**Insights:**
- Process A was marginally cheaper, though not by a wide margin
- Switching costs may outweigh minor savings  
**Recommendation:** Pilot **Process A** on a single line while reducing waste in the current setup to validate its viability.

---

### 3) Employee Retention
**Objective:** Identify trends in retention by **gender** and **local vs. non-local** status  
**Method:** Cohort pivot analysis with retention curves  
**Insights:**
- Local and male employees had slightly higher retention
- Retention gaps were small but consistent  
**Recommendation:** Improve onboarding, shift flexibility, and targeted HR engagement for non-local or high-risk cohorts.

---

## Workbook Design

- **Raw Data:** Filterable source tables with validation
- **Calc Tabs:** KPI-specific calculations, test inputs, and logic
- **Charts:** Clean visuals per KPI (OTD, UTC, Retention)
- Features include slicers, conditional formatting, and export-ready figures

Each tab supports quick scenario testing and updates dynamically when inputs are adjusted.

---

## How to Use

1. Open the Excel workbook and start at the **Summary** tab  
2. Use slicers to filter year, process type, or cohort group  
3. Adjust statistical assumptions (e.g., alpha levels, years) to test sensitivity  
4. Export visuals for presentation or reports  
5. Read the 8-page Word report for structured findings and business recommendations

---

## Deliverables

- 📊 **Excel dashboard** with KPI-specific tabs and real-time visualizations  
- 📄 **8-page Word report** including:
  - Executive summary  
  - KPI deep dives  
  - Visual evidence  
  - Clear, actionable next steps

---

## Summary of Results

| KPI                | Method               | Key Takeaway                                                   |
|--------------------|----------------------|----------------------------------------------------------------|
| On-Time Delivery   | Proportion Test       | Significant improvement by 2018; performance stabilized        |
| Transmission Cost  | ANOVA                 | Process A slightly cheaper; recommend pilot before rollout     |
| Employee Retention | Cohort Analysis       | Local/male cohorts retain better; improve onboarding for others|

---

## Future Enhancements

- **Predictive Modeling** — Add churn or cost prediction using regression or classification  
- **Automated Tracking** — Integrate Power Query for real-time KPI refreshes  
- **ERP Integration** — Deploy within a broader ERP dashboard for end-to-end visibility

---

## GitHub
📂 [View files, dashboards, and report](https://github.com/caguirre1378/Data-Analyst-Portfolio)

---

*Updated: August 30, 2025*
