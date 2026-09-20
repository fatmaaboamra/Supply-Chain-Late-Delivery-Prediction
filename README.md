# Supply Chain Delivery Risk & Predictive Analytics

An end-to-end machine learning project designed to identify and classify e-commerce delivery delay risks prior to order fulfillment, supporting proactive logistics and supply chain operations.

[View Full Source Code & Analysis (DataCo_Supply_Chain.ipynb)](./DataCo_Supply_Chain.ipynb)

---

## Executive Summary

Late deliveries directly impact customer satisfaction, retention, and operating margins. This project develops a predictive classification pipeline on international e-commerce transaction data to forecast shipment delays before dispatch, enabling supply chain teams to take corrective operational measures.

* **Target Variable:** `late_delivery_risk` (Binary Classification: On-Time / Early vs. Late Delivery)
* **Dataset Scope:** 15,900+ verified transaction records across global geographic markets.
* **Champion Model:** Random Forest Classifier achieving **68.75% Accuracy** and an **81.88% Precision** on late delivery identification.

---

## Technical Methodology

### 1. Data Cleaning & Leakage Prevention
* **Leakage Elimination:** Excluded post-fulfillment variables (such as actual shipping duration and explicit delivery status flags) that artificially inflate training performance.
* **Integrity Audits:** Evaluated statistical distribution thresholds using Interquartile Range (IQR) checks, ensuring strict non-negative constraints across pricing and scheduling attributes.
* **Dimensionality Reduction:** Removed personally identifiable information (PII) including customer names, addresses, emails, and attributes with excessive missing values.

### 2. Feature Engineering & Preparation
* **Temporal Extraction:** Derived operational indicators, including order hour and dispatch day of the week, to capture temporal order variations.
* **Selected Feature Space:** Standardized 16 business drivers encompassing pricing, order quantities, shipping modes, customer segments, and regional markets.
* **Class Balance:** Implemented a stratified 80/20 train-test split to preserve target class proportions.

---

## Exploratory Data Analysis

![Exploratory Data Analysis](eda_analysis.png)

* **Shipping Modes:** Substantial discrepancy in late fulfillment ratios across delivery service tiers.
* **Scheduled Timeframes:** Compressed scheduled shipping windows correlate with higher incident rates.
* **Market Exposure:** Regional demand corridors exhibit varying baseline risks, emphasizing localized carrier oversight.

---

## Model Evaluation & Performance Benchmark

Three supervised classification algorithms were trained and benchmarked against standard validation metrics:

| Model | Accuracy (%) | Precision (%) | Recall (%) | F1-Score (%) |
| :--- | :---: | :---: | :---: | :---: |
| **Random Forest** | **68.75%** | **81.88%** | **51.45%** | **63.19%** |
| **Decision Tree** | 67.40% | 77.62% | 52.65% | 62.74% |
| **Logistic Regression** | 67.78% | 80.31% | 50.60% | 62.08% |

---

## Champion Model Diagnostics

![Model Evaluation](model_evaluation.png)

### Key Insights:
* **High Precision Focus:** The Random Forest model achieved an **81.88% precision** on delayed orders, minimizing false alarms and ensuring targeted operational interventions.
* **Primary Operational Drivers:** Feature importance analysis indicates that **Shipping Mode**, **Scheduled Shipping Days**, and **Sales per Customer** are the primary determinants of on-time delivery performance.

---

## Business Impact & Recommendations

1. **Carrier Optimization:** Re-evaluate Service Level Agreements (SLAs) with logistics partners handling high-risk delivery modes.
2. **Buffer Scheduling:** Dynamically adjust automated delivery estimations for constrained regional routes to align customer expectations.
3. **Automated Risk Flags:** Integrate model inference into order management systems to alert fulfillment teams to high-risk transactions instantly.

---

## Project Artifacts & Repository Structure

* `DataCo_Supply_Chain.ipynb`: Complete documented Python workflow covering data cleaning, exploratory analysis, modeling, and evaluation.
* `eda_analysis.png`: Visual distribution of risk across shipping tiers and geographic regions.
* `model_evaluation.png`: Normalized confusion matrix and top operational feature importances.
