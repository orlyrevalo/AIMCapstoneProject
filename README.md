# 📊 Bank Marketing Subscription Prediction

### Capstone Project – End-to-End Machine Learning Pipeline

## 📌 Project Overview

This capstone project develops a complete **end-to-end machine learning solution** to predict whether a bank client will subscribe to a **term deposit** following a **direct marketing campaign**.

The dataset originates from a **Portuguese banking institution (2008–2010)** and contains:

* **45,211 customer records**
* **16 input features**
* **1 binary target variable (`y`)**
* Severe class imbalance (~11.7% positive class)

The objective is to improve **campaign efficiency**, reduce **operational call costs**, and increase **conversion rate** through predictive modeling.

---

## 🎯 Business Problem

Phone marketing campaigns are:

* Expensive
* Time-consuming
* Low conversion (~11.7%)

Calling unlikely customers wastes resources.

This project reframes the challenge as a **binary classification problem**, where the model:

* Ranks customers by subscription probability
* Optimizes marketing targeting
* Balances precision and recall

### ⚖️ Business Trade-Off

* **False Positives** → Increased operational costs
* **False Negatives** → Lost revenue opportunities

Success is defined by:

* Improved conversion rate
* Reduced unnecessary calls
* Higher campaign ROI

---

## 🧠 Methodology

This project follows a structured **CRISP-DM approach**:

### 1️⃣ Data Understanding & Cleaning

* Verified no explicit missing values
* Handled `"unknown"` categories
* Outlier detection via IQR
* Log transformations to stabilize skewed features
* Engineered features:

  * `balance_signlog`
  * `campaign_log`
  * `pdays_log`
  * `previously_contacted`

---

### 2️⃣ Exploratory Data Analysis (EDA)

* Univariate & bivariate analysis
* Correlation analysis (Spearman)
* Structural redundancy detection
* Identified data leakage risk (`duration`)

---

### 3️⃣ Feature Engineering

* **RobustScaler** for numeric features
* **SMOTENC** for class imbalance
* **One-Hot Encoding** for categoricals
* **PCA (95% variance)** tested

---

### 4️⃣ Model Development

Models evaluated:

* Logistic Regression
* Logistic Regression + PCA
* Decision Tree
* Random Forest
* Naive Bayes
* XGBoost

### 📊 Best Model Performance (After Tuning)

| Model                 | ROC-AUC   | Recall (Class 1) | Precision (Class 1) | F1 (Class 1) |
| --------------------- | --------- | ---------------- | ------------------- | ------------ |
| Logistic (Tuned)      | 0.746     | 0.63             | 0.24                | 0.34         |
| Random Forest (Tuned) | 0.804     | **0.55**         | 0.42                | **0.48**     |
| XGBoost (Tuned)       | **0.810** | 0.25             | **0.67**            | 0.37         |

### 🏆 Model Leadership

* **Best ROC-AUC:** XGBoost (0.810)
* **Best Minority F1:** Random Forest (0.48)
* **Best Minority Precision:** XGBoost (0.67)
* **Best Minority Recall:** Random Forest (0.55)

Final model selection depends on business objective:

* Maximize detection → Random Forest
* Minimize false positives → XGBoost
* Optimize ranking → XGBoost

---

## 🔍 Explainability (SHAP Analysis)

SHAP analysis on tuned XGBoost identified top drivers:

1. Contact type (unknown strongly negative)
2. Previous campaign success (strong positive)
3. Financial flexibility indicators
4. Campaign intensity (fatigue effect)
5. Age (requires fairness monitoring)

---

## ⚖️ Fairness & Bias Audit

Age-based fairness evaluation:

Metrics assessed:

* Demographic Parity Difference
* Equal Opportunity Difference
* False Positive Rate Difference

All fairness gaps ≈ 1% or lower → No material age disparity detected at threshold 0.5.

Mitigation strategies proposed:

* Threshold tuning
* Reweighting
* Feature regularization
* Post-processing calibration

---

## 🏗️ Project Structure

```
AIMCapstoneProject/
│
├── README.md
├── requirements.txt
├── notebooks/
│   └── Orly_Revalo_CapstoneProject.ipynb
│
├── data/
│   └── bank-full.csv
│
├── models/
│   ├── log_best_model_xxxxxxxx_xxxx.pkl
│   ├── rf_best_model_xxxxxxxx_xxxx.pkl
│   └── xgb_best_model_xxxxxxxx_xxxx.pkl
│
├── reports/
│   ├── final_report.pdf
│   ├── business_presentation.pptx
│   └── technical_presentation.pptx
│
└── src/
    ├── preprocessing.py
    └── evaluation.py
```

---

## ⚙️ Installation

```bash
pip install -r requirements.txt
```

---

## ▶️ How to Run

1. Clone the repository
2. Install dependencies
3. Open notebook:

   ```
   notebooks/Orly_Revalo_CapstoneProject.ipynb
   ```
4. Execute cells sequentially

---

## 📈 Key Insights

* Ensemble models outperform linear models
* Random Forest achieves best minority balance
* XGBoost achieves best ranking performance
* PCA provides no benefit
* Campaign history strongly predicts conversion
* Class imbalance significantly impacts model behavior

---

## 🧭 Ethical Reflection

High ROC-AUC does not guarantee fairness.

Responsible deployment requires:

* Ongoing bias monitoring
* Transparent targeting strategy
* Periodic fairness audits
* Business + ethical alignment

---

## 📚 Dataset Reference

Moro, S., Laureano, R., & Cortez, P. (2011).
*Using Data Mining for Bank Direct Marketing: An Application of the CRISP-DM Methodology.*

---

## 👩‍💻 Author

**Orly Revalo**
Capstone Project – Machine Learning
2026

GitHub Repository:
https://github.com/orlyrevalo/AIMCapstoneProject
