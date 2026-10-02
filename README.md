# Netflix Customer Churn Prediction and Retention Analysis

## Project Overview

This project analyzes customer churn for a Netflix-style streaming platform using customer subscription and engagement data.

The goal is to identify high-risk customer segments, understand the behavioral signals associated with churn, and develop a machine learning model that can predict customers who are likely to leave the platform.

The project combines exploratory data analysis, feature validation, machine learning, model interpretation, and business recommendations.

> **Note:** The dataset is a public synthetic Netflix-style churn dataset used for analytical practice and does not represent Netflix's internal customer data.

---

## Business Questions

This analysis aims to answer the following questions:

- Which customer segments have the highest churn rates?
- How does customer engagement relate to churn?
- Which behavioral signals are most predictive of churn?
- Can machine learning accurately identify customers at risk of leaving?
- Which customers should be prioritized for retention efforts?

---

## Dataset

The dataset contains **5,000 customer records and 14 variables**, including:

- Subscription type
- Watch hours
- Days since last login
- Monthly fee
- Payment method
- Device type
- Region
- Number of profiles
- Average watch time per day
- Favorite genre
- Churn status

The target variable is:

`churned`

- `0` = Retained customer
- `1` = Churned customer

The dataset is approximately balanced between churned and retained customers.

---

## Data Validation

Before modeling, several data-quality and feature-validation checks were performed.

Two variables were excluded from predictive modeling:

- `monthly_fee` was fully determined by `subscription_type`, creating redundant information.
- `avg_watch_time_per_day` was derived from `watch_hours` and `last_login_days` rather than representing an independent behavioral feature.

Customer ID was also excluded because it does not contain predictive business information.

---

## Exploratory Data Analysis

Several meaningful churn patterns were identified.

### Subscription Type

Basic-plan subscribers had the highest churn rate:

| Subscription Type | Churn Rate |
|---|---:|
| Basic | 61.8% |
| Standard | 45.4% |
| Premium | 43.7% |

### Customer Engagement

Churned customers showed substantially lower viewing activity than retained customers.

Average watch hours:

- Retained customers: approximately **17.45 hours**
- Churned customers: approximately **5.92 hours**

### Customer Inactivity

Churned customers also showed much longer periods of inactivity.

Average days since last login:

- Retained customers: approximately **21.8 days**
- Churned customers: approximately **38.3 days**

These findings suggest that declining engagement and prolonged inactivity are important churn warning signals.

---

## Machine Learning

Two classification models were evaluated:

- Logistic Regression
- Random Forest

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Stratified cross-validation

Random Forest consistently outperformed Logistic Regression.

---

## Feature Importance

Permutation importance was used to identify the most useful predictors while reducing potential bias from Random Forest's default impurity-based feature importance.

The strongest predictive signals were:

1. `watch_hours`
2. `last_login_days`
3. `number_of_profiles`
4. `subscription_type`
5. `payment_method`

Variables such as age, gender, region, device, and favorite genre provided little additional predictive information.

---

## Reduced Model

A reduced Random Forest model was developed using only five predictors:

- Watch hours
- Days since last login
- Number of profiles
- Subscription type
- Payment method

Removing low-value features simplified the model while maintaining strong predictive performance.

---

## Final Model Performance

The final reduced Random Forest model achieved approximately:

| Metric | Result |
|---|---:|
| Accuracy | **99.0%** |
| ROC-AUC | **0.9997** |
| Churn Recall | **~98.6%** |

On the held-out test set, the model correctly identified **496 of 503 churned customers**, with only 7 false negatives.

Because the dataset is synthetic, these results should be interpreted as performance within this analytical case study rather than expected performance on real Netflix customer data.

---

## Business Recommendations

### 1. Detect declining engagement early

Watch hours and days since last login were the strongest churn predictors.

A retention system could flag customers showing:

- Declining viewing activity
- Long periods without logging in
- Multiple churn-risk indicators

These customers could receive personalized content recommendations or re-engagement campaigns.

### 2. Monitor Basic-plan subscribers

Basic subscribers showed substantially higher churn than Standard and Premium subscribers.

Retention strategies could test targeted engagement campaigns, personalized recommendations, or upgrade incentives for this segment.

### 3. Encourage household engagement

Accounts with more profiles showed lower churn rates.

Features that encourage broader household usage and profile creation may be useful areas for further experimentation.

### 4. Use payment method as a secondary signal

Payment method contributed some predictive information but was substantially less important than behavioral engagement.

It should therefore be used as a secondary segmentation feature rather than a primary churn indicator.

---

## Key Takeaway

**Customer engagement was substantially more informative than demographic characteristics in predicting churn.**

The strongest warning signals were lower viewing activity and prolonged inactivity, suggesting that proactive retention strategies should focus on identifying customers whose engagement begins to decline.

---

## Limitations

- The dataset is synthetic and does not represent Netflix's actual customer base.
- Predictive relationships should not be interpreted as causal effects.
- The dataset does not contain longitudinal subscription histories, signup dates, or cancellation dates.
- Rigorous cohort and survival analysis cannot be performed without true time-to-event data.
- Real-world churn may also depend on factors not included in this dataset, such as content availability, promotions, pricing changes, customer service interactions, and competitor behavior.
- The exceptionally high model performance may partially reflect the stronger and cleaner patterns present in synthetic data.

---

## Tools & Technologies

- Python
- pandas
- NumPy
- Matplotlib
- scikit-learn
- Jupyter Notebook

---

## Repository Structure

```text
netflix-customer-churn-analysis/
│
├── README.md
├── netflix_churn_analysis.ipynb
├── netflix_customer_churn.csv
├── requirements.txt
│
└── images/
    ├── churn_by_subscription.png
    ├── watch_hours_vs_churn.png
    ├── last_login_days_vs_churn.png
    ├── feature_importance.png
    └── permutation_importance.png
