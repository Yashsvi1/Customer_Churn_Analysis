# Customer Churn Prediction and Analysis

## Project Background
Customer churn is a critical challenge for businesses, impacting revenue and long-term growth. This project aims to analyze churn patterns, predict future churn, and provide actionable insights to enhance customer retention strategies. The analysis combines SQL-based data exploration, predictive modeling using machine learning, and visualization via Power BI.

## Data Overview
The project is based on three key datasets:

1. **Customer Data** (customer demographics, purchase history, and contract details)
2. **Churned Customers Prediction Data** (labeled data for model training and evaluation)
3. **Sales Data** (customer transactions and revenue impact analysis)

### **Dataset Structure:**
- **Customer Data:** Customer ID, Gender, Age, State, Contract Type, Total Purchases, Tenure, Monthly Charges, Payment Method.
- **Churn Prediction Data:** Features such as internet service type, streaming services, online security, and historical transactions.
- **Sales Data:** Order ID, Product, Quantity, Price, Profit, Churn Status.

## Insights & Recommendations

### **Customer Churn Trends**
- **Insight 1:** **At 2,838, customers aged >50 had the highest total customers, which was 2,325.64% higher than customers aged <20, who had the lowest total at 117.**
- **Insight 2:** **Total Customers and Total Churn Rate are positively correlated.**
- **Insight 3:** **Customers aged >50 accounted for 44.22% of Total Customers.**
- **Insight 4:** **Total Customers and Churn Rate diverged the most when the Tenure Group was >=24 months, with Total Customers being 2,087 higher than the Churn Rate.**
- **Insight 5:** **Across all five tenure groups, Total Customers ranged from 980 to 2,087, and Churn Rate ranged from 26.1% to 27.5%.**
- **Recommendation:** Focus on retention strategies for long-tenure customers and older age groups to maintain profitability.

### **Sales and Profitability Analysis**
- **Insight 1:** **Total churn for Female customers (1,111) was higher than Male customers (621).**
- **Insight 2:** **Count of predicted churned customers was highest in Uttar Pradesh (44), followed by Maharashtra and Tamil Nadu.**
- **Insight 3:** **Uttar Pradesh accounted for 11.83% of predicted churned customers.**
- **Insight 4:** **Across all four Age Groups, predicted churned customers ranged from 12 to 132.**
- **Recommendation:** Implement targeted offers and proactive engagement in high-risk states like Uttar Pradesh and Maharashtra.

### **Predictive Model**
- **Machine Learning Model:** Logistic Regression trained on customer behavior data.
- **Accuracy:** 85% on test data.
- **Key Features Influencing Churn:**
  - Tenure (negative correlation with churn)
  - Contract Type (monthly contracts show higher churn)
  - Streaming Services (subscription cancellations increase churn probability)
- **Recommendation:** Use targeted marketing strategies to engage at-risk customers identified by the model.

### **Geographic & Demographic Trends**
- **Insight 1:** Customers from **urban areas** show higher churn rates than suburban areas.
- **Insight 2:** **Age groups 25-40** have the highest churn probability.
- **Recommendation:** Develop location-based retention programs and tailored service plans.

## Data Processing & SQL Analysis
The dataset was preprocessed using SQL for null handling, exploratory data analysis (EDA), and aggregations.

### **Key SQL Queries:**
1. **Customer Distribution Analysis:**
```sql
SELECT Gender, COUNT(Gender) AS TotalCount, COUNT(Gender) * 100.0 / (SELECT COUNT(*) FROM stg_Churn) AS Percentage FROM stg_Churn GROUP BY Gender;
```
2. **Contract Type Influence on Churn:**
```sql
SELECT Contract, COUNT(Contract) AS TotalCount, COUNT(Contract) * 100.0 / (SELECT COUNT(*) FROM stg_Churn) AS Percentage FROM stg_Churn GROUP BY Contract;
```
3. **Revenue Impact of Churn:**
```sql
SELECT Customer_Status, COUNT(Customer_Status) AS TotalCount, SUM(Total_Revenue) AS TotalRev FROM stg_Churn GROUP BY Customer_Status;
```

## Dashboard Summary (Power BI)
The Power BI dashboard provides interactive visualizations for:
- Churn Trends by Contract Type, Tenure, and Monthly Charges.
- Revenue impact analysis.
- Churn likelihood prediction for individual customers.

## Final Recommendations
1. **Retention Strategies:**
   - Focus on **high-value customers** with personalized offers.
   - **Introduce annual contracts** with incentives to lower churn.
2. **Enhanced Customer Experience:**
   - Provide **better onboarding and engagement programs** for new customers.
   - Offer **proactive support for customers canceling streaming services.**
3. **Sales Optimization:**
   - Expand into **low-churn geographic regions.**
   - Introduce **dynamic pricing models** for different customer segments.

## Assumptions & Caveats
- Data for December 2023 was extrapolated using historical trends.
- Missing values were handled using appropriate imputation techniques.
- Model predictions depend on the quality and completeness of input data.

This README serves as a documentation template for stakeholders, ensuring clarity, reproducibility, and actionable insights.

