# De-identification Statement

## Study Approval

This study was reviewed and approved by the **Institutional Review Board (IRB) of Kaohsiung Veterans General Hospital**. The requirement for individual informed consent was waived due to the retrospective, observational nature of the study and the use of fully de-identified data.

## De-identification Process

All data shared in this repository have been de-identified in accordance with applicable privacy regulations and institutional policies. The following measures were applied before public release:

1. **Direct identifiers removed** — All personal identifiers have been stripped from the dataset, including but not limited to: patient names, medical record numbers, dates of birth, admission/discharge dates, and any other information that could directly identify an individual.

2. **Sequential re-coding** — Each patient record is assigned a sequential `Patient_ID` (1, 2, 3, …) that bears no relationship to any original identifier or medical record number.

3. **Date generalization** — Specific procedure dates have been replaced with the operating year (`OP_Year`) only; no exact dates are present.

4. **Age reporting** — Patient ages are reported as continuous values rounded to one decimal place and are not accompanied by dates of birth.

5. **Small-cell suppression** — Where applicable, rare categories or extreme values have been reviewed to ensure that no individual can be re-identified through unique combinations of quasi-identifiers.

## Protected Health Information (PHI)

No protected health information (PHI), as defined by HIPAA and analogous regulations, is contained in any file within this repository. The datasets (`Lap_Cohort.csv`, `Robot_Cohort.csv`, `data_typed.parquet`) contain only coded, aggregate-level clinical variables that cannot be linked back to any individual patient.

## Data Use Restrictions

This dataset is provided strictly for **academic and research purposes**. Redistribution or any attempt to re-identify individuals is prohibited.

## Contact

For questions regarding data governance or de-identification, please contact the corresponding author of the associated publication.
