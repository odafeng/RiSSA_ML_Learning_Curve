# RiSSA_ML_Learning_Curve

**Machine Learning-Based Risk Modeling for Learning Curve Assessment in Robotic Left-Sided Colorectal Cancer Surgery**

> Associated publication: Huang SF et al., *Journal of Robotic Surgery*, 2026.

## Overview

This repository provides the de-identified datasets and analysis code for a study evaluating the surgical learning curve of robotic-assisted left-sided colorectal resection using machine learning–based risk adjustment. A logistic regression model trained on a historical laparoscopic cohort is applied to a prospective robotic cohort, and cumulative performance is monitored with risk-adjusted CUSUM (RA-CUSUM) charts.

## Repository structure

```
├── data/
│   ├── Lap_Cohort.csv            # Historical laparoscopic cohort (n = 211)
│   ├── Robot_Cohort.csv          # Robotic surgery cohort (n = 93)
│   └── data_typed.parquet        # Combined dataset with proper dtypes
├── notebooks/
│   ├── 1.Clean_Type_EDA.ipynb    # Data cleaning, type casting, and EDA
│   └── 2.Training_Model.ipynb    # Model training, evaluation, and RA-CUSUM
└── figures/
    └── RA_CUSUM.tiff             # RA-CUSUM learning curve plot
```

## Data

Two cohort datasets are included, each containing 25 variables covering patient demographics, operative parameters, clinical outcomes, and pathological findings. Both files have been fully de-identified — see the de-identification statement below.

### Data dictionary

| Variable | Description |
|---|---|
| Patient_ID | Sequential case number (de-identified) |
| Gender | 0 = female, 1 = male |
| OP_Year | Year of operation |
| Age | Age at surgery (years) |
| BMI | Body mass index (kg/m²) |
| ASA | ASA physical status classification |
| Procedure_1 | Procedure type (encoded) |
| Protective_Stoma | Diverting stoma created (0 = no, 1 = yes) |
| Procedure_Time(min) | Total operative time in minutes |
| Blood_Loss | Estimated blood loss (mL) |
| Conv_to_Open | Conversion to open surgery (0 = no, 1 = yes) |
| Time_1stFlatus(d) | Days to first flatus |
| LengthStay | Hospital length of stay (days) |
| Major_Complications | Clavien-Dindo grade ≥ III (0 = no, 1 = yes) |
| Anastomotic_Leakage | Anastomotic leak (0 = no, 1 = yes) |
| Unplanned_ICU_Admission | Unplanned ICU admission (0 = no, 1 = yes) |
| Mortality_30days | 30-day mortality (0 = no, 1 = yes) |
| Neoadjuvant | Neoadjuvant chemoradiotherapy (0 = no, 1 = yes) |
| Composite_Adverse_Event | Composite safety endpoint (0 = no, 1 = yes) |
| Is_Rectum | Rectal cancer (0 = no, 1 = yes) |
| From_Anal_Verge(cm) | Distance from anal verge (cm) |
| Tumor_Size(cm) | Tumor size (cm) |
| Distal_Margin(cm) | Distal resection margin (cm) |
| CRM_positivity | Circumferential resection margin positive (0 = no, 1 = yes) |
| No_LNs | Number of lymph nodes harvested |

## Analysis workflow

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

```bash
pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn
```

## De-identification statement

All patient data have been de-identified prior to publication. No protected health information (names, medical record numbers, dates of birth, or exact surgery dates) is included. Patient_ID is a sequential case number that cannot be linked back to any individual. This study was approved by the Institutional Review Board of Kaohsiung Veterans General Hospital.

## License

This repository is made available for academic use. Please cite the associated publication if you use these data or methods in your work.
