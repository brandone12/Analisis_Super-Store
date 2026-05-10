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
- If `LogSales` / `LogProfit` exist, show their histograms side by side with the originals.
- Boxplot of `Sales` by `Category`.
- **Violin plot** of `Profit` by `Category` (shows distribution shape better than boxplot).
- Bar chart of transaction count by `Segment`, `Category`, and `Region`.
- Distribution of `Discount` values.

### 3. Bivariate analysis
- Scatter plot: `Sales` vs `Profit`, colored by `Category`.
- **Spearman correlation matrix** of all numeric features (Spearman captures non-linear relationships). Display as a heatmap with annotated values.
- **Pairplot** of `Sales`, `Profit`, `Discount`, `ShippingDuration` colored by `Category` — limit to these 4 variables so the plot is readable.
- Boxplot: `Profit` by `Ship Mode` and `Profit` by `Segment`.

### 4. Segment analysis
- Create a pivot table: average `Profit` by `Category` (rows) × `Segment` (columns).
- Display it as a heatmap so you can see which (Category, Segment) combinations are most and least profitable.
- Bar chart: total `Sales` and `Profit` by `Category_Segment` (top 10).

### 5. Time analysis
- Line chart: monthly `Sales` and `Profit` over time.
- Overlay a **3-month rolling mean** to smooth out noise and show the trend clearly.
- Bar chart: average `Profit` by `OrderDayOfWeek` and by `OrderMonth`.

### 6. Outlier spotlight
- Show the 5 transactions with the highest `Profit` and the 5 with the lowest `Profit`.
- Show the 5 transactions with the highest `Sales`.
- Briefly discuss: are these real customers or data entry issues?

### 7. Key insights
- Write 4-6 markdown bullet points summarizing findings. Each point must include a concrete number:
  - Which category is most profitable and by how much (e.g., "Technology generates $X vs $Y from Furniture").
  - Which region or segment underperforms.
  - How discount levels affect profit (e.g., "High discount orders have X% lower profit margin").
  - Any seasonal patterns (best/worst month for profit).
