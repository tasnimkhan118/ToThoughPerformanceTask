# To&Through Candidate Performance Task
An R analytics pipeline evaluating 8th-grade student demographics, cohort trends, and high school graduation rates based on attendance and GPA combinations.

# 8th-Grade Student Cohort & Graduation Outcomes Analysis

## Purpose
This repository contains an R-based data analytics workflow designed to identify, isolate, and evaluate target student segments within our Network. Specifically, this analysis focuses on a priority student population: **students with high 8th-grade attendance rates (above 90%) but low GPAs (below 3.0).** The code tracks how these student profiles change over time, evaluate their demographic baseline comparisons, and analyze their long-term high school graduation outcomes across different cohorts and middle schools.

---

## Code Structure & Logic

The script (`T&T_Analysis.Rmd`) progresses through a data pipeline:

1.  **Data Cleaning & Filtering:** Merges the student rosters, handles missing data trends (such as isolated missing GPAs), and filters out data entry anomalies (e.g., GPAs listed as `8.0` on a standard `4.0` scale) to avoid skews.
2.  **Creating Categorical Variables:** Calculates attendance rates (`(daysAttend / daysEnroll) * 100`) and categorizes students into binary segments (`High` vs. `Low`) for both attendance and GPA metrics.
3.  **Sub-Functions:**
    * `group_over_time()`: Measures if the percentage of students in this group changed over time (across different cohorts of 8th graders).
    * `race_composition()`: Compares the racial/ethnic layout of the target group against the entire student population.
    * `graduation_rate()`: Computes the overall baseline high school graduation rate for the group.
    * `graduation_by_school()`: Evaluates how graduation rates for the target group vary by the middle school they attended.
    * `graduation_by_cohort()`: Tracks changes in high school graduation rates across different calendar years.
4.  **Master Function (`analyze_group`):** Sequentially calls all five sub-functions to print a unified and clean report to the console for any chosen attendance and GPA criteria.

---

## Instructions: How to Run the Code
**Follow these steps to set up your environment and run the analysis from start to finish:**

**1. Before running the script, make sure you have R and RStudio installed.**

**2. Ensure the following three raw data files are saved in your local working directory:**
* **`File1.csv` (Student Roster):** Baseline demographic data including `studID`, `raceEth`, `gender`, `schoolID`, `schoolYear8th`, and `schoolType`.
* **`File2.csv` (8th Grade Outcomes):** Academic performance tracking data including `studID`, `GPA`, `daysAttend`, and `daysEnroll`.
* **`File3.csv` (High School Outcomes):** Long-term metrics including `studID`, `hsID` and `gradStatus` (where `1` indicates graduated).

**3. Load the .Rmd file and set working directory in RStudio.**
* Set your working directory to the file's current location so R can locate your CSV files. In the top menu, navigate to:
* Session > Set Working Directory > To Source File Location

**4. Run the setup chunks sequentially to load libraries, build the data frames, and create the final master dataset with relevent information**
* The current script will load the `tidyverse` library.
* If you don't have it installed, run `install.packages("tidyverse")` in the console

**5. Select which GPA category and Attendance category to analyze and run.**
* Scroll to the final code chunk to select your target student group. Type your metrics into the analyze_group() function.
* GPA group can either be **High** or **Low**
* Attendance group can either be **High** or **Low**




