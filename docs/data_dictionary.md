# Data Dictionary  
## Bank Marketing Dataset

---

## Dataset Collection & Justification

The dataset used in this project is the **Bank Marketing Dataset**, publicly available and originally published by Moro et al. (2011). It contains real-world data from direct marketing campaigns conducted by a Portuguese banking institution between May 2008 and November 2010.

The dataset is widely used in machine learning research for classification problems and follows the **CRISP-DM methodology**, making it a high-quality and well-documented source for predictive modeling.

**Reference:**

Moro, S., Laureano, R., & Cortez, P. (2011).  
*Using Data Mining for Bank Direct Marketing: An Application of the CRISP-DM Methodology.*  
European Simulation and Modelling Conference (ESM 2011).

---

## Dataset Overview

- **File:** `bank-full.csv`
- **Number of Instances:** 45,211
- **Input Features:** 16
- **Target Variable:** 1 (binary)

### Objective
Predict whether a client will subscribe to a term deposit.

---

## Target Variable Distribution

| Class | Count | Percentage |
|-------|-------|------------|
| No    | 39,922 | 88.3% |
| Yes   | 5,289  | 11.7% |

The dataset exhibits **strong class imbalance**, which must be considered during modeling and evaluation.

---

## Feature Types

### Numerical Variables
- age  
- balance  
- day  
- duration  
- campaign  
- pdays  
- previous  

### Categorical Variables
- job  
- marital  
- education  
- contact  
- month  
- poutcome  

### Binary Variables
- default  
- housing  
- loan  

### Target Variable
- y (binary: yes/no)

Categorical features require encoding, and numerical features may require scaling during preprocessing.

---

## Missing Values

There are no explicit missing values (NaN). However, some categorical variables contain the value `"unknown"`, representing missing or unavailable information. These will be handled during preprocessing.

---

## Numerical Feature Characteristics

- **Age:** Moderately right-skewed distribution.
- **Balance:** Highly skewed with both positive and negative values; potential outliers.
- **Duration:** Strongly right-skewed; highly predictive but may introduce data leakage if used for pre-call prediction.
- **Campaign / Previous:** Long-tailed distributions.
- **pdays:** Contains `-1` indicating no previous contact.

Certain features (e.g., `balance`, `duration`) may require transformation or robust scaling.

---

# Detailed Variable Dictionary

| Variable Name | Type | Description | Allowed Values |
|--------------|------|------------|----------------|
| age | Integer | Age of the client in years | Numeric |
| job | Categorical | Type of job | admin, unknown, unemployed, management, housemaid, entrepreneur, student, blue-collar, self-employed, retired, technician, services |
| marital | Categorical | Marital status | married, divorced, single |
| education | Categorical | Education level | unknown, secondary, primary, tertiary |
| default | Binary | Has credit in default | yes, no |
| balance | Integer | Average yearly balance in euros | Numeric (may include negative values) |
| housing | Binary | Has housing loan | yes, no |
| loan | Binary | Has personal loan | yes, no |
| contact | Categorical | Contact communication type | unknown, telephone, cellular |
| day | Integer | Last contact day of the month | 1–31 |
| month | Categorical | Last contact month of year | jan, feb, mar, apr, may, jun, jul, aug, sep, oct, nov, dec |
| duration | Integer | Last contact duration in seconds | Numeric (0 and above) |
| campaign | Integer | Number of contacts during current campaign | Numeric (1 and above) |
| pdays | Integer | Days since last contact from previous campaign | -1 (no previous contact) or positive integer |
| previous | Integer | Number of contacts before this campaign | Numeric (0 and above) |
| poutcome | Categorical | Outcome of previous campaign | unknown, other, failure, success |
| y | Binary | Has the client subscribed to a term deposit | yes, no |