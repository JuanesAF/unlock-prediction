# 🏦 Predictive Model for Risk-Based Unlocking of International Transfers

This repository presents the development and deployment of a machine learning model designed to assist an international banking entity in **automating the decision-making process for unlocking blocked international transfers**, using historical transactional and customer profile data.

---

## 📌 Project Background

As part of the analytics team within the Risk and Compliance Division, I was assigned to design a predictive solution to reduce manual workload and optimize operational decision-making in the **unlocking of blocked international money transfers**.

The bank blocks certain incoming remittances when the recipient exceeds their predefined transactional quota. These blocked transactions are then manually reviewed by a compliance team, consuming significant time and effort.

---

## 🎯 Objective

The goal of this project was to build a predictive model that could determine, with high reliability, whether a blocked transaction:
- **Should be unlocked** (`0`), or  
- **Should remain blocked for manual review** (`1`).

This automation aims to:
- Reduce manual intervention.
- Speed up the customer experience.
- Maintain compliance with financial regulations on anti-money laundering (AML) and counter-terrorism financing (CTF).

---

## 👨‍💻 My Role

- Led the end-to-end solution: from EDA and data cleaning to model selection and deployment.
- Collaborated with the compliance and risk teams to understand edge cases and legal boundaries.
- Delivered an explainable and reproducible machine learning pipeline integrated into the internal decision-support system.

---

## 🧠 Methodology

### 1. Data Exploration & Understanding
- Dataset contained thousands of blocked transactions over time, with customer demographics, behavioral data, transaction metadata, and risk profile indicators.
- Identified imbalance in target classes (approx. 20% blocked).
- Detected redundant variables and high-cardinality categorical fields.

### 2. Data Cleaning & Preprocessing
- Dropped columns with over 50% missing values.
- Label-encoded categorical variables.
- Imputed remaining null values with domain-justified defaults (e.g., 0 or "unknown").
- Ensured train/test schema alignment.

### 3. Feature Engineering
- Created aggregated features per client (e.g., number of previous blocked operations).
- Engineered risk-category interactions and time-based transaction frequency metrics.

### 4. Model Selection & Optimization
After testing several classifiers (Logistic Regression, RandomForest, etc.), the final model selected was:

> ✅ **LightGBM**, optimized via grid search cross-validation.

Final hyperparameters:
```python
{
  'learning_rate': 0.05,
  'max_depth': 15,
  'min_child_samples': 10,
  'n_estimators': 300,
  'num_leaves': 20,
  'reg_alpha': 0,
  'reg_lambda': 0.1
}
