# Data Dictionary

This document describes the 25 variables contained in `Lap_Cohort.csv` and `Robot_Cohort.csv`. The combined dataset (`data_typed.parquet`) includes one additional variable, `approach`.

## Variable Definitions

| # | Variable | Type | Description | Values / Units |
|---|----------|------|-------------|----------------|
| 1 | `Patient_ID` | Integer | Sequential case identifier (non-identifiable) | 1, 2, 3, … |
| 2 | `Gender` | Binary | Patient sex | 0 = Female, 1 = Male |
| 3 | `OP_Year` | Integer | Year the operation was performed | e.g., 2023, 2024, 2025 |
| 4 | `Age` | Numerical | Patient age at the time of surgery | Years (decimal) |
| 5 | `BMI` | Numerical | Body mass index | kg/m² |
| 6 | `ASA` | Ordinal | American Society of Anesthesiologists physical status classification | 1, 2, 3, 4 |
| 7 | `Procedure_1` | Nominal | Type of surgical procedure performed | 1 = Anterior resection (AR), 2 = Left hemicolectomy, 3 = Low anterior resection (LAR) |
| 8 | `Protective_Stoma` | Binary | Whether a diverting stoma was created | 0 = No, 1 = Yes |
| 9 | `Procedure_Time(min)` | Numerical | Total operative time | Minutes |
| 10 | `Blood_Loss` | Numerical | Estimated intraoperative blood loss | mL |
| 11 | `Conv_to_Open` | Binary | Conversion to open surgery | 0 = No, 1 = Yes |
| 12 | `Time_1stFlatus(d)` | Numerical | Time to first flatus after surgery | Days |
| 13 | `LengthStay` | Numerical | Length of hospital stay | Days |
| 14 | `Major_Complications` | Binary | Occurrence of major postoperative complications (Clavien–Dindo ≥ III) | 0 = No, 1 = Yes |
| 15 | `Anastomotic_Leakage` | Binary | Occurrence of anastomotic leakage | 0 = No, 1 = Yes |
| 16 | `Unplanned_ICU_Admission` | Binary | Unplanned admission to intensive care unit | 0 = No, 1 = Yes |
| 17 | `Mortality_30days` | Binary | Death within 30 days of surgery | 0 = No, 1 = Yes |
| 18 | `Neoadjuvant` | Binary | Whether the patient received neoadjuvant therapy | 0 = No, 1 = Yes |
| 19 | `Composite_Adverse_Event` | Binary | Composite outcome indicating any adverse event (target variable for ML model) | 0 = No, 1 = Yes |
| 20 | `Is_Rectum` | Binary | Tumor located in the rectum | 0 = No (colon), 1 = Yes (rectum) |
| 21 | `From_Anal_Verge(cm)` | Numerical | Distance of the tumor from the anal verge | cm |
| 22 | `Tumor_Size(cm)` | Numerical | Maximum tumor diameter | cm |
| 23 | `Distal_Margin(cm)` | Numerical | Distal resection margin length | cm |
| 24 | `CRM_positivity` | Binary | Circumferential resection margin positivity | 0 = Negative, 1 = Positive |
| 25 | `No_LNs` | Numerical | Number of lymph nodes harvested | Count |

## Additional Variable in Combined Dataset

| # | Variable | Type | Description | Values |
|---|----------|------|-------------|--------|
| 26 | `approach` | Binary | Surgical approach (added during data merging) | 0 = Laparoscopic, 1 = Robotic |

## Variable Categories

For modeling purposes, variables are grouped as follows:

- **Ordinal**: `ASA`
- **Nominal**: `Procedure_1`
- **Binary**: `Gender`, `Protective_Stoma`, `Conv_to_Open`, `Major_Complications`, `Anastomotic_Leakage`, `Unplanned_ICU_Admission`, `Mortality_30days`, `Neoadjuvant`, `Composite_Adverse_Event`, `Is_Rectum`, `CRM_positivity`
- **Numerical**: `Age`, `BMI`, `Procedure_Time(min)`, `Blood_Loss`, `Time_1stFlatus(d)`, `LengthStay`, `From_Anal_Verge(cm)`, `Tumor_Size(cm)`, `Distal_Margin(cm)`, `No_LNs`

## Missing Data

Some records contain missing values (encoded as `NaN`). The notebook `1.Clean_Type_EDA.ipynb` documents the missing-data pattern and handling strategy.
