---
layout: single
title: "World Layoffs: SQL Data Cleaning"
excerpt: "Prepare a real-world layoffs dataset for SQL EDA and trend analysis."
classes: wide
category: analytics
tags: [mysql, sql, cleaning, data-wrangling, eda]
thumbnail: /assets/images/layoffs-splash.png
permalink: /projects/world-layoffs-cleaning/
weight: 40
---

> **Goal** — Prepare a real-world layoffs dataset for SQL EDA and trend analysis.  
> **Stack** — MySQL (queries run via Workbench).  
> **Output** — Cleaned table `layoffs_staging2` ready for downstream analysis.

---

## At a glance
- **Removed duplicates** using `ROW_NUMBER()` partitioned over key fields.  
- **Standardized text fields** like `company`, `industry`, and `country`.  
- **Addressed nulls** via self-joins and selective row deletions.  
- **Converted types** for SQL compatibility, including parsing dates.  
- Maintained a clean **raw → staging → final** pipeline structure.

---

## Project structure
- Raw CSV file imported into `layoffs` (raw baseline).  
- Duplicated into `layoffs_staging` for cleaning.  
- Final output: `layoffs_staging2` — fully cleaned and formatted.

---

## 1. Raw import
Imported the layoffs CSV into MySQL and created a raw table for reference.

**Database:** `world_layoffs`  
**Table:** `layoffs` (baseline copy)

```sql
-- Raw import: load CSV into this table
CREATE TABLE layoffs (
  company TEXT,
  location TEXT,
  industry TEXT,
  total_laid_off INT,
  percentage_laid_off TEXT,
  date TEXT,
  stage TEXT,
  country TEXT,
  funds_raised_millions INT
);
