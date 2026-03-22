# RiSSA_ML_Learning_Curve

ML-based risk modeling for learning curve assessment in robotic left-sided colorectal cancer surgery.

Associated publication: **Huang SF**, Tan YL, Hsu CW, et al. Machine learning–based risk modeling for safety-focused learning curve assessment in robotic left-sided colorectal cancer surgery. *J Robotic Surg.* 2026;20:190.

## Data

Two de-identified cohort files are provided:

- `Lap_Cohort.csv` — laparoscopic cohort (historical comparison)
- `Robot_Cohort.csv` — robotic cohort (study group)
- `data_typed.parquet` — combined dataset with enforced column types

## Notebooks

- `Notebooks/1.Clean_Type_EDA.ipynb` — data cleaning, type casting, and exploratory data analysis
- `Notebooks/2.Training_Model.ipynb` — model training and evaluation

## Data dictionary

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

## De-identification statement

All patient data have been de-identified prior to publication. No protected health information (names, medical record numbers, dates of birth, or exact surgery dates) is included. Patient_ID is a sequential case number that cannot be linked back to any individual. This study was approved by the Institutional Review Board of Kaohsiung Veterans General Hospital.

## License

This dataset is provided for academic and research purposes only.
