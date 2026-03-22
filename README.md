# RiSSA_ML_Learning_Curve

**Machine Learning-Based Risk Modeling for Learning Curve Assessment in Robotic Left-Sided Colorectal Cancer Surgery**

> Associated publication: Huang SF et al., *Journal of Robotic Surgery*, 2026.

## Overview

This repository provides the de-identified datasets and analysis code for a study evaluating the surgical learning curve of robotic-assisted left-sided colorectal resection using machine learning–based risk adjustment. A logistic regression model trained on a historical laparoscopic cohort is applied to a prospective robotic cohort, and cumulative performance is monitored with risk-adjusted CUSUM (RA-CUSUM) charts.

## Repository Structure

```
RiSSA_ML_Learning_Curve/
├── Notebooks/
│   ├── 1.Clean_Type_EDA.ipynb   # Data cleaning, type casting, and exploratory analysis
│   └── 2.Training_Model.ipynb   # Model training, evaluation, and RA-CUSUM monitoring
├── Lap_Cohort.csv               # Historical laparoscopic cohort (n = 211)
├── Robot_Cohort.csv             # Robotic surgery cohort (n = 93)
├── data_typed.parquet           # Combined dataset with proper dtypes
├── DATA_DICTIONARY.md           # Variable definitions and coding schemes
├── DEIDENTIFICATION.md          # De-identification statement
└── .gitignore
```

## Data

Two cohort datasets are included, each containing 25 variables covering patient demographics, operative parameters, clinical outcomes, and pathological findings. Both files have been fully de-identified — see [`DEIDENTIFICATION.md`](DEIDENTIFICATION.md) for details. A complete variable-level description is available in [`DATA_DICTIONARY.md`](DATA_DICTIONARY.md).

## Analysis Workflow

### Notebook 1 — Data Cleaning & EDA

- Loads `Lap_Cohort.csv` and `Robot_Cohort.csv`; adds an `approach` indicator (1 = robotic, 0 = laparoscopic).
- Handles missing values, coerces data types (ordinal, nominal, binary, numerical).
- Produces descriptive statistics, distribution plots, and a missing-data summary.
- Outputs `data_typed.parquet` for downstream modeling.

### Notebook 2 — Model Training & Learning Curve Monitoring

- **Target variable**: `Composite_Adverse_Event` (binary).
- **Features**: `ASA`, `Age`, `BMI`, `Is_Rectum`.
- **Model**: Logistic regression with median imputation + standardization; hyperparameter tuning via `GridSearchCV`.
- **Validation**: 5-fold CV (mean AUC ≈ 0.665) and 1000-iteration bootstrap confidence intervals.
- **Learning curve monitoring**: RA-CUSUM plots applied to the robotic cohort to track cumulative deviation between observed and predicted adverse event rates.

## Requirements

- Python ≥ 3.9
- pandas, numpy, matplotlib, seaborn, scipy, statsmodels, scikit-learn

Install dependencies:

```bash
pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn
```

## Ethics & Data Use

This study was approved by the Institutional Review Board of Kaohsiung Veterans General Hospital. All data have been de-identified in compliance with applicable regulations. This dataset is provided for **academic and research purposes only**.

## License

This repository is made available for academic use. Please cite the associated publication if you use these data or methods in your work.
