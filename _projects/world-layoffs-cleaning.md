---
layout: single
title: "World Layoffs: SQL Data Cleaning"
date: 2025-01-15
category: "SQL & Databases"
tags: [mysql, sql, cleaning, staging, analytics-ready]
thumbnail: /assets/images/layoffs-splash.png
weight: 40
description: "De-duping, standardization, null handling, and type fixes for global layoffs data."
---

**Goal.** Prepare a messy layoffs dataset for EDA and trend analysis.

**Stack.** MySQL.

**Highlights**
- **Duplicates:** ROW_NUMBER() over key fields → remove row_num > 1.
- **Standardization:** trimmed company; unified industry labels; cleaned country strings.
- **Nulls:** filled industry via self-join; removed rows with no signal.
- **Types:** converted dates to `DATE` and enforced schema.

**Output.** Clean table `layoffs_staging2` for analysis.

**Links**
- SQL scripts: <https://github.com/caguirre1378/Data-Analyst-Portfolio>
