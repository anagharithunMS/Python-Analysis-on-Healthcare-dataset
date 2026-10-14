# Healthcare Patient Admissions and Billing Analysis

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)
![Status](https://img.shields.io/badge/Status-Complete-green)

An end-to-end data analytics project in Python that cleans a messy healthcare admissions dataset, explores it, and tests whether cost and length of stay are driven by condition, age, insurer or admission type.

## Project Overview

Hospitals record who was admitted, what for, who treated them, what was billed and how the tests turned out. This project takes a raw file of about 55,000 patient admissions with real-world data problems and turns it into a clean, analysis-ready dataset. It then answers one question honestly: what actually influences hospital cost and length of stay?

## Objectives

- Audit and clean a messy dataset (missing values, duplicates, mixed formats, inconsistent labels, impossible values)
- Explore admissions by medical condition, admission type and insurance provider
- Compare billing and length of stay across patient groups
- Test whether the differences seen are larger than chance
- Present the findings in charts, written insights and a one-page summary

## Dataset

| | |
|---|---|
| **File** | `healthcare_dataset.csv` |
| **Raw size** | 55,750 rows, 15 columns |
| **Cleaned size** | 54,844 rows, 19 columns |
| **Period** | May 2019 to May 2024 |

Each row is one patient admission. Columns: Name, Age, Gender, Blood Type, Medical Condition, Date of Admission, Doctor, Hospital, Insurance Provider, Billing Amount, Room Number, Admission Type, Discharge Date, Medication, Test Results.

The file contains data-quality problems that were added on purpose for cleaning practice: missing values, duplicate rows, four different date layouts, inconsistent labels and casing, extra spaces, text typed into numeric columns, and impossible ages and bills.

## Workflow

| Phase | What happens |
|---|---|
| 1. Introduction | Overview, objective, column dictionary |
| 2. Loading and inspection | Import, data types, numeric and date conversion |
| 3. Data quality audit | Every problem measured before anything is changed |
| 4. Data cleaning | Standardise, de-duplicate, correct, fill, validate, export |
| 5. Exploration | Distributions, correlations, group summaries |
| 6. Wrangling | Engineered features, lookup merge, cross-tabulations |
| 7. Statistics | Mean, median, mode, spread, percentiles |
| 8. Visualization | Nine charts (Matplotlib, Seaborn, Plotly) |
| 9. Insights | Significance tests, findings, recommendations, summary |

## Key Cleaning Decisions

- **Dates:** four layouts are parsed with their own explicit formats. A single day-first rule misreads the month-first dates and creates thousands of negative stays.
- **Duplicates:** text is standardised first, so case-variant copies are caught. Duplicates are checked a second time after filling gaps.
- **Impossible values:** ages outside 1 to 110 and bills outside 0 to 100,000 become missing, then are filled with the median.
- **Categorical gaps:** labelled `Unknown` instead of the most common value, which would invent data.
- **Engineered features:** Length of Stay, Age Group, Billing Category, Cost Per Day.

## Key Findings

- The average bill is about 25,600 and varies by only 2.1% across conditions and 0.9% across insurers.
- Age has no meaningful relationship with billing or length of stay (correlation close to 0).
- Length of stay is 1 to 30 days (mean 15.5) and the same across admission types and conditions.
- Admissions are steady at about 914 a month, split evenly across Elective, Urgent and Emergency.
- Test results (Abnormal, Normal, Inconclusive) each hold about one third.
- All 8 significance tests (ANOVA and chi-square) gave p-values above 0.05, so no strong drivers of cost or stay length were found.
- Hospital and doctor names are almost all unique, so provider-level ranking is not meaningful.

## Tech Stack

Python, pandas, NumPy, Matplotlib, Seaborn, Plotly, SciPy, Jupyter Notebook

## Project Structure

```
├── Healthcare_Patient_Analysis.ipynb   # full analysis
├── healthcare_dataset_dirty.csv        # raw input data
├── healthcare_dataset_cleaned.csv      # created by the notebook
└── README.md
```

## How to Run

1. Clone the repository
```bash
   git clone https://github.com/[your-username]/[your-repo].git
   cd [your-repo]
```
2. Install the libraries
```bash
   pip install pandas numpy matplotlib seaborn plotly scipy jupyter nbformat
```
3. Open the notebook and run all cells
```bash
   jupyter notebook Healthcare_Patient_Analysis.ipynb
```

## Limitations

- Hospital and doctor names are near-unique, which limits provider-level analysis.
- 1,120 missing discharge dates were rebuilt from a typical 15-day stay, so stay-length results depend partly on that assumption.
- The data is very evenly distributed and looks synthetic, which probably explains why so few patterns appear.

## Author

**Anagha Sivaraman**
Data Analytics project, built with Python and Jupyter.
