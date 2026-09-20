# Supply Chain Delivery Risk & Predictive Analytics

An end-to-end predictive modeling project designed to identify and classify e-commerce delivery delay risks (`late_delivery_risk`) prior to order fulfillment, supporting proactive logistics planning.

---

## Executive Summary

Late deliveries directly impact customer satisfaction, retention, and operational overhead. This project builds a machine learning classification pipeline on international e-commerce transaction data to forecast shipment delays before dispatch, enabling supply chain managers to intervene early.

* **Target Variable:** `late_delivery_risk` (Binary Classification: On-Time / Early vs. Late Delivery)
* **Dataset Scope:** 15,900+ verified transaction records across global geographic markets.
* **Champion Model:** Random Forest Classifier achieving **68.75% Accuracy** and an **81.88% Precision** on late delivery detection.

---

## Technical Pipeline & Methodology

### 1. Data Cleaning & Leakage Prevention
* **Leakage Elimination:** Removed post-fulfillment variables (such as `days_for_shipping_real` and explicit status tags) that artificially inflate model performance in training.
* **Integrity Audits:** Validated data boundaries using Interquartile Range (IQR) checks, ensuring strict non-negative constraints on financial and temporal features.
* **Dimensionality Reduction:** Dropped high-cardinality PII identifiers (names, emails, street details) and attributes with over 50% missingness.

### 2. Feature Engineering & Preparation
* **Temporal Extraction:** Generated operational timestamps, including order hour and dispatch day of the week, to capture peak demand fluctuations.
* **Curated Feature Space:** Standardized 16 business drivers encompassing pricing, order quantities, shipping modes, customer segments, and regional markets.
* **Class Balance:** Implemented a stratified 80/20 train-test split to preserve natural target class distribution.

---

## Exploratory Data Analysis (EDA)

![EDA Insights](eda_analysis.png)

* **Shipping Modes:** Substantial discrepancy in late fulfillment ratios across delivery service tiers.
* **Scheduled Timeframes:** Compressed scheduled shipping windows correlate with higher incident rates.
* **Market Exposure:** Regional demand corridors exhibit varying baseline risks, emphasizing localized carrier oversight.

---

## Model Evaluation & Performance Benchmark

Three supervised algorithms were trained and benchmarked against standard classification metrics:

| Model | Accuracy (%) | Precision (%) | Recall (%) | F1-Score (%) |
| :--- | :---: | :---: | :---: | :---: |
| **Random Forest** | **68.75%** | **81.88%** | **51.45%** | **63.19%** |
| **Decision Tree** | 67.40% | 77.62% | 52.65% | 62.74% |
| **Logistic Regression** | 67.78% | 80.31% | 50.60% | 62.08% |

---

## Champion Model Diagnostics

![Model Evaluation](model_evaluation.png)

### Key Model Takeaways:
* **High Precision Priority:** The Random Forest model achieved an **81.88% precision** on delayed orders, minimizing false alarms and ensuring targeted operational interventions.
* **Primary Operational Drivers:** Feature importance analysis reveals that **Shipping Mode**, **Scheduled Shipping Days**, and **Sales per Customer** are the leading determinants of supply chain punctuality.

---

## Business Impact & Recommendations

1. **Carrier Optimization:** Re-evaluate Service Level Agreements (SLAs) with logistics partners handling high-risk delivery modes.
2. **Buffer Scheduling:** Dynamically adjust automated delivery estimations for constrained regional routes to align customer expectations.
3. **Automated Risk Flags:** Integrate model inference into order management systems to alert fulfillment teams to high-risk transactions instantly.

---

## Tools & Libraries Used
* **Language:** Python
* **Data Processing:** Pandas, NumPy
* **Machine Learning:** Scikit-learn
* **Visualization:** Matplotlib, Seaborn
