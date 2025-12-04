# 🏆 TSA and Physical Demands — Data Analysis  
### Beyond Formations: Team Surface Area and Its Influence on Physical Demands Across Defensive Phases in the 2022 FIFA World Cup

This repository contains the full data analysis workflow and dataset used in the study:

**“Beyond Formations: Team Surface Area and Its Influence on Physical Demands Across Defensive Phases in the 2022 FIFA World Cup.”**  
Author: **Danilo Arruda**  
Date: **2025**

---

## 📂 Repository Structure
TSA-and-Physical-Demands-Data-Analysis/
│
├── data/dataset/tsa_data.csv # Clean dataset used in the analysis
│  
├── tsa-data-analysis.Rmd # Full analysis in RMarkdown format
├── tsa-data-analysis.html # Full analysis in html format
├── permutation_anova_results.csv
├── regression_slopes_results.csv
├── pairwise_permutation_effect_sizes.csv
│
└── README.md


---
## Dataset Description
The dataset contains player-level performance and tactical surface area metrics from matches in the 2022 FIFA World Cup.
Each row represents a single player in a single match, including their physical outputs, positional role, team system, and team surface area (TSA) measures across different tactical phases.

The dataset includes the following groups of variables:

1️⃣ Match Metadata
Column	Description
match	Full match label (e.g., Argentina 3 – 3 France)
match_string	Machine-friendly match ID (e.g., Argentina_France)
match_number	The official FIFA match number
team	Team of the player (e.g., Argentina)
opponent	Opposing team
system	Tactical formation/system used (e.g., 433, 442, 532)

2️⃣ Player Information
Column	Description
player	Player name
number	Jersey number
position	Functional position (e.g., CM, FW, WG)

3️⃣ Physical Performance Metrics

These represent external load measures collected during match play.

Variable	Description
total_distance	Total distance covered (m)
zone_1–zone_5	Distance covered at intensity bands (m), where zone_5 is highest intensity
high_speed_runs	Number of high-speed actions
sprints	Number of sprints
top_speed	Maximum speed reached (km/h)


4️⃣ Possession Phase Surface Area (TSA) Variables

Team surface area (width × height) during attacking phases:

Variable	Meaning
possession_build_width, possession_build_height, possession_build_area	TSA during early buildup
possession_progression_width, possession_progression_height, possession_progression_area	TSA during midfield progression
possession_third_width, possession_third_height, possession_third_area	TSA in the attacking thid

## 📘 Study Overview

The study investigates how **team surface area (TSA)** — measured across multiple offensive and defensive phases — relates to **physical demands** during the 2022 FIFA World Cup.

### Key Research Questions
1. Does team compactness (surface area) influence physical demands such as:
   - Total distance
   - High-speed running
   - Sprint count
   - Top speed  
2. Do different defensive and offensive areas interact with **team tactical systems**?  
3. Are there system-specific relationships between TSA and physical output?

---

## 🧠 Methodology Summary

### **Data Processing**
- TSA computed as:  
  `width × height` for:
  - Defensive phases (high, mid, low block)  
  - Possession phases (build-up, progression, final third)

### **Statistical Analysis**
- Shapiro-Wilk normality tests  
- Non-parametric **Permutation ANOVA** using `aovp()` with 5000–10000 iterations  
- Interaction testing between:
  - **System** (e.g., 4-3-3, 5-3-2)  
  - **Surface Area Variables**  
- Regression slope estimation per system  
- Pairwise permutation comparisons of slopes when interactions are significant  
- Effect sizes via partial eta-squared (η²)

### **Visualization**
- Automated density plots for all dependent variables  
- Interactive result tables rendered via DT:
  - **Permutation ANOVA Results**
  - **Regression Slopes**
  - **Pairwise Comparisons**

---

## 🚀 Reproducing the Analysis

### 1. Install required R packages:

```r
install.packages(c(
  "dplyr", "tidyr", "ggplot2", "stringr", "broom",
  "kableExtra", "rstatix", "lmPerm", "effectsize", "DT"
))

### 📊 Outputs
The following files are automatically produced:
permutation_anova_results.csv
regression_slopes_results.csv
pairwise_permutation_effect_sizes.csv
Interactive tables appear directly inside the knitted HTML report.


