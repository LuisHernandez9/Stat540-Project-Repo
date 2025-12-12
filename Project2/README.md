# STAT 540 – Project 2: Election Polls and Polling Bias

This project analyzes **US election polling data** to study how well pre-election polls match actual election results, with a particular focus on the **2016 election** and comparisons across earlier years. Using R and the `tidyverse`, the project explores **polling accuracy, spread, and bias** at both the national and state levels.

---

## 📊 Dataset

- **File:** `elections_polls.RData`
- **Main object:** `polls` (a `data.frame`)
- **Contains polling data for:**
  - Multiple election years (e.g., 2008, 2010, 2012, 2014, 2016)
  - Different election types: presidential, senate, and house races
  - State-level and some more localized races

Key columns include:

- `race` – race identifier (`year_electiontype_location`)
- `race_state` – race identifier at the state level
- `state`, `state_long` – state abbreviations and full names  
- `type` – race type (e.g., `Pres`, `Sen-G`, `House-G`)
- `year` – election year  
- `pollster` – name of the polling organization  
- `samplesize` – number of respondents  
- `startdate`, `enddate` – field dates for each poll  
- `democrat_name`, `republican_name` – candidate names  
- `democrat_poll`, `republican_poll` – polled vote shares  
- `democrat_result`, `republican_result` – actual election results  

---

## 🧩 Project Overview

All work is done in **`STAT540 - Project 2.Rmd`**, which is structured into several parts. The main goals are:

1. **Clean and subset polling data**
2. **Compute poll “spread” and compare it to actual election results**
3. **Aggregate polls by race (state/year)**
4. **Quantify and visualize polling error/bias**
5. **Compare patterns across years and race types**

### Part 1 – Late-Stage Polls (October–November)

Focus: Restricting to **polls close to Election Day**.

You:
- Use `enddate` to extract the month.
- Filter `polls` to keep only polls ending in **October or November**.
- Work with this filtered set for the rest of the analysis.

This isolates polls most relevant to final pre-election expectations.

---

### Part 2 – Poll vs Actual Spread

Focus: Measuring how far off the polls are from reality.

You:
- Compute the **poll “spread”** between the two main parties  
  (e.g., Democrat % – Republican %).
- Compute the **actual spread** using election results.
- Add both the **poll spread** and **actual spread** (often called `spread` and `spread_act`) as new columns to the data.

This creates the core variables used to measure polling accuracy.

---

### Part 3 – Collapsing Polls by Race

Focus: Moving from individual polls to **race-level summaries**.

You:
- Group polls by **race characteristics** (e.g., `type`, `year`, `state`).
- Create a new data frame, often called `reduced_polls`, containing:
  1. Mean poll spread per race  
  2. Standard deviation of spread  
  3. Mean actual spread (`spread_act`)  
  4. Number of polls per race  
  5. Race information (year, state, type)

This step summarizes multiple polls for the same race into a single “race-level” record.

---

### Later Parts (4–9) – Polling Error & Bias

Focus: Understanding **systematic polling bias** and **uncertainty**.

You typically:

- Define a **bias term** (e.g., poll spread – actual spread).
- Examine how bias behaves by:
  - **Year** (e.g., is 2016 different from earlier years?)
  - **Race type** (Presidential vs Senate vs House)
  - **State** (which states had the largest polling errors?)
- Construct **intervals** (using standard deviations or standard errors) around mean spreads for each state and visualize them.
- Make plots such as:
  - State-level point estimates with **error bars** for the 2016 presidential race.
  - Distributions of bias across races and election types.
- Answer interpretive questions like:
  - Are bias terms centered around zero?
  - Are polls systematically more favorable to one party?
  - Are some races or years more uncertain than others?

The project blends **data wrangling**, **summary statistics**, and **visualization** to assess how reliable pre-election polls are.

---

## 🧠 Skills Practiced

- Loading RData files and inspecting structures with `str()`
- Data wrangling with **`dplyr`** (`filter`, `mutate`, `group_by`, `summarize`)
- Creating new variables (spread, actual spread, bias)
- Aggregating poll-level data to race-level summaries
- Visualizing uncertainty and bias with **`ggplot2`**
- Interpreting real-world consequences of polling error

---

## 📄 Main File

- **`STAT540 - Project 2.Rmd`**  
  Contains all code, written answers, and plots. Knitting this notebook produces an HTML report that walks through the entire polling bias analysis.
