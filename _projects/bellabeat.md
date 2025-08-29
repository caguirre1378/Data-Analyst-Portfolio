---
layout: single
title: "Bellabeat Smart Device Usage Analysis"
excerpt: "Fitbit public data used to explain behavior and inform Bellabeat’s marketing & product engagement."
classes: wide
category: analytics
tags: [r, tidyverse, dplyr, lubridate, ggplot2, janitor, tableau]
thumbnail: /assets/images/bellabeat-splash.png
permalink: /projects/bellabeat/
weight: 30
---

> **Goal** — Uncover usage patterns (steps, calories, sleep) and translate them into actions that grow engagement and acquisition.  
> **Stack** — R (tidyverse, dplyr, lubridate, janitor, ggplot2), Tableau.  
> **Data** — 30-day Fitbit dataset (~30 users, public).

---

## At a glance
- Imported & merged **daily activity, sleep, and calories** CSVs; standardized columns.  
- Cleaned records (missing/zero activity), fixed dates, and built features:  
  **active_minutes_total**, **day_of_week**.  
- Summarized usage by weekday and produced charts in **ggplot2/Tableau**.

---

## Data & preparation
- Datasets: `dailyActivity_merged.csv`, `sleepDay_merged.csv`, `dailyCalories_merged.csv`.  
- Cleaned with `janitor::clean_names()`, parsed dates, inner-joined on **id + date**.  
- Filters removed missing values and zero-activity days.  
- Engineered features for analysis & dashboards.

**Core import & merge (R):**
```r
library(tidyverse)
library(janitor)
library(lubridate)

daily_activity <- read_csv("dailyActivity_merged.csv") %>%
  clean_names() %>%
  mutate(activity_date = as.Date(activity_date, "%m/%d/%Y"))

daily_sleep <- read_csv("sleepDay_merged.csv") %>%
  clean_names() %>%
  mutate(sleep_day = as.Date(sleep_day, "%m/%d/%Y"))

daily_calories <- read_csv("dailyCalories_merged.csv") %>%
  clean_names() %>%
  mutate(activity_day = as.Date(activity_day, "%m/%d/%Y"))

merged_data <- daily_activity %>%
  inner_join(daily_sleep,   by = c("id", "activity_date" = "sleep_day")) %>%
  inner_join(daily_calories,by = c("id", "activity_date" = "activity_day")) %>%
  rename(date = activity_date)
