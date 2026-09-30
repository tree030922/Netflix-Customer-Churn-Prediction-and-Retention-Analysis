# Netflix-Customer-Churn-Prediction-and-Retention-Analysis
## Project Description
This project analyzes customer churn behavior for a Netflix-style streaming platform using subscriber demographic, subscription, engagement, and usage data. The goal is to identify the key factors associated with customer churn, determine which customer segments are at higher risk of leaving the platform, and build a predictive model to estimate churn probability.

The analysis includes data cleaning, exploratory data analysis, customer segmentation, and machine learning using Python, pandas, and scikit-learn. Subscriber characteristics such as subscription type, monthly fee, viewing behavior, login activity, device usage, payment method, and profile count are examined to understand their relationship with churn. Multiple classification models are evaluated using metrics such as accuracy, precision, recall, F1-score, and ROC-AUC.

The project ultimately aims to translate model results and behavioral patterns into actionable retention insights, helping a streaming platform identify high-risk customer groups and design more targeted customer engagement and retention strategies.

## Business Questions
1.Which subscription segments have the highest churn rates?
2.How does customer engagement relate to churn?
3.Which behavioral signals are most strongly associated with churn?
4.Can customer churn be predicted using machine learning?
5.Which customer groups should be prioritized for retention efforts?


## Dataset
The analysis uses a publicly available Netflix-style customer churn dataset containing 5,000 customer records and 14 variables.

Key features include:

- Subscription type
- Watch hours
- Days since last login
- Monthly fee
- Payment method
- Device type
- Region
- Number of profiles
- Average watch time per day
- Churn status

This is a public/synthetic dataset used for analytical practice and does not represent Netflix's internal customer data.


## Methodology
1. Data quality checks
2. Exploratory data analysis
3. Customer segmentation
4. Feature engineering
5. Machine learning model development
6. Model evaluation
7. Business insight generation


## Key Findings
- Basic subscribers had the highest churn rate at approximately 61.8%, compared with 45.4% for Standard and 43.7% for Premium users.
- Churned customers had substantially lower average watch hours than retained customers.
- Churned customers had been inactive for significantly longer periods before leaving.
- Crypto and Gift Card payment users showed higher churn rates than Credit Card and Debit Card users.
- Device type and region showed relatively small differences in churn rates.


## Visualizations
