# 🛸 UFO Sightings Data Pipeline & Power BI Dashboard

An end-to-end data analysis project featuring Python ETL data cleaning and an interactive Power BI dashboard exploring global UFO sighting trends, duration patterns, and geographic distributions.

---

## 📌 Project Overview
This project processes, cleans, and analyzes a historical dataset of over 80,000 UFO sightings. Using **Python (Pandas)** for data wrangling and **Power BI** for interactive data visualization, this project transforms messy, unstandardized raw report logs into a dynamic dashboard for spatio-temporal analysis.

### 🛠️ Tech Stack & Tools
* **Data Cleaning & ETL:** Python (`pandas`, `numpy`)
* **Data Visualization:** Power BI Desktop (DAX, Interactive Slicers)
* **Documentation & Version Control:** Markdown, Git, GitHub

---

## 📊 Dashboard Preview



| Overview Page | 
| :---: | 
<img width="1396" height="784" alt="Screenshot 2026-07-26 231623" src="https://github.com/user-attachments/assets/fd6be49c-140f-4d63-8df2-81ef1fcb37db" /> 



---

## 🧹 Data Cleaning & ETL Pipeline Highlights

The raw dataset (`ufo_sighting_data.csv`) contained several anomalies, missing values, and formatting issues that required automated cleaning using Python (`scripts/data_cleaning.py`):

1. **Timestamp Fixing (`Date_time`):** 
   * Replaced non-standard `24:00` midnight entries with `00:00`.
   * Parsed strings into standard `datetime64` objects and extracted `Year`, `Month_Name`, `Day_Name`, and `Hour` features for dashboard slicing.
2. **Coordinate & Numeric Standardization:**
   * Cleaned corrupted non-numeric text strings from `latitude` (e.g., `33q.200088`).
   * Converted `length_of_encounter_seconds` to numeric float and replaced non-positive durations with `NaN`.
3. **Smart Missing Value Imputation:**
   * Handled `NaN` values in `country` and `state/province` by converting them to `'UNKNOWN'`.
   * Implemented smart location logic: if a state/province code was known (e.g., `'CA'`), the country was inferred (`'US'` or `'CA'`).
   * Grouped missing or generic `UFO_shape` values into `'Unspecified'`.
4. **Column Pruning & Deduplication:**
   * Dropped unneeded text columns (`city`, `described_duration_of_encounter`, `description`, `date_documented`).
   * Removed exact duplicate sighting reports.

---

## 📈 Key Insights & Dashboard Features

* **Geographic Distribution:** Over 80% of reported sightings originate from North America, with California, Texas, and Washington leading in report volume.
* **Peak Sighting Times:** Sighting reports peak during evening hours (8:00 PM – 11:00 PM) and increase significantly during summer months (July–August).
* **Most Common Shapes:** Light, Circle, and Triangle are consistently the top reported UFO shapes across all decades.

---

## 📂 Project Structure

```text
ufo-sightings-powerbi-dashboard/
│
├── data/
│   ├── raw/
│   │   └── ufo_sighting_data.csv          # Raw dataset
│   └── processed/
│       └── ufo_sighting_data_cleaned.csv  # Output from Python ETL
│
├── scripts/
│   └── data_cleaning.py                   # Automated Python cleaning pipeline
│
├── reports/
│   ├── ufo_sightings_dashboard.pbix       # Power BI report file
│   └── dashboard_screenshots/             # Visual previews for GitHub
│
├── .gitignore
├── requirements.txt
└── README.md
