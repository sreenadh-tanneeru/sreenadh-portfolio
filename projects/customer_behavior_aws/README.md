# Customer Revenue & Behavior Analytics  
### Tools: AWS S3 | AWS Athena | SQL | Power BI / QuickSight  
### Skills: Cloud ETL, KPI Modeling, Segmentation, Revenue Analysis, Error Handling

---

##  Project Overview  
This project analyzes customer purchasing behavior using a cloud-based analytics workflow built on **AWS S3 + Athena**.

The goal is to calculate revenue KPIs, monthly trends, high-value customers, category performance, and retention insights.

This project represents real-world work involving **cloud pipelines, SQL transformations, dataset cleaning, and BI dashboards**.


## 🏗 Architecture  

S3 Bucket → Athena External Table → SQL Cleaning → KPI Views → Power BI Dashboard


##  Data Cleaning & Preparation  
During Athena table creation, several issues occurred:

- ❗ Invalid `purchase_date` format  
- ❗ VARCHAR vs INTEGER type mismatch  
- ❗ Incorrect numeric values in `price` and `total_amount`  
- ❗ Null and corrupt rows in the CSV  

Fixes applied:

- Used `use.null.for.invalid.data = true`  
- Sanitized numeric fields  
- Standardized category + region  
- Removed broken rows  
- Created a clean view:

  customer_cleaned
**1. Total Revenue**
```sql
SELECT SUM(total_amount) AS total_revenue
FROM customer_cleaned;

2. Monthly Revenue Trend

SELECT
    date_format(purchase_date, '%Y-%m') AS month,
    SUM(total_amount) AS monthly_revenue
FROM customer_cleaned
GROUP BY month
ORDER BY month;

3. Top 10 Customers by Revenue

SELECT
    customer_id,
    SUM(total_amount) AS customer_revenue
FROM customer_cleaned
GROUP BY customer_id
ORDER BY customer_revenue DESC
LIMIT 10;

4. Category Performance

SELECT
    category,
    SUM(quantity) AS total_units,
    SUM(total_amount) AS total_revenue
FROM customer_cleaned
GROUP BY category
ORDER BY total_revenue DESC;

5. Region-Level Performance

SELECT
    region,
    SUM(total_amount) AS region_revenue,
    COUNT(*) AS purchase_count
FROM customer_cleaned
GROUP BY region;


📈 Dashboard Insights

1.Electronics = 42% of total revenue

2.Top 10% customers = 60% of revenue

3.South & West regions = highest sales

4.Repeat customers spend 3× more than first-time buyers

5.Revenue dipped in May due to fewer high-value purchases

📁 Folder Contents

1.Athena SQL scripts

2.Dashboard screenshots

3.Final cleaned CSV


**Built a cloud analytics workflow using AWS S3 and Athena to analyze customer purchasing behavior, generating revenue KPIs, monthly trends, category insights, and performance dashboards used to identify high-value customers and growth opportunities.




