# Loan Default Risk Analysis

## Project Overview

Analyzed a portfolio of **601 consumer loans** to identify key drivers of loan default and delinquency risk. Built an interactive **Power BI dashboard** with relational data model and DAX-driven insights to support lending underwriting and pricing decisions.

**Key Finding:** Subprime borrowers (credit score <620) with high debt-to-income ratio (>40%) exhibit a **57% default rate**, compared to just **4%** for super-prime borrowers (≥740 credit score) with low DTI (<20%). This **14× difference** highlights the critical importance of credit score and DTI in risk assessment.

---

## Data Model

### Tables
- **borrower_profiles** (500 borrowers)
  - Dimensions: age, state, education level, employment status, years employed
  - Metrics: annual income, credit score, homeownership type, dependents, existing monthly debt

- **loan_applications** (601 loans)
  - Dimensions: loan purpose, term (months), application date
  - Metrics: loan amount, interest rate, monthly payment, DTI ratio
  - Outcomes: loan status (Current, Paid Off, Late, Default), days delinquent, default flag

### Relationship
- One-to-many: borrower_profiles → loan_applications (one borrower may have multiple loans)
- Key: borrower_id

### Calculated Columns
**Borrower Segmentation:**
- `Credit Score Band`: Subprime (<620), Near-prime (620–679), Prime (680–739), Super-prime (≥740)
- `Income Band`: <30K, 30K–50K, 50K–75K, 75K–100K, 100K+
- `Age Band`: <25, 25–34, 35–44, 45–54, 55–64, 65+

**Loan Segmentation:**
- `DTI Band`: <20%, 20–30%, 30–40%, 40–50%, 50%+
- `Loan Amount Band`: <5K, 5K–10K, 10K–20K, 20K–35K, 35K+
- `Interest Rate Band`: <6%, 6–10%, 10–15%, 15%+
- `Loan Status Simple`: Current, Paid Off, Late, Default

---

## Dashboard Pages

### **Page 1: Portfolio Overview**
- **Cards**: Total Loans (601), Default Rate % (24%), Delinquency Rate % (41%), Default Exposure ($3M)
- **Charts**:
  - Loan status distribution (Current: 209, Paid Off: 189, Late: 112, Default: 91)
  - Default rate by loan purpose (Wedding: 28%, Home Improvement: 27%, Vacation: 26%)
  - Default rate by state (geographic heatmap)
- **Slicers**: Year, Loan Purpose, State

### **Page 2: Borrower Risk Profile**
- **Heatmap**: Default rate by Credit Score Band × DTI Band
  - Subprime + 50%+ DTI: **57% default** (highest risk)
  - Super-prime + <20% DTI: **4% default** (lowest risk)
- **Bar Charts**:
  - Default rate by income band (lower income = higher default)
  - Default rate by homeownership (renters: 28%, homeowners: 16%)
  - Default rate by employment type (part-time: 23%, full-time: 20%)
- **Insights**: Credit score and DTI are the strongest predictors of default risk

### **Page 3: Loan Characteristics**
- **Column Charts**:
  - Default rate by loan amount band (smaller loans riskier)
  - Default rate by interest rate band (higher rates = higher defaults, driven by risk-based pricing)
- **Scatter Plot**: DTI ratio vs. Default Rate (bubble size = loan count)
  - Shows clustering at high default rates in 50–150+ DTI range
  - Reveals need for DTI limits in approval policy
- **Detail Table**: Loan-level drill-through (loanid, borrowerid, purpose, amount, DTI, status, default flag)

---

## Key Metrics (DAX Measures)

