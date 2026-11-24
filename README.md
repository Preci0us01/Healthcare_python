# Healthcare Admissions, Billing & Length-of-Stay Analysis

An exploratory data analysis (EDA) workflow in Python (⁠ pandas ⁠, ⁠ numpy ⁠, ⁠ matplotlib ⁠, and ⁠ seaborn ⁠) examining patient admission and discharge records, billing totals, care capacity indicators, and temporal billing patterns across ⁠ healthcare_dataset .

---

## Project Overview

This notebook prepares raw hospital admission records for analysis by standardizing text fields, parsing admission and discharge dates, deriving length-of-stay durations, and generating summary KPIs alongside monthly and yearly billing visualizations.

### Dataset Schema

The dataset includes demographic, clinical, operational, and financial columns:

•⁠  ⁠*Patient & Demographics:* Name, Age, Gender ⁠& Blood Type


⁠
•⁠  ⁠*Clinical & Care:* ⁠ Medical Condition, Doctor⁠, Hospital, Medication & Test Results

•⁠  ⁠*Admissions & Facilities:* ⁠ Date of Admission, Discharge Date⁠, Admission Type & Room Number 


⁠
•⁠  ⁠*Billing & Coverage:* ⁠ Insurance Provider ⁠, ⁠ Billing Amount ⁠

---

## Key Metrics 

| Metric | Value | Notes |
| :--- | :--- | :--- |
| *Total Billing Amount* | ⁠ N1.4B | Formatted in billions (⁠ N...B ⁠) in the summary output |
| *Unique Patients* | ⁠ 40.23K ⁠| Calculated via ⁠ .nunique() ⁠ on ⁠ Name |
| *Unique Doctors* | ⁠ 40.34K | Calculated via ⁠ .nunique() ⁠ on ⁠ Doctor|
| *Unique Rooms* | ⁠ 400 ⁠| Calculated via ⁠ .nunique() ⁠ on ⁠ Room Number |
| *Average Patient Age* | ⁠ 52yrs ⁠ | calculated via .mean()  |
| *Total Length of Stay* | ⁠ 860750 days| Sum of ⁠ Length of Stay ⁠ (⁠ Discharge Date - Date of Admission ⁠)|
| *Average Length of Stay* | ⁠ 15yrs | Calculated from the average of Total length of stay .mean() |

---

 ## Data Cleaning & Feature Engineering
 - *Data Conversion & Time Features:* Converted Date of Admission and Discharge Date with ```pd.to_datetime(df['Date of Admission'])``` & ```pd.to_datetime(df['Discharge Date'])``` and extracted the month(three-letter month names e.g; Jan,Feb) and Year(four-digit Year) with ```df['Month'].dt.strftime('%b')``` and ```df['Year'].dt.strftime('%Y')```.
 - *String Normalization:* Applied ```df['Name'].str.strip().str.title()``` to Name to clean extra whitespaces and inconsistent casing(for example Bobby jackSon to Bobby Jackson).
 - *Length of stay:* calculated ```df['Length of Stay'] = df['Discharge Date'] - df['Date of Admission']``` as a timedelta column.
---

## Temporal Billing Trends

- ⁠*Monthly Billing:* Aggregated ⁠ Billing Amount ⁠ by ⁠ Month ⁠ ordered chronologically (⁠ Jan ⁠–⁠ Dec ⁠) and plotted with ⁠ FuncFormatter ⁠ in millions (⁠M), with observed monthly totals ranging from roughly ⁠ N107.9M ⁠ (⁠ Feb ⁠) to ⁠ N122.8M ⁠ (⁠ Jul ⁠).
- ⁠*Yearly Billing:* Aggregated ⁠ Billing Amount ⁠ across ⁠ Year ⁠ (⁠ 2019 ⁠–⁠ 2024 ⁠), showing roughly ⁠ ~1.90e8 ⁠ in ⁠ 2019 ⁠, steady levels around ⁠ ~2.80e8 ⁠ to ⁠ ~2.87e8 ⁠ from ⁠ 2020 ⁠ through ⁠ 2023 ⁠, and ⁠ ~9.78e7 ⁠ in ⁠ 2024 ⁠ (reflecting the dataset's date range).

---

## Getting Started

1.⁠ ⁠*Install required libraries:*
   ```bash
   pip install pandas numpy matplotlib seaborn
