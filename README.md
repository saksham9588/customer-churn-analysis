# Customer Churn Analysis & Prediction

**End-to-End Data Analytics Project | SQL • Python • Statistics • Machine Learning • Power BI**

## Project Overview

Customer churn is a major challenge for subscription-based businesses. Understanding which customers are leaving, identifying patterns associated with churn, and developing potential retention strategies can help businesses make informed decisions.

In this project, I analyzed **7,043 telecom customer records** to investigate customer churn using SQL, Python, statistical analysis, and machine learning.

I also developed a **three-page interactive Power BI dashboard** to communicate findings through business KPIs and customer segmentation.

## Business Objectives

- Calculate the overall customer churn rate.
- Identify customer segments associated with higher churn.
- Investigate relationships between contract type, tenure, payment methods, internet service, and churn.
- Apply statistical testing to evaluate observed relationships.
- Develop and compare churn prediction models.
- Present actionable findings through an interactive Power BI dashboard.

## Tools & Technologies

| Category | Technologies |
|---|---|
| Data Analysis | Python, Pandas, NumPy |
| Database & Querying | SQL, SQLite |
| Visualization | Power BI, Matplotlib, Seaborn |
| Statistics | Chi-Square Tests, Welch's t-test, Cramér's V |
| Machine Learning | Scikit-learn, Logistic Regression, Random Forest, Gradient Boosting |
| Development | Google Colab |

## Dataset

**Source:** IBM Telco Customer Churn dataset

- Customer records: 7,043
- Original columns: 21
- Target variable: `Churn` (Yes / No)
- Key features: Contract, tenure, MonthlyCharges, TotalCharges, PaymentMethod, InternetService, and TechSupport

### Data Cleaning

During data validation, I discovered that `TotalCharges` was stored as a text column.

Further investigation revealed **11 whitespace entries**, all belonging to customers with zero months of tenure.

I converted the column to numeric and replaced these missing values with zero, documenting the assumption that charges had not yet accumulated.

I also checked customer identifiers, categorical values, numerical ranges, and logical consistency across related features.

## Key Business Findings

### 1. Overall Customer Churn

| Metric | Value |
|---|---:|
| Total Customers | 7,043 |
| Churned Customers | 1,869 |
| Retained Customers | 5,174 |
| Overall Churn Rate | 26.54% |

Approximately one in four customers in the dataset had churned.

### 2. Churn by Contract Type

| Contract | Churn Rate |
|---|---:|
| Month-to-month | 42.71% |
| One year | 11.27% |
| Two year | 2.83% |

Month-to-month customers had substantially higher observed churn.

**Business implication:** Investigate why these customers leave and evaluate suitable retention incentives without eliminating flexible contracts.

### 3. Churn by Payment Method

Electronic-check customers had the highest observed churn rate at **45.29%**, compared with lower rates among automatic-payment customers.

This relationship may be influenced by other customer characteristics and should not be interpreted as causal.

### 4. Internet Service & Tenure

Fiber-optic customers had an observed churn rate of **41.89%**, compared with **18.96%** for DSL customers.

Customers with shorter tenure also exhibited substantially higher churn rates, suggesting that early customer retention deserves further investigation.

### 5. High-Churn Customer Segment

Identified a segment consisting of customers with:

- Month-to-month contracts
- Fiber-optic internet
- No technical support subscription

**Results:**

| Metric | Value |
|---|---:|
| Customers in Segment | 1,796 |
| Churned Customers | 1,033 |
| Segment Churn Rate | 57.52% |

This segment accounted for approximately 55.3% of all churned customers, making it a potential priority for further investigation.

## Statistical Analysis

Performed Chi-square tests to investigate associations between churn and categorical customer characteristics.

| Variable | Cramér's V |
|---|---:|
| Contract | 0.4101 |
| Internet Service | 0.3225 |
| Payment Method | 0.3034 |

All three tests provided evidence of statistical associations with churn.

### An Interesting Finding: Simpson's Paradox

Churned customers had higher average monthly charges overall:

- Churned: $74.44
- Retained: $61.27

However, within each internet-service category, churned customers had **lower** average monthly charges than retained customers.

This reversal demonstrates why aggregated statistics can be misleading and highlights the importance of customer segmentation.

## Machine Learning

Developed and compared three classification models using stratified five-fold cross-validation.

| Model | Mean CV F1-score |
|---|---:|
| Logistic Regression | 0.5931 |
| Random Forest | 0.5400 |
| Gradient Boosting | 0.5882 |

Selected a tuned Logistic Regression model for its F1 performance and relative interpretability.

At an exploratory classification threshold of 0.30, the model achieved the following results on the test set:

| Metric |                 Result |
|       ---         |        ---: |
| Accuracy          |      74.80% |
| Precision (Churn) |      51.76% |
| Recall (Churn)    |      74.87% |
| F1-score (Churn)  |      61.20% |
| ROC-AUC           |      0.8409 |

The threshold was selected provisionally to prioritize identifying potentially churned customers in a hypothetical low-cost outreach scenario.

These evaluation results are exploratory, not evidence of production performance.

## Power BI Dashboard

Built a three-page dashboard to
