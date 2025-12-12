# STAT 540 – Project 1 (Guided): EDA and ggplot2 Visualization

This project is a **guided exploratory data analysis (EDA)** exercise using the `us_contagious_diseases` dataset from the **`dslabs`** package. The main goal is to practice working with tidy data and creating clear visualizations in **R** with **ggplot2**.

---

## 🔍 Dataset

- **Dataset:** `us_contagious_diseases`
- **Source package:** `dslabs`
- **Content:** Historical records of infectious diseases in the United States, including:
  - Disease type (e.g., measles, hepatitis A, etc.)
  - State and year
  - Population
  - Case counts
  - `weeks_reporting` – number of weeks with surveillance data

---

## 📂 Project Overview

The project is structured into **three main parts** inside `Project 1-1.Rmd`:

### Part 1 – Weeks Reporting (EDA with ggplot2)

Focus: Understanding the `weeks_reporting` variable.

You:
- Load the `us_contagious_diseases` data.
- Explore what `weeks_reporting` represents.
- Create:
  - A histogram of `weeks_reporting`.
  - Faceted histograms by disease using `facet_wrap()`.
  - Visual displays of how weeks reported vary by disease, state, and year.

This part emphasizes:
- Basic EDA
- Histograms
- Faceting for comparisons across diseases

---

### Part 2 – Rate Calculation (Raw vs Adjusted)

Focus: Computing **disease rates per 100,000 people** and correcting for partial reporting.

You:
- Filter the data to:
  - Exclude Alaska and Hawaii.
  - Keep only records with `weeks_reporting > 0`.
  - Create a subset for **North Carolina** (`nc_subset`).
- Compute:
  - **Unadjusted rate**:  
    \[
    \text{raw_rate} = \frac{\text{count}}{\text{population}} \times 100000
    \]
  - **Adjusted rate**, which accounts for the number of weeks reporting.
- Compare:
  - Adjusted vs unadjusted rates.
  - North Carolina vs the overall US rate for a chosen disease.
- Visualize:
  - A scatterplot of adjusted vs unadjusted rates, colored by `weeks_reporting`, with an identity line for comparison.

This part emphasizes:
- Rate calculations
- The impact of incomplete data
- Interpretation of adjusted vs unadjusted metrics

---

### Part 3 – National Trends Over Time

Focus: Big-picture trends in disease rates across the entire US.

You:
- Group data by **disease** and **year**.
- Compute the **overall US adjusted rate** for each disease and year using:
  - Summed counts and populations across states.
- Create line plots showing:
  - How disease rates evolve over time for the entire US.
  - Comparisons across diseases.
- Optionally compare:
  - A specific state (e.g., North Carolina) to US-wide trends.

This part emphasizes:
- `group_by()` and `summarize()`
- Time series style plots
- Comparing state-level and national patterns

---

## 🧠 Skills Practiced

- Using **tidyverse** (`dplyr`, `ggplot2`) with the pipe operator `%>%`
- EDA with histograms, faceting, and box/line plots
- Correct computation of **per-capita rates**
- Adjusting for **incomplete reporting** using `weeks_reporting`
- Building interpretable visualizations for public health data

---

## 📄 Main File

- `Project 1-1.Rmd`  
  Contains all code chunks, graphics, and short written answers for Parts 1–3. Knitting this file produces the final HTML notebook for the project.
