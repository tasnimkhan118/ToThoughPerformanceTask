# To-Through-Candidate-Performance-Task
A modular R analytics pipeline evaluating 8th-grade student demographics, cohort trends, and high school graduation rates based on flexible attendance and GPA combinations.

# 8th-Grade Student Cohort & Graduation Outcomes Analysis

## Purpose
This repository contains an R-based data analytics workflow designed to identify, isolate, and evaluate target student segments within our Network. Specifically, this analysis focuses on a priority student population: **students with high 8th-grade attendance rates (above 90%) but low GPAs (below 3.0).** The codebase utilizes a modular, functional approach to track how these student profiles change over time, evaluate their demographic baseline comparisons, and analyze their long-term high school graduation outcomes across different cohorts and middle schools.

---

## Data Inputs & File Structure

To run this analysis, ensure the following three raw data files are saved in your local working directory alongside the script:

* **`File1.csv` (Student Roster):** Baseline demographic data including `studID`, `raceEth`, `gender`, `schoolID`, `schoolYear8th`, and `schoolType`.
* **`File2.csv` (8th Grade Outcomes):** Academic performance tracking data containing `GPA`, `daysAttend`, and `daysEnroll`.
* **`File3.csv` (High School Outcomes):** Long-term metrics including `hsID` and `gradStatus` (where `1` indicates graduated).

---

## Code Structure & Logic

The script (`TasnimKhan_T&T.Rmd`) progresses through a data pipeline:

1.  **Data Cleaning & Filtering:** Merges the student rosters, handles missing data trends (such as isolated missing GPAs), and filters out data entry anomalies (e.g., GPAs listed as `8.0` on a standard `4.0` scale) to avoid skews.
2.  **Creating Categorical Variables:** Calculates precise attendance rates (`(daysAttend / daysEnroll) * 100`) and categorizes students into binary segments (`High` vs. `Low`) for both attendance and GPA metrics.
3.  **Modular Analysis Sub-Functions:**
    * `group_over_time()`: Measures if the percentage of students in this group changed over time (across different cohorts of 8th graders).
    * `race_composition()`: Compares the racial/ethnic layout of the target group against the entire student population.
    * `graduation_rate()`: Computes the overall baseline high school graduation rate for the group.
    * `graduation_by_school()`: Evaluates how graduation rates for the target group vary by the middle school they attended.
    * `graduation_by_cohort()`: Tracks changes in high school graduation rates across different calendar years.
4.  **Master Function (`analyze_group`):** Sequentially calls all five sub-functions to print a unified and clean report to the console for any chosen attendance and GPA criteria.

---

## Instructions: How to Run the Code

### Prerequisites
Make sure you have [R and RStudio](https://posit.co/download/rstudio-desktop/) installed. You will also need the `tidyverse` package suite. If you don't have it installed, run the following command in your R console:

```r
install.packages("tidyverse")
