# AGENTS.md — Análisis-Superstore

## Orchestrator pattern
The main agent acts as **orquestador** — it owns the analysis plan and delegates
domain work to skills loaded per phase:

| Phase | Skill file |
|---|---|
| 1. Data Wrangling | `.agents/skills/data-preparation.md` |
| 2. EDA | `.agents/skills/exploratory-analysis.md` |
| 3. Predictive Modeling | `.agents/skills/predictive-modeling.md` |

The orchestrator never writes code directly in phases 1-3; it loads the
appropriate skill and follows that skill's instructions. Each skill produces
cells for `superstore-analysis.ipynb`.

## Stack & Setup
- Python 3.11+, **Poetry** for deps (no `requirements.txt`)
- `poetry install` → `poetry run jupyter notebook` to work
- `poetry add <lib>` for new dependencies
- Libraries: pandas, numpy, matplotlib, seaborn, scipy, scikit-learn

## Dataset
- `Sample - Superstore.csv`: 9994 retail transactions (classic Tableau sample)
- Columns: Row ID, Order ID, Order/Ship Date, Ship Mode, Customer, Segment,
  Geography, Product, Category, Sub-Category, Sales, Quantity, Discount, Profit

## Workflow
- **Spec First** — present a plan before editing code
- Target variable: **Profit** (regression)
- Do not ignore nulls in `Profit` or `Sales` (quantitative columns)

## No infrastructure
- No tests, no CI, no linter/formatter/typechecker
- No notebooks committed yet; all work in Jupyter at repo root
