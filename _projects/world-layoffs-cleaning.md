---
layout: single
title: "World Layoffs: SQL Data Cleaning"
excerpt: "SQL-powered data cleaning pipeline to prepare a public layoffs dataset for analysis and business insights."
classes: wide
category: analytics
tags: [mysql, sql, data-cleaning, wrangling, eda, business-insights]
thumbnail: /assets/images/layoffs-splash.png
permalink: /projects/world-layoffs-cleaning/
weight: 40
---

> **Goal** — Clean and standardize a real-world layoffs dataset to enable reliable SQL-based trend analysis and exploratory data analysis.  
> **Stack** — MySQL (Workbench), GitHub.  
> **Data** — Public global layoffs dataset (Layoffs.fyi, CSV format).  
> **Output** — Cleaned and structured SQL table `layoffs_staging2`, optimized for business intelligence and reporting.

---

## Overview

This project focused on preparing a raw layoffs dataset for deeper business analysis using SQL. It involved building a structured ETL (Extract, Transform, Load) pipeline across three stages:

1. Raw Import (unchanged data source)  
2. Staging Copy (intermediate cleaning and transformation)  
3. Final Cleaned Table (analysis-ready)

The cleaning process addressed duplicates, inconsistent text formatting, missing values, and incorrect data types. The resulting dataset was optimized for downstream analytics and dashboard use.

---

## Key Highlights

- Duplicates were removed using `ROW_NUMBER()` partitioned over company, location, industry, and date fields.  
- Text fields were standardized by trimming whitespace and consolidating variations in industries and country formatting.  
- Null values in key fields were resolved using self-joins or dropped when non-informative.  
- Text-based date fields were converted into SQL `DATE` format for accurate filtering and time-series analysis.  
- The final schema was aligned for efficiency, consistency, and compatibility with business reporting tools.

---

## Database Structure

**Database:** `world_layoffs`

| Table              | Purpose                                |
|--------------------|----------------------------------------|
| `layoffs`          | Raw data directly imported from CSV    |
| `layoffs_staging`  | Intermediate working copy              |
| `layoffs_staging2` | Final cleaned table used for analysis  |

---

## 1. Raw Data Import

The initial table `layoffs` was created from a CSV export of the original dataset. This table was preserved as an unmodified baseline.

```sql
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
```

---

## 2. Staging & Cleaning Pipeline

### Step 1: Create Staging Tables

Two copies of the raw data were created to safely perform transformations without affecting the original.

```sql
-- Clone structure and data for transformation
CREATE TABLE layoffs_staging LIKE layoffs;
INSERT INTO layoffs_staging SELECT * FROM layoffs;

-- Define the final table structure
CREATE TABLE layoffs_staging2 (
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
INSERT INTO layoffs_staging2 SELECT * FROM layoffs_staging;
```

---

### Step 2: Remove Duplicate Records

Duplicate rows were identified using `ROW_NUMBER()` and removed from the cleaned table.

```sql
-- Identify duplicates
WITH duplicate_cte AS (
  SELECT *,
    ROW_NUMBER() OVER (
      PARTITION BY company, location, industry, total_laid_off, percentage_laid_off, date, stage, country, funds_raised_millions
    ) AS row_num
  FROM layoffs_staging
)
DELETE FROM layoffs_staging2
WHERE row_num > 1;
```

---

### Step 3: Standardize Text Fields

Inconsistent formatting in company names, industries, and countries was corrected.

```sql
-- Trim whitespace from company names
UPDATE layoffs_staging2 SET company = TRIM(company);

-- Consolidate industry values
UPDATE layoffs_staging2
SET industry = 'Crypto'
WHERE industry LIKE 'Crypto%';

-- Remove trailing punctuation from countries
UPDATE layoffs_staging2
SET country = TRIM(TRAILING '.' FROM country)
WHERE country LIKE 'United States%';
```

---

### Step 4: Handle Missing Values

Wherever possible, missing `industry` values were filled using self-joins. Rows without useful signals were removed.

```sql
-- Fill missing industry values using other rows
UPDATE layoffs_staging2 t1
JOIN layoffs_staging2 t2
  ON t1.company = t2.company AND t1.location = t2.location
SET t1.industry = t2.industry
WHERE t1.industry IS NULL AND t2.industry IS NOT NULL;

-- Remove rows missing both layoff metrics
DELETE FROM layoffs_staging2
WHERE total_laid_off IS NULL AND percentage_laid_off IS NULL;
```

---

### Step 5: Convert Dates to SQL DATE Format

Text-formatted dates were converted for compatibility with time-based analysis.

```sql
-- Convert string to DATE format
UPDATE layoffs_staging2
SET date = STR_TO_DATE(date, '%m/%d/%Y');

-- Update column type
ALTER TABLE layoffs_staging2
MODIFY COLUMN date DATE;
```

---

### Step 6: Final Table Verification

After transformation, helper columns were dropped and the final cleaned dataset was reviewed.

```sql
-- Drop temporary columns if any were used
ALTER TABLE layoffs_staging2 DROP COLUMN row_num;

-- Preview the cleaned dataset
SELECT * FROM layoffs_staging2;
```

---

## Use Cases for Analysis

The cleaned dataset supports a range of business intelligence use cases, including:

- Layoffs by country, industry, or company  
- Time-series visualizations of layoff spikes or patterns  
- Correlations between funding and layoffs  
- Stage-based breakdowns (early, growth, IPO, etc.)

---

## System Setup & Execution

**Software:**  
- MySQL Workbench or equivalent SQL IDE  
- GitHub for version control and documentation

**Workflow:**  
1. Import raw CSV to create `layoffs` table  
2. Duplicate to `layoffs_staging` and `layoffs_staging2`  
3. Run cleaning scripts step-by-step  
4. Analyze data from `layoffs_staging2`

---

## Future Enhancements

- Automate the cleaning pipeline using stored procedures or Python scripts  
- Connect the final cleaned table to Tableau or Power BI for interactive dashboards  
- Integrate API-based data ingestion for real-time updates  
- Add version tracking for schema changes and refresh logs

---

**Updated:** August 31, 2025  
**GitHub Repo:** [Data-Analyst-Portfolio](https://github.com/caguirre1378/Data-Analyst-Portfolio)
