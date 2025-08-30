# 🚨 Fraud Transaction Detection <br><br>
**📌 Project Overview**  <br>

This project focuses on building a machine learning model to detect fraudulent financial transactions using a real-world inspired dataset (~6.3M rows, 10+ features). Fraudulent transactions are extremely rare compared to legitimate ones, making this a highly imbalanced classification problem.
The goal is to proactively identify fraud patterns, improve detection rates, and suggest infrastructure-level prevention strategies for financial institutions.

**📂 #Dataset** <br>
Size: 6,362,620 rows × 10 columns <br>
Key Features:
step: Time step (hours)
type: Transaction type (CASH_OUT, TRANSFER, PAYMENT, etc.)
amount: Transaction amount
oldbalanceOrg, newbalanceOrig: Sender’s balances before and after
oldbalanceDest, newbalanceDest: Receiver’s balances before and after
isFraud: Fraud label (target variable)
isFlaggedFraud: Flag raised by existing system
Source: Accredian Business Case Dataset

**⚙️# Methodology**
1. Data Preprocessing
Handled missing values, infinite values, and zero balances with safe replacements.
Removed redundant raw balance columns by engineering more meaningful features.
Addressed class imbalance using class_weight='balanced' during model training.
2. Feature Engineering
Time Features: hour_of_day, day_of_week (derived from step).
Balance Discrepancies: errorBalanceOrig, errorBalanceDest.
Proportional Ratios: amount_to_oldbalance_ratio, balance_change_ratio_orig, balance_change_ratio_dest.
Categorical Encoding: Transaction type (TRANSFER, CASH_OUT critical for fraud).
3. Model Development
Algorithm: Random Forest Classifier (n_estimators=100, class_weight='balanced').
Train/Test Split: Stratified 80/20 split.
Evaluation Metrics:
ROC-AUC
PR-AUC (Average Precision)
Confusion Matrix
Precision, Recall, F1-score
Recall@TopK (operational focus)

**📊 # Results**
ROC-AUC: ~0.99
Fraud concentrated in TRANSFER and CASH_OUT transaction types.
Most fraud transactions occur between 1-8 hours everyday.
Engineered features (balance discrepancies, ratios) were top predictors, confirming domain intuition.

**🔑 # Key Insights**
Fraudulent transactions often leave inconsistencies in balance updates.
Fraudsters tend to drain accounts completely, reflected in high ratio features.
Most fraud flows through TRANSFER → CASH_OUT, consistent with money laundering patterns.
Temporal features add moderate but useful signal (fraud spikes at odd hours).

**🛡️ # Recommendations**
Implement real-time fraud detection with hybrid ML + rules.
Introduce velocity checks and step-up authentication for high-risk transactions.
Monitor model drift and retrain regularly to adapt to evolving fraud strategies.
Use canary rollouts and A/B testing to evaluate new prevention measures before full deployment.

**🚀 How to Run**
Clone this repository
git clone https://github.com/div_d/Financial-Payment-Services-Fraud-Tansactions-dectection-using-ML.git
cd Financial-Payment-Services-Fraud-Tansactions-dectection-using-ML

Install dependencies
pip install -r requirements.txt

Open the notebook and run step by step
jupyter notebook deevyansh-fraudtransactions.ipynb

**🧑‍💻 Author <br>
Deevyansh Dewangan  <br>
B.Tech 2025, IIT Roorkee**
<br><br>
Focus: Machine Learning, Data Science, Financial Modeling