```dax
Total Loans = COUNTROWS('loan_applications')

Defaulted Loans = CALCULATE(COUNTROWS('loan_applications'), 'loan_applications'[defaulted] = 1)

Default Rate % = DIVIDE([Defaulted Loans], [Total Loans])

Delinquent Loans = CALCULATE(COUNTROWS('loan_applications'), 'loan_applications'[loanstatus] IN {"Late", "Default"})

Delinquency Rate % = DIVIDE([Delinquent Loans], [Total Loans])

Default Exposure = CALCULATE(SUM('loan_applications'[loanamount]), 'loan_applications'[defaulted] = 1)

Average DTI = AVERAGE('loan_applications'[dtiratio])

Average Interest Rate = AVERAGE('loan_applications'[interestrate])

Average Credit Score = AVERAGE('borrower_profiles'[creditscore])

Average Annual Income = AVERAGE('borrower_profiles'[annualincome])

Key Insights & Recommendations
Insight 1: Credit Score is the Strongest Risk Predictor
Subprime borrowers (<620): 46% default rate

Super-prime borrowers (≥740): 13% default rate

Action: Reject applications with credit score <600; require co-signer for 600–650 range.

Insight 2: High DTI + Subprime = Extreme Risk
Subprime + DTI >40%: 57% default rate (14× difference from super-prime + DTI <20%)

Action: Implement hard limit: reject loans where DTI >45% AND credit score <650.

Insight 3: Loan Purpose Matters
Wedding: 28% default rate

Home Improvement: 27% default rate

Auto Loan: 20% default rate

Action: Increase interest rates by 1–2% on Wedding/Vacation loans; tighten approval thresholds.

Insight 4: Renters Are Riskier Than Homeowners
Renters: 28% default rate

Homeowners: 16% default rate

Action: Require additional income documentation for renters; consider loan amount limits.

Tools & Technologies
BI Tool: Power BI Desktop

Data Modeling: DAX (Data Analysis Expressions)

Calculated Columns: 8 engineered dimensions

Measures: 10 KPI calculations

Data Sources: borrower_profiles.csv, loan_applications.csv (601 loans, 500 borrowers)

Files in This Repository
README.md – Project documentation (this file)

borrower_profiles.csv – Borrower demographic and credit data

loan_applications.csv – Loan transaction and status data

screenshots/ – Power BI dashboard screenshots (3 pages)

How to Use This Project
Review the README to understand the business problem and key findings.

Open the Power BI file (if available) to interact with the dashboard:

Page 1: Portfolio overview with KPIs and loan status breakdown

Page 2: Risk segmentation by credit score and DTI (heatmap)

Page 3: Loan characteristics (amount, interest rate, DTI scatter plot)

Use slicers to filter by year, loan purpose, or state.

Drill into the detail table on Page 3 to inspect individual loans.

Reference the DAX measures section to understand metric calculations.

Case Study Summary
Analyzed a portfolio of 601 consumer loans to identify borrower and loan-level drivers of default and delinquency risk. Built a relational data model joining borrower profiles (credit score, income, employment, homeownership) with loan applications (amount, term, interest rate, DTI ratio, payment status). Engineered segmentation dimensions (credit score bands: subprime to super-prime; DTI bands: <20% to 50%+; income and age cohorts) and created 10 DAX measures quantifying portfolio default rate (24%), delinquency rate (41%), and loss exposure ($3M on defaulted loans). Identified high-risk segment: subprime borrowers with DTI >40% exhibit 57% default rate versus 4% for super-prime borrowers with DTI <20%, a 14× difference. Dashboard recommendations: tighten underwriting approval thresholds for subprime + high-DTI applicants, increase pricing on high-risk loan purposes (Wedding, Vacation, Home Improvement), and implement early-warning monitoring for accounts with rising DTI or existing debt burden. Expected impact: potential 40–50% reduction in default losses through selective underwriting tightening.

Future Enhancements
Add time-series analysis to track default rate trends over time.

Implement predictive scoring model (logistic regression) to assign risk scores to new applicants.

Integrate payment behavior (days past due, payment amount variance) as early-warning indicators.

Add geographic cohort analysis by state and regional economic indicators.

Build scenario planning dashboard to model impact of underwriting policy changes.

Contact & Attribution
Data Analyst: [Subhankar Das]
LinkedIn: [https://www.linkedin.com/in/subhankar-das-01a1b6244/]
GitHub: [https://github.com/subhankar-das18]
Project Date: March 2026

