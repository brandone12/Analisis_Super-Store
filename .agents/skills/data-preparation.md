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

### 2. Parse dates
- Convert `Order Date` and `Ship Date` to datetime.
- Create `DeliveryTime` = `Ship Date` - `Order Date` (in days).

### 3. Handle missing values
- Report null counts per column.
- If `Postal Code` has nulls, consider dropping or forward-filling.
- For any nulls in quantitative columns (`Sales`, `Profit`), note they must NOT be dropped — investigate and impute if needed.

### 4. Feature engineering
Create these new columns:
- `OrderYear`, `OrderMonth`, `OrderDayOfWeek` from `Order Date`
- `ProfitMargin` = `Profit / Sales` (handle division by zero with NaN → fill 0)
- `DiscountLevel`: bin Discount into `["None", "Low", "Medium", "High"]`
- Encode categoricals (`Category`, `Sub-Category`, `Segment`, `Ship Mode`, `Region`) using one-hot encoding or label encoding.

### 5. Drop high-cardinality / low-value columns
Drop: `Row ID`, `Order ID`, `Customer ID`, `Customer Name`, `Product ID`, `Product Name`, `Country`, `Postal Code`.

### 6. Final check
- Confirm no nulls remain in the final feature set.
- Display the cleaned dataframe's shape and first 5 rows.
- Save the cleaned dataset to `superstore_clean.csv` for the next phase.
