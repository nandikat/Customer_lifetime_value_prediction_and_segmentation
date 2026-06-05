# Customer Lifetime Value Prediction and Segmentation

This project presents an end-to-end machine learning pipeline for predicting Customer Lifetime Value (CLV) and segmenting customers into meaningful behavioral groups[cite: 2]. 

## 📌 Project Overview
* **Objective**: Segment customers based on value and behavior, and predict their future Customer Lifetime Value[cite: 2].
* **Dataset**: The Online Retail II UCI dataset (sourced via Kaggle), which contains 1,067,371 historical online retail transactions from 2009-2011 for a UK-based online retailer[cite: 2].
* **Problem Context**: The system handles a high rate of missing Customer IDs, cancelled transactions, and an extreme right-skew where the vast majority of transactions are compressed near £0[cite: 2].

## 🛠️ Methodology
1. **Data Cleaning**: Dropped rows with null Customer IDs (removing 22.77% of records), removed 34,335 duplicate rows, filtered out 19,494 cancelled transactions (invoices prefixed with 'C'), and excluded line items with negative or zero quantity[cite: 2].
2. **RFM Calculation**: Computed Recency, Frequency, and Monetary (RFM) metrics per customer[cite: 2].
3. **Feature Engineering**: Derived Average Order Value (AOV) and applied a log-scale transformation to the Monetary target variable to mitigate the effects of massive wholesale purchases[cite: 2].
4. **K-Means Clustering**: Segmented the customer base into behavioral groups using $K=4$ based on scaled RFM features[cite: 2].
5. **CLV Prediction**: Trained and evaluated Ridge Regression, Random Forest, and XGBoost regressors[cite: 2].

## 📊 Customer Segmentation
The K-Means algorithm identified four distinct behavioral tiers[cite: 2]:
* **Active Retail Shoppers**: 3,836 customers characterized by moderate recency and frequency[cite: 2].
* **Lost/Dormant Customers**: 2,003 customers characterized by high recency (long since last purchase) and low frequency[cite: 2].
* **Loyal Power Users**: 35 customers characterized by high frequency and consistent spend[cite: 2].
* **Whales (Top Wholesalers)**: 4 customers representing extreme outliers with massive monetary value (over £100,000) and frequency[cite: 2].

## 🚀 Model Evaluation & Results
The models were evaluated using Mean Absolute Error (MAE) and $R^{2}$ score[cite: 2]. XGBoost was selected as the primary model due to its ability to handle complex, non-linear relationships and minimize prediction errors iteratively[cite: 2]. 

| Model | MAE (£) | $R^{2}$ Score |
| :--- | :--- | :--- |
| **XGBoost (Proposed)** | 290.83[cite: 2] | 0.9301[cite: 2] |
| **Random Forest** | 401.79[cite: 2] | 0.862[cite: 2] |
| **Ridge Regression** | 2,152.33[cite: 2] | 0.0917[cite: 2] |

Feature importance analysis revealed that purchase frequency and average order value are the dominant drivers of CLV[cite: 2].
