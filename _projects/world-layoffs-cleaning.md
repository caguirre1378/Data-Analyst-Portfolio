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


> **Goal** — Prepare a real-world layoffs dataset for exploratory data analysis and trend insights.
> **Stack** — MySQL (Workbench), GitHub.
> **Output** — Cleaned table `layoffs_staging2` suitable for business reporting and analytics.

---

## At a glance

* **Removed duplicates** using `ROW_NUMBER()` over key fields and filtered to retain unique records.
* **Standardized text** across company, industry, and country columns for clean joins and visuals.
* **Filled or dropped nulls** logically (e.g., self-join on company/location to fill missing industry).
* **Converted types** such as text dates into actual `DATE` format for analysis.
* Final table `layoffs_staging2` is optimized for queries, filtering, and visualization.

---

## Data pipeline

### 1. Raw import

* Created an untouched base table `layoffs` from the original Excel-exported CSV.
* Purpose: preserve a reference for auditing and comparison.

```sql
-- Initial raw import table
CREATE TABLE layoffs (...);
-- Import CSV to this table
```

**Database**: `world_layoffs`
**Table**: `layoffs` (raw)

---

### 2. Staging tables

Performed all transformations in duplicates:

```sql
-- Stage 1: Clone raw table for work
CREATE TABLE layoffs_staging LIKE layoffs;
INSERT INTO layoffs_staging SELECT * FROM layoffs;

-- Stage 2: Structure for final cleaned table
CREATE TABLE layoffs_staging2 (
  company TEXT,
  location TEXT,
  industry TEXT,
  total_laid_off INT DEFAULT NULL,
  percentage_laid_off TEXT,
  date TEXT,
  stage TEXT,
  country TEXT,
  funds_raised_millions INT DEFAULT NULL
);

INSERT INTO layoffs_staging2
SELECT * FROM layoffs_staging;
```

---

## Cleaning process

### Step 1: Remove duplicates

Used `ROW_NUMBER()` partitioned by company, location, date, etc.

```sql
-- Identify duplicates
WITH duplicate_cte AS (
  SELECT *,
         ROW_NUMBER() OVER (PARTITION BY company, location, industry, total_laid_off,
                                             percentage_laid_off, date, stage, country, funds_raised_millions) AS row_num
  FROM layoffs_staging
)
SELECT * FROM duplicate_cte WHERE row_num > 1;

-- Remove duplicates
DELETE FROM layoffs_staging2
WHERE row_num > 1;
```

---

### Step 2: Standardize formatting

Trimmed fields and merged inconsistent values.

```sql
-- Trim whitespace from company
UPDATE layoffs_staging2 SET company = TRIM(company);

-- Merge industry variations
UPDATE layoffs_staging2 SET industry = 'Crypto' WHERE industry LIKE 'Crypto%';

-- Fix country field
UPDATE layoffs_staging2 SET country = TRIM(TRAILING '.' FROM country);
```

---

### Step 3: Handle nulls

Filled or removed based on signal presence.

```sql
-- Fill missing industry using same company/location
UPDATE layoffs_staging2 t1
JOIN layoffs_staging2 t2
  ON t1.company = t2.company AND t1.location = t2.location
SET t1.industry = t2.industry
WHERE t1.industry IS NULL AND t2.industry IS NOT NULL;

-- Remove rows where no layoff data exists
DELETE FROM layoffs_staging2
WHERE total_laid_off IS NULL AND percentage_laid_off IS NULL;
```

---

### Step 4: Convert types

Ensured date is stored as a `DATE`, not text.

```sql
-- Convert date text to DATE
UPDATE layoffs_staging2
SET date = STR_TO_DATE(date, '%m/%d/%Y');

-- Update column type
ALTER TABLE layoffs_staging2
MODIFY COLUMN date DATE;
```

---

### Step 5: Final cleanup

Removed helper columns and verified schema.

```sql
-- Remove row_num column
ALTER TABLE layoffs_staging2 DROP COLUMN row_num;

-- Final verification
SELECT * FROM layoffs_staging2;
```

---

## Usage instructions

* Import raw CSV into MySQL under `world_layoffs.layoffs`.
* Run the scripts to create staging layers and execute transformations.
* Use `layoffs_staging2` for dashboards or further analysis in tools like Tableau/Power BI.

### Queries you can run

* Total layoffs by industry or country
* Monthly trend of layoffs by stage (e.g., Series A vs Series B)
* Correlation between funding size and layoff severity

---

## Deliverables

* Cleaned `layoffs_staging2` table (in MySQL).
* GitHub repo with SQL scripts and table previews.
* Future-ready: easy integration with Tableau/Power BI.

---

## Future work

* Add support for **live data ingestion**.
* **Automate** cleaning scripts for ongoing updates.
* Create Tableau dashboard from this table (coming soon).

---

*Updated: August 31, 2025*
