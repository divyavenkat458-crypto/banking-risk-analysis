# Banking Customer Risk Analysis

An end-to-end analysis of a retail banking customer dataset — from raw MySQL data through Python-based exploratory data analysis (EDA) to an interactive Power BI dashboard summarizing customer risk, loyalty, and income profiles.

## Project Overview

This project analyzes a banking customer dataset (`banking_case.customer`) to understand customer segments by **loyalty classification, risk weighting, income, nationality, gender, and occupation**, and how these relate to bank deposits, loans, and business lending.

The workflow has two stages:
1. **Data extraction & EDA (Python / Jupyter)** — pulling data from a MySQL database and exploring it with `pandas`, `matplotlib`, and `seaborn`.
2. **Dashboarding (Power BI)** — visualizing the cleaned dataset as an interactive report with slicers for gender, loyalty classification, age group, and nationality.

## Tech Stack

- **Database:** MySQL
- **Data Extraction:** `mysql.connector`, `pandas.read_sql`
- **Analysis:** Python (`pandas`, `matplotlib`, `seaborn`)
- **Visualization / Dashboard:** Power BI
- **Environment:** Jupyter Notebook

## Repository Structure

```
banking-risk-analysis/
├── banking_risk_analysis.ipynb   # Data pull + EDA notebook
├── dashboard_screenshot.png      # Power BI dashboard preview
└── README.md
```

## Data Pipeline (Notebook)

1. Connect to a local MySQL instance and query the `banking_case.customer` table into a DataFrame.
2. Initial checks: `.shape`, `.info()`, `.isnull().sum()`, `.describe()`.
3. **Feature engineering:** bucket `Estimated Income` into an `Income Band` (`Low` / `Med` / `High`) and map `GenderId` to a readable `gender` column.
4. **Categorical profiling:** value counts across `BRId`, `GenderId`, `IAId`, `Income Band`, `Nationality`, `Occupation`, `Fee Structure`, `Loyalty Classification`, and `Amount of Credit Cards`.
5. **Relationship analysis:** cross-tabs of `Loyalty Classification` against gender, income band, and nationality.
6. **Univariate analysis:** count plots of key categorical fields, split by gender and by nationality.
7. **Bivariate analysis:** `Loyalty Classification` vs. `Fee Structure`.
8. **Numerical analysis:** distribution plots (histogram + KDE) for `Estimated Income`, `Superannuation Savings`, and `Credit Card Balance`.

## Dashboard Highlights (Power BI)

**Top-level KPIs**
| Metric | Value |
|---|---|
| Total Customers | 3,000 |
| Sum of Bank Deposits | 2.01 bn |
| Sum of Bank Loans | 1.77 bn |
| Sum of Business Lending | 2.60 bn |
| Average Estimated Income | 171.31K |

**Report visuals**
- Total customers by **Loyalty Classification** (Jade > Silver > Gold > Platinum)
- Sum of Business Lending by **Fee Structure** (High / Mid / Low)
- Total customers by **Risk Weighting**
- Average estimated income by **Age Group** (middle age, senior, young)
- Credit Card Balance by **Loyalty Classification**
- Bank Loans vs. Bank Deposits by **Loyalty Classification**
- Average estimated income by **Occupation** (top roles: Environmental Tech, Software Engineer IV, Desktop Support Technician, General Manager)
- Interactive slicers: **Gender**, **Loyalty Classification**, **Age Group**, **Nationality**

## Key Insights

- Jade-tier customers form the largest loyalty segment and also carry the highest combined bank loans and deposits.
- Business lending is concentrated among customers on a **High** fee structure.
- Estimated income is broadly similar across age groups, with only modest variation between young, middle-age, and senior customers.
- A small number of high-paying occupations (Environmental Tech, Software Engineer IV) stand out in average estimated income.

## How to Reproduce

1. Set up a MySQL database with the `banking_case.customer` table.
2. Update the connection credentials in the notebook (`host`, `username`, `password`, `port`).
3. Run `banking_risk_analysis.ipynb` top to bottom to reproduce the EDA and charts.
4. Open the Power BI file (if included) to explore the interactive dashboard, or refer to `dashboard_screenshot.png` for a static preview.

## Note

> Credentials in the original notebook are hard-coded for local development. Before publishing to GitHub, replace them with environment variables (e.g. via `python-dotenv`) and remove any real passwords from version history.
