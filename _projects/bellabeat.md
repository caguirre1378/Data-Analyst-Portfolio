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
> **Stack** — R (tidyverse, dplyr, lubridate, janitor, ggplot2), Tableau Public.
> **Data** — 30-day Fitbit dataset (≈30 users, anonymized public data).

---

## At a glance

* Ingested and merged **daily activity**, **sleep**, and **calorie tracking** data.
* Cleaned and filtered records, excluding days with missing data or zero activity.
* Engineered features such as **total active minutes** and **weekday labels**.
* Analyzed activity patterns by weekday and user behavior segments.
* Built visual dashboards in Tableau to support wellness engagement insights.

---

## Data & preparation

* Raw datasets included:
  `dailyActivity_merged.csv`, `sleepDay_merged.csv`, and `dailyCalories_merged.csv`.
* Each file was imported into R and cleaned using `janitor::clean_names()` to standardize column names.
* Dates were parsed consistently across all datasets using `lubridate::as_date()`.
* Merged the datasets by **user ID** and **date**, producing a clean master dataset.
* Removed records with missing data and zero steps to maintain quality.

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
```

---

## Analysis & insights

* Added calculated fields such as **total\_active\_minutes** by summing lightly, fairly, and very active minutes.
* Derived **day\_of\_week** from the date field to analyze patterns by weekday.
* Grouped data to explore averages by weekday and user-level activity trends.
* Created Tableau dashboards to explore how activity, sleep, and calories interact.

**Top behavioral insights:**

* **Weekday vs weekend split**: Most users were significantly more active Monday through Friday, with notable drops on weekends.
* **Sleep & activity correlation**: Users with consistent sleep patterns tended to maintain higher levels of activity and calorie burn.
* **Active minute patterns**: Days with high total active minutes were often aligned with peak calorie burn.

---

## Visualizations

* Used **ggplot2** to build exploratory bar plots, histograms, and scatter plots for internal review.
* Designed a **Tableau dashboard** to visualize:

  * **Average steps by weekday**
  * **Calories burned vs. total active minutes**
  * **Sleep duration vs. daily steps**

---

## Recommendations

* **Encourage weekend activity** through in-app challenges or reward prompts.
* **Nudge users with low sleep consistency** to adopt wind-down routines — sleep quality links to engagement.
* Create **habit-forming nudges** for users who show sporadic calorie/activity logs (e.g., auto-reminders).
* Use clustering logic in future phases to segment users by wellness engagement style (e.g., active sleepers vs. calorie burners).

---

## Reproduce

1. Download the Fitbit public dataset from Kaggle.
2. Load and clean files in R using `tidyverse`, `lubridate`, and `janitor`.
3. Merge datasets by ID and date.
4. Explore with `ggplot2` and publish in Tableau.

**Dashboard (optional link):** [Bellabeat Engagement Dashboard](#)

---

## Next

* Segment by **demographic if available** (e.g., age group, gender).
* Test correlation of steps/sleep/calories with clustering or regression.
* Recommend **personalized goal nudges** based on user segment.
