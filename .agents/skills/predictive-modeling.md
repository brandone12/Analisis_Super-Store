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

### 2. Train/test split
- `train_test_split(X, y, test_size=0.2, random_state=42)`.

### 3. Train models
Train these three regressors with default parameters:
- **Linear Regression** (baseline)
- **Random Forest Regressor** (`n_estimators=100, random_state=42`)
- **Ridge Regression** (`alpha=1.0`)

### 4. Evaluate
For each model compute on the test set:
- `R^2` (coefficient of determination)
- `RMSE` (root mean squared error)
- `MAE` (mean absolute error)

Display results in a comparison table.

### 5. Feature importance
- For the best model (by R²), extract and plot feature importance / coefficients.
- Print a horizontal bar chart of the top 10 most important features.

### 6. Model selection
Write a markdown cell justifying the final choice:
- Which model performed best and by how much.
- Why that model is appropriate for this data (e.g., handles non-linearity, interpretability).
- Any caveats (e.g., profit prediction is noisy, model may struggle with extreme values).
