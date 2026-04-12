# Loan Default Risk Analysis

A data analytics project that studies **loan default behaviour** across different borrower profiles. Using **SQL, Power BI, and Excel/CSV**, this project analyzes which customer segments are more likely to default and builds an interactive dashboard to support better credit risk decisions.

---

## Project Overview

The objective of this project is to understand patterns behind loan defaults and identify key risk factors such as income level, loan amount, credit-to-income ratio, employment status, and demographics. The dashboard helps credit teams quickly see which applicants are high risk and how defaults are distributed across segments.

---

## Business Problem

Lending institutions need to balance growth with risk. Approving too many risky loans increases default losses, while being too strict reduces revenue and customer acquisition. This project answers questions like:

- Which borrower groups have the highest default rates?
- How do income, loan amount, and EMI-to-income ratio affect default risk?
- Are certain occupations, age groups, or regions more likely to default?
- What profile characteristics are common among good vs. bad borrowers?

---

## Tools & Technologies

- **SQL** — data extraction, joins, aggregations, risk calculations  
- **Power BI** — interactive risk dashboard and visual storytelling  
- **DAX** — measures for default rate, approval rate, and risk scores  
- **Excel / CSV** — data storage and initial cleaning  

---

## Dataset Information

The dataset contains historical loan application records with fields such as:

- `Application_ID`
- `Customer_ID`
- `Age`
- `Gender`
- `Income`
- `Loan_Amount`
- `Tenure`
- `EMI` or `Installment`
- `Credit_to_Income_Ratio`
- `Employment_Type`
- `Marital_Status`
- `Region`
- `Default_Flag` (0 = No Default, 1 = Default)

A detailed description of the dataset columns can be found in `dataset/data_description.md` (add or rename this file if needed).

---

## Folder Structure

```text
loan-default-risk-analysis/
├── README.md
├── dataset/
│   ├── borrower_profiles.csv
│   ├── loan_applications.csv
│   └── data_description.md
├── dashboard/
│   └── Loan_Default_Risk_Dashboard.pbix
├── queries/
│   └── loan_default_analysis.sql
└── screenshots/
    ├── overview.png
    ├── risk_by_segment.png
    ├── income_vs_default.png
    └── region_default_rate.png
```

    [![GitHub Repo stars](https://img.shields.io/github/stars/subhankar-das18/Loan-Default-Risk-Analysis?style=social)](https://github.com/subhankar-das18/Loan-Default-Risk-Analysis)

---

## SQL Analysis

Key SQL analyses performed in this project include:

- Overall default rate across all loans  
- Default rate by income band, age group, and employment type  
- Relationship between `credit_to_income_ratio` and default  
- Default rate by loan amount and tenure  
- Region-wise distribution of good vs. bad loans  

All important queries are stored in `queries/loan_default_analysis.sql`.

---

## Dashboard Features

The Power BI dashboard provides:

- KPI cards for total applications, total approved loans, default rate, and high‑risk share  
- Overview page showing good vs. bad loans and key summary metrics  
- Risk by segment: default rate by income band, age group, employment type, and marital status  
- Income vs. default: charts linking income, EMI burden, and default behaviour  
- Region-wise risk map or bar chart showing where default is more common  
- Slicers to filter by time period, region, employment type, and income band  

---

## Key Insights

Example insights you can refine based on your data:

- Borrowers with **high credit-to-income ratio** show significantly higher default rates.  
- Certain income bands and age groups are more prone to default than others.  
- Self‑employed or unstable employment categories have a higher share of bad loans.  
- Some regions show consistently higher default rates, indicating location-based risk.  

Update these bullets with your real numbers once you review your dashboard.

---

## Business Impact

This analysis and dashboard can help lenders:

- Identify risky applicant profiles before loan approval  
- Design better credit policies and eligibility rules  
- Adjust interest rates or credit limits based on risk level  
- Focus collections efforts on segments with high probability of default  
- Support more transparent, data-driven lending decisions  

---

## Dashboard Screenshots

### Overview
![Overview](screenshots/overview.png)

### Risk by Segment
![Risk by Segment](screenshots/risk_by_segment.png)

### Income vs Default
![Income vs Default](screenshots/income_vs_default.png)

### Region-wise Default Rate
![Region Default Rate](screenshots/region_default_rate.png)

Replace the file names above if your screenshots have different names.

---

## How to Use

1. Download the dataset from the `dataset` folder.  
2. Open the `Loan_Default_Risk_Dashboard.pbix` file from the `dashboard` folder in Power BI Desktop.  
3. If needed, update the data source paths to point to your local CSV files.  
4. Refresh the data and explore the visuals using the available filters.
5. [![GitHub Repo stars](https://img.shields.io/github/stars/subhankar-das18/Loan-Default-Risk-Analysis?style=social)](https://github.com/subhankar-das18/Loan-Default-Risk-Analysis)

---

## Skills Demonstrated

- Data cleaning and preparation for risk modelling  
- SQL joins, aggregations, and calculated fields for risk metrics  
- Building interactive dashboards in Power BI  
- Creating DAX measures for default rate and risk segmentation  
- Communicating credit risk insights to non-technical stakeholders  

---

## Author

**Subhankar Das**  
Aspiring Data Analyst | SQL | Power BI | Risk Analytics

- GitHub: [subhankar-das18](https://github.com/subhankar-das18)  
- LinkedIn: *Add your LinkedIn link here*  

Feedback and suggestions are welcome through issues or pull requests.
