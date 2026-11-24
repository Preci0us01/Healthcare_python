# Healthcare Admissions, Billing & Length-of-Stay Analysis

An exploratory data analysis (EDA) workflow in Python (⁠ pandas ⁠, ⁠ numpy ⁠, ⁠ matplotlib ⁠, and ⁠ seaborn ⁠) examining patient admission and discharge records, billing totals, care capacity indicators, and temporal billing patterns across ⁠ healthcare_dataset 4.csv ⁠[span_1](start_span)[span_1](end_span).

---

## Project Overview

This notebook prepares raw hospital admission records for analysis by standardizing text fields, parsing admission and discharge dates, deriving length-of-stay durations, and generating summary KPIs alongside monthly and yearly billing visualizations[span_2](start_span)[span_2](end_span).

### Dataset Schema

The dataset includes demographic, clinical, operational, and financial columns[span_3](start_span)[span_3](end_span):

•⁠  ⁠*Patient & Demographics:* ⁠ Name ⁠, ⁠ Age ⁠, ⁠ Gender ⁠, ⁠ Blood Type ⁠[span_4](start_span)[span_4](end_span)
•⁠  ⁠*Clinical & Care:* ⁠ Medical Condition ⁠, ⁠ Doctor ⁠, ⁠ Hospital ⁠, ⁠ Medication ⁠, ⁠ Test Results ⁠[span_5](start_span)[span_5](end_span)
•⁠  ⁠*Admissions & Facilities:* ⁠ Date of Admission ⁠, ⁠ Discharge Date ⁠, ⁠ Admission Type ⁠, ⁠ Room Number ⁠[span_6](start_span)[span_6](end_span)
•⁠  ⁠*Billing & Coverage:* ⁠ Insurance Provider ⁠, ⁠ Billing Amount ⁠[span_7](start_span)[span_7](end_span)

---

## Key Metrics (Snapshot from Notebook Run)

| Metric | Value | Notes |
| :--- | :--- | :--- |
| *Total Billing Amount* | ⁠ N1.4B ⁠[span_8](start_span)[span_8](end_span) | Formatted in billions (⁠ N...B ⁠) in the summary output[span_9](start_span)[span_9](end_span) |
| *Unique Patients* | ⁠ 40.23K ⁠[span_10](start_span)[span_10](end_span) | Calculated via ⁠ .nunique() ⁠ on ⁠ Name ⁠[span_11](start_span)[span_11](end_span) |
| *Unique Doctors* | ⁠ 40.34K ⁠[span_12](start_span)[span_12](end_span) | Calculated via ⁠ .nunique() ⁠ on ⁠ Doctor ⁠[span_13](start_span)[span_13](end_span) |
| *Unique Rooms* | ⁠ 400 ⁠[span_14](start_span)[span_14](end_span) | Calculated via ⁠ .nunique() ⁠ on ⁠ Room Number ⁠[span_15](start_span)[span_15](end_span) |
| *Average Patient Age* | ⁠ 52yrs ⁠[span_16](start_span)[span_16](end_span) | Mean of ⁠ Age ⁠[span_17](start_span)[span_17](end_span) |
| *Total Length of Stay* | ⁠ 860750 days ⁠[span_18](start_span)[span_18](end_span) | Sum of ⁠ Length of Stay ⁠ (⁠ Discharge Date - Date of Admission ⁠)[span_19](start_span)[span_19](end_span) |
| *Average Length of Stay* | ⁠ 15yrs ⁠[span_20](start_span)[span_20](end_span) | Printed from ⁠ Avg_loc.days ⁠ with a ⁠ yrs ⁠ label; verify units before reporting[span_21](start_span)[span_21](end_span) |

---

## Data Cleaning & Feature Engineering

•⁠  ⁠*Date Conversion & Time Features:* Converted ⁠ Date of Admission ⁠ and ⁠ Discharge Date ⁠ with ⁠ pd.to_datetime() ⁠ and extracted ⁠ Month ⁠ (three-letter month names, e.g., ⁠ Jan ⁠) and ⁠ Year ⁠ (four-digit year)[span_22](start_span)[span_22](end_span).
•⁠  ⁠*String Normalization:* Applied ⁠ .str.strip().str.title() ⁠ to ⁠ Name ⁠ and ⁠ Insurance Provider ⁠ to clean extra whitespace and inconsistent casing (for example, ⁠ Bobby JacksOn ⁠ to ⁠ Bobby Jackson ⁠)[span_23](start_span)[span_23](end_span).
•⁠  ⁠*Length of Stay:* Calculated ⁠ df['Length of Stay'] = df['Discharge Date'] - df['Date of Admission'] ⁠ as a ⁠ timedelta ⁠ column[span_24](start_span)[span_24](end_span).

---

## Temporal Billing Trends

•⁠  ⁠*Monthly Billing:* Aggregated ⁠ Billing Amount ⁠ by ⁠ Month ⁠ ordered chronologically (⁠ Jan ⁠–⁠ Dec ⁠) and plotted with ⁠ FuncFormatter ⁠ in millions (⁠ N...M ⁠), with observed monthly totals ranging from roughly ⁠ N107.9M ⁠ (⁠ Feb ⁠) to ⁠ N122.8M ⁠ (⁠ Jul ⁠)[span_25](start_span)[span_25](end_span).
•⁠  ⁠*Yearly Billing:* Aggregated ⁠ Billing Amount ⁠ across ⁠ Year ⁠ (⁠ 2019 ⁠–⁠ 2024 ⁠), showing roughly ⁠ ~1.90e8 ⁠ in ⁠ 2019 ⁠, steady levels around ⁠ ~2.80e8 ⁠ to ⁠ ~2.87e8 ⁠ from ⁠ 2020 ⁠ through ⁠ 2023 ⁠, and ⁠ ~9.78e7 ⁠ in ⁠ 2024 ⁠ (reflecting the dataset's date range)[span_26](start_span)[span_26](end_span).

---

## Getting Started

1.⁠ ⁠*Install required libraries:*
   ```bash
   pip install pandas numpy matplotlib seaborn
