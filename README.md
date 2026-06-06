# Customer Lifetime Value Prediction and Segmentation

This project presents an end-to-end machine learning pipeline for predicting Customer Lifetime Value (CLV) and segmenting customers into meaningful behavioral groups. 

##  Project Overview
* **Objective**: Segment customers based on value and behavior, and predict their future Customer Lifetime Value.

##  Methodology
1. **Data Cleaning**: Dropped rows with null Customer IDs (removing 22.77% of records), removed 34,335 duplicate rows, filtered out 19,494 cancelled transactions (invoices prefixed with 'C'), and excluded line items with negative or zero quantity.
2. **RFM Calculation**: Computed Recency, Frequency, and Monetary (RFM) metrics per customer.
3. **Feature Engineering**: Derived Average Order Value (AOV) and applied a log-scale transformation to the Monetary target variable to mitigate the effects of massive wholesale purchases.
4. **K-Means Clustering**: Segmented the customer base into behavioral groups using $K=4$ based on scaled RFM features.
5. **CLV Prediction**: Trained and evaluated Ridge Regression, Random Forest, and XGBoost regressors.

##  Customer Segmentation
The K-Means algorithm identified four distinct behavioral tiers:
* **Active Retail Shoppers**: 3,836 customers characterized by moderate recency and frequency.
* **Lost/Dormant Customers**: 2,003 customers characterized by high recency (long since last purchase) and low frequency.
* **Loyal Power Users**: 35 customers characterized by high frequency and consistent spend.
* **Whales (Top Wholesalers)**: 4 customers representing extreme outliers with massive monetary value (over £100,000) and frequency.

##  Model Evaluation & Results
The models were evaluated using Mean Absolute Error (MAE) and $R^{2}$ score. XGBoost was selected as the primary model due to its ability to handle complex, non-linear relationships and minimize prediction errors iteratively. 

| Model | MAE (£) | $R^{2}$ Score |
| :--- | :--- | :--- |
| **XGBoost (Proposed)** | 290.83 | 0.9301 |
| **Random Forest** | 401.79 | 0.862 |
| **Ridge Regression** | 2,152.33 | 0.0917 |

Feature importance analysis revealed that purchase frequency and average order value are the dominant drivers of CLV.
