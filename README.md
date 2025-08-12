# Fraud Detection Case Study

## 📌 Overview
This project was developed as part of an internship application task.  
The goal is to predict fraudulent transactions for a financial company using machine learning,  
and provide actionable business recommendations based on the analysis.

## 📊 Dataset
- **Rows:** 6,362,620
- **Columns:** 10
- **Target Variable:** `isFraud` (1 = Fraudulent, 0 = Non-Fraudulent)
- **Source:** Provided in internship task
- **Description:**  
  The dataset simulates financial transactions, including `step` (time in hours), transaction `type`,  
  `amount`, balances before and after transactions for both sender and recipient, and fraud indicators.

## 🛠️ Project Workflow
1. **Data Cleaning**  
   - Checked for missing values (none found)  
   - Handled outliers carefully to retain possible fraud cases  
   - Checked for multi-collinearity using VIF  

2. **Feature Engineering**  
   - Removed identifiers (`nameOrig`, `nameDest`)  
   - Encoded `type` into dummy variables  

3. **Model Building**  
   - Handled class imbalance using **SMOTE**  
   - Trained a **Random Forest Classifier**  

4. **Model Evaluation**  
   - Metrics: Precision, Recall, F1-score, ROC-AUC  
   - Plots: Confusion Matrix, ROC Curve, Feature Importance  

5. **Business Insights**  
   - Identified the top 10 predictive features for fraud detection  
   - Provided interpretations based on real-world fraud patterns  

6. **Recommendations**  
   - Real-time fraud scoring  
   - Step-up authentication for high-risk transactions  
   - Velocity checks for rapid multiple transactions  
   - Risk scoring for suspicious recipient accounts  
   - Periodic model retraining

## 📈 Model Performance
- **ROC-AUC Score:** ~0.99
- High **Recall** to minimize missed fraud cases  
- Balanced precision to avoid excessive false positives

## 🔍 Top 10 Predictive Features
| Rank | Feature           | Importance |
|------|-------------------|------------|
| 1    | oldbalanceOrg     | 30.16%     |
| 2    | amount            | 16.61%     |
| 3    | newbalanceOrig    | 16.09%     |
| 4    | type_TRANSFER     | 9.97%      |
| 5    | type_CASH_OUT     | 6.03%      |
| 6    | step              | 5.85%      |
| 7    | type_PAYMENT      | 5.59%      |
| 8    | newbalanceDest    | 5.51%      |
| 9    | oldbalanceDest    | 4.15%      |
| 10   | type_DEBIT        | 0.01%      |

## 💡 Recommendations
1. Integrate real-time fraud detection into transaction systems.  
2. Flag high-value and sudden balance-drop transactions for extra verification.  
3. Monitor and block recipient accounts with zero starting balance receiving large credits.  
4. Apply velocity rules for multiple transactions within short time periods.  
5. Retrain the model periodically to capture new fraud trends.

## 🚀 How to Run
```bash
pip install -r requirements.txt
jupyter notebook Fraud_Detection_Case_Study.ipynb
