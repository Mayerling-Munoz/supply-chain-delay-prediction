# Supply Chain Delay Prediction
### Predictive Analysis of Logistics Delivery Delays using Python and Machine Learning

---

## Project Overview

This project analyzes order delivery data from an international distribution company to identify patterns in late deliveries and build a classification model to predict delay risk.

The dataset covers **2,000 orders** across **5 geographic regions** and **5 carriers** over the period 2022–2024, and includes realistic data quality issues such as null values, inconsistent formatting, and data entry errors — simulating real-world operational data.

---

## Business Problem

1 in 4 orders arrives late. By the time the company is aware of a delay, the customer is already waiting and the operational cost has already occurred. The goal of this project is to anticipate which orders are at risk **before** the delay happens.

---

## Project Structure

```
supply-chain-delay-prediction/
│
├── Avance2.ipynb        # Main analysis notebook
├── orders.csv           # 2,000 order records (main table)
├── customers.csv        # 100 B2B customers across 5 regions
├── products.csv         # 50 products across 6 categories
└── carriers.csv         # 5 carriers with transport mode and cost data
```

---

## Methodology

The analysis follows a structured 4-step data science workflow:

**Step 1 — Exploratory Data Analysis (EDA)**
- Null value distribution by column
- Unique value inspection to detect inconsistencies in categorical fields
- Delay distribution and relationship with key variables (carrier, region, product category)

**Step 2 — Data Cleaning and Feature Engineering**
- Standardization of categorical fields with multiple spelling variations (e.g., `delivered`, `DELIVERED`, `Deliverd` → `Delivered`)
- Null imputation: median for numeric fields, mode for categorical fields, row removal when status was missing
- New features derived from dates: lead time in days, order month, day of week
- Label encoding for categorical variables

**Step 3 — Predictive Modeling**
- Binary classification target: `late_delivery` (1 = late, 0 = on time)
- Cancelled orders excluded from model training
- 80/20 train-test split with stratification
- Two models trained and compared: Logistic Regression (baseline) and Random Forest

**Step 4 — Evaluation and Business Insights**
- Metrics: Precision, Recall, F1-Score, AUC-ROC
- Confusion matrices for both models
- Feature importance analysis (Random Forest)
- Delay rate by carrier and by geographic region

---

## Key Findings

| Finding | Detail |
|---|---|
| Late delivery rate | 25% of non-cancelled orders arrived late |
| Highest-risk region | South America (29.3% late delivery rate) |
| Highest-risk carrier | AirExpress (27.0% — despite being air transport) |
| Geography vs. carrier impact | Region gap: 7 points vs. carrier gap: 4 points |
| Top predictive variables | Order amount (24.7%), quantity (22.5%), product weight (17.9%) |

---

## Tools and Libraries

![Python](https://img.shields.io/badge/Python-3.10-blue)
![pandas](https://img.shields.io/badge/pandas-2.0-lightblue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3-orange)
![matplotlib](https://img.shields.io/badge/matplotlib-3.7-green)
![seaborn](https://img.shields.io/badge/seaborn-0.12-teal)

- **Data manipulation:** pandas
- **Visualization:** matplotlib, seaborn
- **Machine Learning:** scikit-learn (LogisticRegression, RandomForestClassifier)
- **Evaluation:** classification_report, ROC curve, confusion matrix

---

## How to Run

1. Clone this repository
```bash
git clone https://github.com/Mayerling-Munoz/supply-chain-delay-prediction.git
```

2. Install dependencies
```bash
pip install pandas matplotlib seaborn scikit-learn
```

3. Open the notebook
```bash
jupyter notebook Avance2.ipynb
```

> Make sure the four CSV files are in the same directory as the notebook.

---

## About

This project was developed as the final project for the Machine Learning course at **Universidad Politécnica Internacional (UPI)**, as part of a Data Analysis Technician degree program.

*Mayerling Munoz — Data Analysis | Business Intelligence | Operations*  
[LinkedIn](https://www.linkedin.com/in/mayerling-munoz)
