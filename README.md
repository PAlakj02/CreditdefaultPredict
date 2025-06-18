# Credit Card Behaviour Score Prediction Using Classification and Risk-Based Techniques

##  Objective

This project aims to help **Bank A** identify customers likely to default on their credit card payments in the upcoming month. The model prioritizes reducing false negatives — those undetected defaulters — due to their high financial impact ($10,000–$100,000 each), while also maintaining acceptable precision to avoid mislabeling reliable customers.

---

## 📊 Dataset Overview

- **Training Set:** 25,247 rows, 27 features (with target)
- **Validation Set:** 5,016 rows, 26 features (without target)
- **Target Variable:** `next_month_default` (1 = default, 0 = no default)

### Feature Groups
- **Demographics:** sex, age, education, marriage
- **Financial History:** credit limits, past bills & payments
- **Repayment Behavior:** pay flags, default streaks

---

## 🛠️ Data Preprocessing

- Categorical normalization (e.g., education, marriage)
- Missing value imputation for `age`
- Feature Engineering:
  - `delinquency_streak`
  - `PAY_TO_BILL_ratio`
  - `credit_utilization`
  - `payment_volatility`
- Standardization using `StandardScaler`
- **SMOTE** applied to address class imbalance (originally 81:19)

---

##  Exploratory Data Analysis (EDA)

- Distributions and trends in repayment patterns
- Correlation heatmaps
- Analysis of behavioral traits in defaulting vs non-defaulting users

---

## 🤖 Model Training & Evaluation

### Models Tried:
- Logistic Regression
- Decision Tree
- **XGBoost**
- **LightGBM**  *(Final Model)*

### Key Metric:
- **F2 Score** (β = 2) to favor recall over precision due to business priorities

### Performance Summary (after 5 fold cross-validation) and optimal threshold :

| Model        | F2 Score | Precision | Recall  | AUC-ROC |
|--------------|----------|-----------|---------|---------|
| XGBoost      | 0.8065   | 0.8911    | 0.8050  | 0.9336  |
| LightGBM  | 0.6039   | 0.2716    | 0.8701  | 0.9302  |

---

##  Final Output

- **Model:** `best_model.pkl`
- **Threshold:** `best_threshold.pkl`
- **Submission File:** `submission_22124028.csv`
  - Includes `Customer_ID` and predicted `next_month_default`

---

##  Business Impact

- Enhances proactive risk mitigation
- Enables early warning systems for high-risk accounts
- Supports strategic credit adjustments
- Prevents significant financial losses due to undetected defaulters

---

##  Key Learnings

- SMOTE is effective for addressing severe class imbalance.
- Engineered behavioral features outperform raw demographic features.
- Threshold tuning is critical for aligning with business priorities.
- F2 Score is a more suitable metric for risk-sensitive domains like finance.

---



