---

layout: single
title: "Cyclistic Rider Behavior"
excerpt: "12 months of Chicago bike-share data to explain casual vs member behavior and drive membership growth."
classes: wide
category: analytics
tags: \[r, tidyverse, ggplot2, dplyr, lubridate, tableau]
thumbnail: /assets/images/cyclist-splash.png
permalink: /projects/cyclistic/
weight: 20
----------

> **Goal** — Compare **casual** vs **member** rider behavior to identify usage patterns and drive membership growth.
> **Stack** — R (tidyverse, dplyr, ggplot2, lubridate, janitor), Tableau Public.
> **Data** — 12 months of Divvy/Cyclistic trip data (\~4.1M rides).

---

## At a glance

* Downloaded and consolidated 12 monthly CSVs into one large dataset.
* Cleaned and transformed records (removed invalid durations, fixed datetimes, dropped NAs).
* Engineered features: `ride_length` in minutes, `day_of_week`, `hour`, `month`, and `season`.
* Created visualizations showing usage volume, time-of-day trends, and ride duration by type.
* Published interactive dashboards to Tableau for stakeholder use.

---

## Data & preparation

* Standardized all monthly datasets using `janitor::clean_names()` for consistency.
* Parsed `started_at` and `ended_at` with `lubridate`, calculated ride durations.
* Applied filters to exclude rides <1 minute, records missing `member_casual` or station data.
* Added derived features to support trend and behavior segmentation.

**Core import & clean (R):**

```r
library(tidyverse)
library(lubridate)
library(janitor)

# Import all monthly CSVs
datasets <- list.files("data_raw", pattern = "\\.csv$", full.names = TRUE)

# Clean and stack into one dataframe
all_trips <- datasets %>%
  map_df(read_csv) %>%
  clean_names() %>%
  mutate(
    started_at = ymd_hms(started_at),
    ended_at = ymd_hms(ended_at),
    ride_length = as.numeric(difftime(ended_at, started_at, units = "mins")),
    day_of_week = wday(started_at, label = TRUE),
    hour = hour(started_at),
    month = month(started_at, label = TRUE)
  ) %>%
  filter(ride_length > 1, !is.na(member_casual)) %>%
  drop_na()
```

---

## Summary statistics

Using `dplyr`, I computed aggregate metrics for both rider groups:

```r
summary_stats <- all_trips %>%
  group_by(member_casual) %>%
  summarise(
    avg_ride_length = mean(ride_length),
    median_ride_length = median(ride_length),
    max_ride_length = max(ride_length),
    min_ride_length = min(ride_length),
    ride_count = n()
  )
```

* **Casual riders** take longer rides (\~23.6 mins on average).
* **Members** ride more frequently, but for shorter durations (\~12.6 mins).
* Casual rides peak on **weekends**, members ride more during **weekdays**.

---

## Visualizations & insights

### 🚲 Ride Volume by Day of Week

* Casual users spike Saturday–Sunday.
* Members ride most during weekdays (commuting behavior).

### ⏱ Average Ride Duration by Day

* Casual riders take longer weekend rides.
* Members ride shorter distances but consistently throughout the week.

### 🕒 Hourly Usage Heatmap

* Casual: Afternoon/evening use.
* Members: Clear morning and evening rush hour trends.

All visuals were developed using `ggplot2` in R and mirrored in Tableau for stakeholder presentation.

---

## Tableau Dashboard

[🔗 View Dashboard](https://public.tableau.com/app/profile/your_profile_name/viz/cyclistic_dashboard)

**Filters included:**

* Rider type (casual vs member)
* Day of week
* Hour of day
* Ride duration range

**KPIs displayed:**

* Total rides: 4.1M+
* Avg. ride duration by rider type
* Peak usage windows by day/hour
* Seasonal and monthly ride trends

---

## Strategic Recommendations

* Offer **weekend ride promos** to casual riders.
* Promote membership benefits after 3–5 casual rides.
* Use app push notifications to recommend plans based on user patterns.

---

## Deliverables

* Cleaned and annotated R scripts for data import, transformation, and plotting.
* Tableau dashboards with rider trends and KPIs.
* GitHub repository with README and report.

---

## Links

* [GitHub Repository](https://github.com/caguirre1378/Data-Analyst-Portfolio)
* [Interactive Tableau Dashboard](https://public.tableau.com/app/profile/your_profile_name/viz/cyclistic_dashboard)
