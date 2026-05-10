---
name: predictive-modeling
description: Predictive modeling skill for training and selecting a regression model to predict Profit on the Superstore dataset. Load and follow these instructions when the orchestrator enters Phase 3.
---

# Predictive Modeling — Superstore Dataset

## Objective
Train, evaluate, and select the best regression model to predict `Profit` using the cleaned features.

## Steps

### 1. Load prepared data
- Read `superstore_clean.csv`.
- Separate features `X` (all numeric columns except `Profit`) and target `y = Profit`.
- If `LogProfit` exists, do **not** include it in `X` — it's a transformed version of the target.
- If `IsOutlier` exists, keep it in `X` (the model can learn to discount outliers).

### 2. Train/test split
- `train_test_split(X, y, test_size=0.2, random_state=42)`.

### 3. Train models
Train these three regressors with default parameters:
- **Linear Regression** (baseline — simple and interpretable)
- **Ridge Regression** (`alpha=1.0` — like linear but penalizes large coefficients)
- **Random Forest Regressor** (`n_estimators=100, random_state=42` — handles non-linearity well)

### 4. Evaluate
For each model compute on the test set:
- `R²` (coefficient of determination — how much variance is explained)
- `RMSE` (root mean squared error — in same units as Profit)
- `MAE` (mean absolute error — average error in dollars)
- **MAPE** (mean absolute percentage error — average % error, very intuitive)

Display results in a comparison table.

### 5. Cross-validation (best model only)
- Take the model with the highest test R².
- Run `cross_val_score` with 5 folds and report the mean R² and standard deviation.
- Discuss: if the cross-val mean is close to the test R², the model is stable; if it's much lower, the model may be overfitting.

### 6. Hyperparameter tuning (Random Forest only)
Only if Random Forest is the best model:
- Use `GridSearchCV` with 5-fold CV to test a small grid:
  - `n_estimators`: `[50, 100, 200]`
  - `max_depth`: `[None, 10, 20]`
- Report the best parameters and the improvement in R².

### 7. Residual analysis (Linear Regression only)
- Plot a histogram of residuals (errors = actual - predicted).
- Plot a **Q-Q plot** to check if residuals follow a normal distribution (one of Linear Regression's assumptions).
- Discuss: if residuals are roughly normal and centered at 0, the linear model is reasonable.

### 8. Feature importance
- For the best model (by R² after tuning, if applicable), extract and plot feature importance / coefficients.
- Print a horizontal bar chart of the top 10 most important features.

### 9. Model selection
Write a markdown cell justifying the final choice:
- Which model performed best and by how much (R², RMSE, MAPE).
- Why that model is appropriate for this data (e.g., handles non-linearity, interpretability).
- Any caveats (e.g., profit prediction is noisy, model may struggle with extreme values).
