# Loan Default Prediction Using LendingClub Data

This project analyzes and predicts loan repayment behavior using a dataset of over 9,500 loans from [LendingClub.com](https://www.lendingclub.com). It includes data cleaning, exploratory data analysis (EDA), model training, and an interactive Tableau dashboard.

---

##  Dataset Overview

- **Source**: LendingClub  
- **Rows**: 9,578  
- **Features**: 14  
- **Target**: `not.fully.paid` (1 = Default, 0 = Paid)

###  Features Dictionary

| Feature             | Description                                              |
|---------------------|----------------------------------------------------------|
| `credit.policy`     | 1 = Meets LendingClub's credit criteria                  |
| `purpose`           | Reason for the loan                                      |
| `int.rate`          | Interest rate (%)                                        |
| `installment`       | Monthly installment                                      |
| `log.annual.inc`    | Log of annual income                                     |
| `dti`               | Debt-to-Income ratio                                     |
| `fico`              | Credit score                                             |
| `days.with.cr.line` | Length of credit history                                 |
| `revol.bal`         | Revolving credit balance                                 |
| `revol.util`        | Utilization ratio                                        |
| `inq.last.6mths`    | Credit inquiries                                         |
| `delinq.2yrs`       | Delinquencies in 2 years                                 |
| `pub.rec`           | Public derogatory records                                |
| `not.fully.paid`    | 1 = Not fully paid (default), 0 = Fully paid             |

---

##  Exploratory Data Analysis (EDA)

### 🔗 Correlation Matrix

- `installment` vs `loan.amnt`: Strong positive (~0.97)  
- `fico` vs `int.rate`: Strong negative correlation  
- `not.fully.paid`: Weak linear correlation → non-linear models preferred

<img width="750" height="750" alt="image" src="https://github.com/user-attachments/assets/868f49d6-49f7-4fb9-9549-408518b931e4" />

---

###  Histograms by Loan Status

| Feature       | Observation                                |
|---------------|--------------------------------------------|
| `int_rate`    | Defaults have higher interest rates        |
| `fico`        | Defaulters have lower FICO scores          |
| `dti`         | Slightly higher for defaulters             |
| `revol_util`  | Higher in defaults                         |

Plot Paths:

<img width="450" height="450" alt="image" src="https://github.com/user-attachments/assets/491be2d7-26ad-4530-abb9-5fe5f9da5d92" />

<img width="450" height="450" alt="image" src="https://github.com/user-attachments/assets/bdbed32f-2809-4032-ac6a-ea1522f75176" />

<img width="450" height="450" alt="image" src="https://github.com/user-attachments/assets/12212ec3-1b2f-4d0f-b7a4-7b8c794fafef" />

<img width="450" height="450" alt="image" src="https://github.com/user-attachments/assets/cf51a66b-05a0-491b-b95c-8ae4ff6916bd" />


---

###  Line Plot: Loan Feature Trends by Purpose

This plot shows feature averages by loan `purpose` (only fully paid loans):

- **Small Business Loans**:
  - Higher installments
  - Longer credit histories
  - Higher balances

- **Credit Card / Debt Consolidation**:
  - More consistent, lower-risk borrower profiles

<img width="750" height="750" alt="image" src="https://github.com/user-attachments/assets/cfb1f62a-3a19-4ffc-bbf8-4923d73a03c1" />

---

##  Model Training & Evaluation

###  Model: Random Forest Classifier

- Captures non-linear relationships  
- `class_weight='balanced'` to address class imbalance  
- Evaluation optimized for **recall** on defaults

| Metric     | Paid (0) | Default (1) |
|------------|----------|-------------|
| Precision  | 0.97     | 0.95        |
| Recall     | 0.95     | 0.98        |
| F1 Score   | 0.96     | 0.96        |
| Support    | 2419     | 2408        |


###  Key Insights

- Business Objective: Prioritize identifying loans that are likely not to be paid back.

- Overall Accuracy of the Model = 96% → Excellent general performance.

- The model achieved a high recall of 0.98 for Class 1 (Not Fully Paid), meaning it successfully catches nearly all high-risk loans.

- Precision of 0.95 ensures that false positives (flagging a good loan as risky) remain low.

- This balance between recall and precision makes the model highly effective for minimizing financial risk while maintaining lending opportunity.

---

##  Interactive Tableau Dashboard

<img width="550" height="550" alt="Dashboard" src="https://github.com/user-attachments/assets/dd851d24-9c41-4a63-9473-9f11e96abe06" />

### Includes:
- KPIs: Total Loans, Default Rate, Avg Installment  
- Histograms by Loan Status  
- Line Charts by Loan Purpose  
- Correlation Matrix (Python-generated)  
- Model Evaluation Panel

---

##  Tools Used

| Tool                      | Purpose                        |
|---------------------------|--------------------------------|
| **Python**                | Data preprocessing & modeling  |
| **pandas / seaborn**      | EDA and static visualizations  |
| **scikit-learn**          | Classification model training  |
| **Tableau**               | Interactive dashboard          |

---

##  Business Implications

- Credit score, interest rate, and revolving utilization are **strong predictors** of loan default  
- **Small business loans** are riskier — even when fully paid, they show elevated indicators  
- **Random Forest** is a robust solution for predicting loan repayment with high accuracy and recall  

---



