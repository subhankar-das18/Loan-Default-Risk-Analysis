# 🏦 Loan Default Risk Analysis 

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

> **Business Question:** Which borrower segments are most likely to default — and what risk factors should the lending team act on immediately?

---   

## 📌 Project Overview

Loan defaults cost financial institutions billions every year. This project simulates a retail lending portfolio and builds a Power BI risk dashboard that helps credit analysts and risk teams identify high-risk borrower segments using credit score, Debt-to-Income (DTI) ratio, and loan characteristics — before approvals are made.

---

## 🎯 Key Business Questions Answered

- What is the overall default rate across the loan portfolio?
- Which credit score bands have the highest default risk?
- How does DTI ratio correlate with default probability?
- Which loan types and purposes carry the most risk?
- What is the total portfolio value at risk?

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| Power BI | Interactive risk dashboard and visualization |
| DAX | Default rate, risk segmentation, portfolio KPIs |
| SQL | Data extraction, cleaning, and aggregation |

---

## 📊 Dashboard Preview

 ![Dashboard Preview](https://github.com/subhankar-das18/Loan-Default-Risk-Analysis/blob/main/Dataset/Screenshot/Screenshot%202026-06-23%20215932.png?raw=true)

---

## 📈 Key DAX Measures

```dax
-- Default Rate %
Default Rate % = 
DIVIDE(
    COUNTROWS(FILTER('Loans', 'Loans'[Status] = "Defaulted")),
    COUNTROWS('Loans'),
    0
) * 100

-- Total Portfolio Value at Risk
Portfolio at Risk = 
SUMX(
    FILTER('Loans', 'Loans'[Status] = "Defaulted"),
    'Loans'[Loan_Amount]
)

-- Average DTI by Risk Segment
Avg DTI = AVERAGE('Loans'[DTI_Ratio])

-- High Risk Borrower Count
High Risk Borrowers = 
COUNTROWS(
    FILTER('Loans', 
        'Loans'[Credit_Score] < 580 && 
        'Loans'[DTI_Ratio] > 0.43
    )
)
```

---

## 💡 Key Insights (What I Found)

- 🔴 Borrowers with **credit scores below 580** defaulted at 4.5x the rate of prime borrowers
- 📊 **DTI ratio above 43%** was the single strongest predictor of default across all loan types
- 🏠 **Personal loans** carried 2x higher default risk than secured home loans
- 💰 Borrowers in the **$25K–$50K loan range** represented 61% of total portfolio default value
- ✅ **Borrowers with 3+ years of credit history** had significantly lower default rates regardless of income

---

## 📂 Repository Structure

```
Loan-Default-Risk-Analysis/
│
├── dashboard/
│   └── loan_risk_dashboard.pbix
│
├── data/
│   └── loan_data.csv
│
├── sql/
│   └── risk_queries.sql
│
└── README.md
```

---

## 🚀 How to Run This Project

1. Clone this repository
2. Open `loan_data.csv` to explore the raw dataset
3. Open `loan_risk_dashboard.pbix` in Power BI Desktop
4. Refresh the data connection if prompted
5. Use slicers to filter by credit score band, DTI range, and loan type

---

## 👤 Author

**Subhankar Das** — Aspiring Data Analyst from Kolkata, India

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/YOUR-LINK)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/subhankar-das18)
