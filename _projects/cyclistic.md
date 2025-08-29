---
layout: single
title: "Cyclistic Rider Behavior"
excerpt: "12 months of bike-share data in Chicago to explain casual vs member behavior and drive membership growth."
classes: wide
category: analytics
tags: [r, tidyverse, ggplot2, dplyr, lubridate, tableau]
thumbnail: /assets/images/cyclist-splash.png
permalink: /projects/cyclistic/
weight: 20
---

> **Goal** — Compare **casual** vs **member** behavior and surface levers that increase membership conversion.  
> **Stack** — R (tidyverse, dplyr, ggplot2, lubridate, janitor), Tableau Public.  
> **Data** — 12 months of Divvy/Cyclistic trips (~4.1M rides).

---

## At a glance
- Ingested 12 monthly CSVs, standardized columns, and combined to a single dataset.  
- Cleaned records (removed zero/negative durations, fixed timestamps, dropped missing rider type/stations).  
- Built tidy features: **ride_length** (mins), **day_of_week**, **hour**, **month/season**.  
- Summarized usage by rider type, weekday, hour, and season; produced Tableau dashboards.

---

## Data & preparation
- Read CSVs and column-standardized with **janitor::clean_names()**.  
- Parsed `started_at`/`ended_at` with **lubridate**; computed `ride_length` in minutes.  
- Filters: `ride_length > 1`, non-missing `member_casual`, valid station ids.  
- Feature engineering: weekday factors, hour of day, month/season flags.

```r
library(tidyverse); library(lubridate); library(janitor)

files <- list.files("data_raw", pattern="\\.csv$", full.names=TRUE)

all_trips <- files %>%
  map_df(readr::read_csv) %>%
  clean_names() %>%
  mutate(
    started_at = ymd_hms(started_at),
    ended_at   = ymd_hms(ended_at),
    ride_length = as.numeric(difftime(ended_at, started_at, units = "mins")),
    day_of_week = wday(started_at, label = TRUE),
    hour        = hour(started_at)
  ) %>%
  filter(ride_length > 1, !is.na(member_casual)) %>%
  drop_na()
