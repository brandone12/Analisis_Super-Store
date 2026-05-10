---
name: exploratory-analysis
description: EDA skill for statistical analysis and visualization of the Superstore dataset. Load and follow these instructions when the orchestrator enters Phase 2.
---

# Exploratory Data Analysis — Superstore Dataset

## Objective
Explore the cleaned dataset to uncover patterns, correlations, and insights. All work goes into `superstore-analysis.ipynb`.

## Steps

### 1. Load cleaned data
- Read `superstore_clean.csv`.
- Display basic info and summary statistics.

### 2. Univariate analysis
- Histogram of `Sales` and `Profit` (note skew).
- Boxplot of `Sales` by `Category`.
- Bar chart of transaction count by `Segment`, `Category`, and `Region`.
- Distribution of `Discount` values.

### 3. Bivariate analysis
- Scatter plot: `Sales` vs `Profit`, colored by `Category`.
- Correlation heatmap of all numeric features.
- Boxplot: `Profit` by `Ship Mode` and `Profit` by `Segment`.

### 4. Time analysis
- Line chart: monthly `Sales` and `Profit` over time.
- Bar chart: `Profit` by `OrderDayOfWeek`.

### 5. Key insights
- Write 3-5 markdown bullet points summarizing findings (e.g., which category is most profitable, which region underperforms, discount impact on profit).
