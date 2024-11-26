# SQL and Analytics Insights for Company X

## Project Description

This project is focused on analyzing and enhancing the success of Company X, an online payment platform where customers can pay bills, recharge, transfer money, and more. By leveraging SQL queries and visualization tools, this repository provides solutions for analyzing customer behavior, identifying churn risks, segmenting customers, and ensuring product availability for sustained revenue.

## Analytical Section

### 1. Key Metrics for Success

The top three metrics defining the success of the platform are:
- **Transaction Volume:** Reflects platform usage.
- **Customer Retention Rate:** Indicates the ability to maintain active customers.
- **Revenue Growth:** Measures financial performance over time.

### 2. Predicting Customer Churn

Factors to consider for predicting churn:
- **Activity Level:** Frequency and recency of transactions.
- **Payment Diversity:** Use of multiple products or services.
- **Customer Support Interaction:** Complaints and resolution times.

### 3. Customer Segmentation Methods

- **Behavioral Segmentation:** Based on transaction frequency and type.
- **Demographic Segmentation:** Analyzing age, gender, or location.
- **Monetary Value Segmentation:** High-value vs. low-value customers.

## Technical Queries

### 1. Customers Using Two or More Products

Query to count customers using two or more products:
```sql
SELECT COUNT(DISTINCT customer_id) 
FROM Payment_Table_Final 
WHERE customer_id IN ( 
    SELECT customer_id  
    FROM Payment_Table_Final  
    GROUP BY customer_id  
    HAVING COUNT(DISTINCT payment_type) >= 2 
);

 ### 2. Identifying Churned Customers

Definition: A churned customer is one who has not transacted within the last 90 days. Query to count churned customers:

```sql
SELECT COUNT(DISTINCT customer_id) 
FROM Payment_Table_Final 
WHERE paymentdate < DATEADD(day, -90, GETDATE());


 ### 3. Top 5 Critical Products
Query to identify products critical for sustained revenue:

```sql
SELECT product_id, product_name, COUNT(*) AS total_orders 
FROM Order_Table_Final 
GROUP BY product_id, product_name 
ORDER BY total_orders DESC 
LIMIT 5;
