---
name: data-preparation
description: Data wrangling skill for cleaning, transforming, and preparing the Superstore dataset for predictive modeling. Load and follow these instructions when the orchestrator enters Phase 1.
---

# Data Preparation — Superstore Dataset

## Objective
Clean, transform, and engineer features from `Sample - Superstore.csv` so the resulting dataset is ready for EDA and predictive modeling.

## Steps

### 1. Load and inspect
- Load the CSV into a pandas DataFrame.
- Display `df.info()`, `df.shape`, `df.head()`, and `df.describe()`.
- Check for nulls: `df.isnull().sum()`.
- Report the skewness of `Sales` and `Profit` using `df[['Sales','Profit']].skew()`.

### 2. Parse dates
- Convert `Order Date` and `Ship Date` to datetime.
- Create `ShippingDuration` = `Ship Date` - `Order Date` (in days, as integer).

### 3. Handle missing values
- Report null counts per column.
- If `Postal Code` has nulls, consider dropping or forward-filling.
- For any nulls in quantitative columns (`Sales`, `Profit`), note they must NOT be dropped — investigate and impute if needed.

### 4. Outlier detection
- Compute IQR for `Sales` and `Profit`.
- Create a boolean column `IsOutlier` that flags rows where either `Sales` or `Profit` falls outside 1.5×IQR.
- **Do not drop outliers** — keep the column so the analyst can decide later.
- Show how many rows are flagged and discuss briefly.

### 5. Feature engineering
Create these new columns:
- `OrderYear`, `OrderMonth`, `OrderDayOfWeek` from `Order Date`
- `IsWeekend`: 1 if `OrderDayOfWeek` is Saturday or Sunday, else 0
- `ProfitMargin` = `Profit / Sales` (handle division by zero with NaN → fill 0)
- `SalesPerDay` = `Sales / (ShippingDuration + 1)` (avoid division by zero)
- `Category_Segment`: concatenation of `Category` and `Segment` (for possible future grouping)
- `DiscountLevel`: bin Discount into `["None", "Low", "Medium", "High"]`:
  - 0 → "None", (0, 0.2] → "Low", (0.2, 0.5] → "Medium", > 0.5 → "High"
- If `Sales` or `Profit` have high skew (> 1.0), apply `np.log1p` to create `LogSales` and `LogProfit` columns. Keep the original columns too.

### 6. Encode categoricals
- Use one-hot encoding with `pd.get_dummies(..., drop_first=True)` on:
  `Category`, `Sub-Category`, `Segment`, `Ship Mode`, `Region`
- Explain that `drop_first=True` avoids multicollinearity (predictors that are too correlated with each other).

### 7. Drop high-cardinality / low-value columns
Drop: `Row ID`, `Order ID`, `Customer ID`, `Customer Name`, `Product ID`, `Product Name`, `Country`, `Postal Code`.

### 8. Final check
- Confirm no nulls remain in the final feature set.
- Display the cleaned dataframe's shape and first 5 rows.
- Report memory usage: `df.info(memory_usage='deep')`.
- Save the cleaned dataset to `superstore_clean.csv` for the next phase.
