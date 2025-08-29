---
layout: single
title: "World Layoffs: SQL Data Cleaning"
excerpt: "Prepare a messy layoffs dataset for EDA and trend analysis."
classes: wide
category: sql
tags: [mysql, data-cleaning, sql]
thumbnail: /assets/images/layoffs-splash.png
permalink: /projects/world-layoffs/
weight: 10
---

> **Goal** — Prepare a real-world layoffs dataset for EDA and trend analysis.  
> **Stack** — MySQL.  
> **Output** — Clean table **`layoffs_staging2`** ready for analysis.

---

## Highlights
- **Duplicates**: `ROW_NUMBER()` over key fields → delete `row_num > 1`.  
- **Standardization**: trimmed `company`; unified `industry`; cleaned `country` strings.  
- **Nulls**: filled `industry` via self-join; removed rows with no signal.  
- **Types**: converted text dates to `DATE` and enforced schema.  

---

## Project overview
This project cleans and standardizes a global layoffs dataset so it can support reliable trend analysis. The work covers duplicate detection, text normalization, null handling, and type conversions—implemented in **MySQL** with a raw → staging → cleaned table pattern.

---

## Data pipeline

### 1) Raw import
Create a raw table (unchanged baseline) and load the CSV.

> Database: `world_layoffs`  
> Table: `layoffs` (raw)

*(Keep this table immutable for audit/compare.)*

### 2) Staging copies
Work in isolated copies to transform safely.

```sql
-- Stage 1: structure + data clone
CREATE TABLE layoffs_staging LIKE layoffs;
INSERT INTO layoffs_staging SELECT * FROM layoffs;

-- Stage 2: final cleaned table structure
CREATE TABLE `layoffs_staging2` (
  `company`                TEXT,
  `location`               TEXT,
  `industry`               TEXT,
  `total_laid_off`         INT DEFAULT NULL,
  `percentage_laid_off`    TEXT,
  `date`                   TEXT,
  `stage`                  TEXT,
  `country`                TEXT,
  `funds_raised_millions`  INT DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

INSERT INTO layoffs_staging2
SELECT * FROM layoffs_staging;
