📈 Loan Default Prediction Using LendingClub Data
This project analyzes and predicts loan repayment behavior using a dataset of over 9,500 loans from LendingClub.com. It includes data cleaning, exploratory data analysis (EDA), model training, and an interactive Tableau dashboard.

📂 Dataset Overview
Source: LendingClub

Rows: 9,578

Features: 14

Target: not_fully_paid (1 = Default, 0 = Paid)

🧾 Features Dictionary
Feature	Description
credit_policy	1 = Meets LendingClub's credit criteria
purpose	Reason for the loan
int_rate	Interest rate (%)
installment	Monthly installment
log_annual_inc	Log of annual income
dti	Debt-to-Income ratio
fico	Credit score
days_with_cr_line	Length of credit history
revol_bal	Revolving credit balance
revol_util	Utilization ratio
inq_last_6mths	Credit inquiries
delinq_2yrs	Delinquencies in 2 years
pub_rec	Public derogatory records
not_fully_paid	1 = Not fully paid (default), 0 = Fully paid

🔍 Exploratory Data Analysis (EDA)
🔗 Correlation Matrix

Installment vs Loan Amount: Strong positive (~0.97)

FICO vs Interest Rate: Strong negative

Not Fully Paid: Weak linear correlation with any one feature → Use non-linear models

📊 Histograms by Loan Status
Below are sample histograms comparing feature distributions by not_fully_paid:

Feature	Observation
int_rate	Defaults have higher interest rates
fico	Defaulters have lower FICO scores
dti	Slightly higher for defaulters
revol_util	Higher in defaults

📁 Plots:

plots/fico_histogram.png

plots/int_rate_histogram.png

plots/dti_histogram.png

plots/revol_util_histogram.png

📈 Line Plot: Loan Feature Trends by Purpose

Small Business Loans:

Higher installments

Longer credit histories

Higher balances

Credit Card / Debt Consolidation:

More consistent, lower-risk profiles

🤖 Model Training & Evaluation
✅ Model: Random Forest Classifier
Handles non-linear relationships

Balanced class weights to handle class imbalance

Evaluation prioritized Recall for defaults

Metric	Paid (0)	Default (1)
Precision	0.97	0.95
Recall	0.95	0.98
F1 Score	0.96	0.96
Support	2419	2408

📌 Confusion Matrix

🎯 Key Insights
96% overall accuracy

High recall for defaulters (0.98) ensures few missed risks

Aligns with business priority: “Better to catch defaulters than miss them”

📊 Interactive Tableau Dashboard
🔗 View Dashboard on Tableau Public

Replace with actual link after publishing.

Includes:
KPIs: Total Loans, Default Rate, Avg Installment

Histograms by Loan Status

Line Charts by Purpose

Correlation Matrix (imported from Python)

Model Evaluation Panel

🛠️ Tools Used
Tool	Purpose
Python	Data cleaning, modeling, EDA
pandas / matplotlib / seaborn	Visualization
scikit-learn	Classification modeling
Tableau	Interactive dashboard

🧠 Business Implications
Credit score, interest rate, and revolving utilization are strong predictors of loan default

Small business loans are riskier—even when fully paid, they show elevated risk metrics

Machine learning models like Random Forest provide robust default prediction

📁 Folder Structure
php
Copy
Edit
loan-default-prediction/
│
├── data/
│   └── loan_data.csv
│
├── plots/
│   ├── correlation_heatmap.png
│   ├── fico_histogram.png
│   ├── int_rate_histogram.png
│   ├── revol_util_histogram.png
│   ├── loan_purpose_trend.png
│   └── confusion_matrix.png
│
├── dashboard/
│   └── dashboard.twbx   # Exported Tableau Workbook (optional)
│
├── model/
│   └── loan_model.pkl   # Trained model (optional)
│
├── README.md
└── main.ipynb           # Notebook with all code
