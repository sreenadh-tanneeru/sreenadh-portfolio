# Marketing Campaign ROI & Performance Analytics  
### Tools: SQL | Excel | Power BI  
### Skills: KPI Analysis, Data Cleaning, Aggregations, ROI Modeling, Dashboard Development

##  Project Overview  
This project analyzes marketing campaign performance using SQL to calculate revenue, conversions, ROI, and region-level metrics.

##  Key Questions Answered  
- Which campaign has the highest ROI?  
- Where should marketing increase/decrease spend?  
- Which region converts best?  
- What is the monthly revenue trend?  

##  SQL KPIs 
```sql

### 1. ROI by Campaign

SELECT 
  Campaign_Name,
  SUM(Revenue) AS Total_Revenue,
  SUM(Ad_Spend) AS Total_Spend,
  SUM(Conversions) AS Total_Conversions,
  (SUM(Revenue) - SUM(Ad_Spend)) / SUM(Ad_Spend) AS ROI
FROM clean_campaigns
GROUP BY Campaign_Name
ORDER BY ROI DESC;

2. Region Performance

SELECT
  Region,
  SUM(Revenue) AS Region_Revenue,
  SUM(Conversions) AS Region_Conversions
FROM clean_campaigns
GROUP BY Region;

3. Monthly Trend
SELECT
  DATE_FORMAT(Date, '%Y-%m') AS Month,
  SUM(Revenue) AS Monthly_Revenue
FROM clean_campaigns
GROUP BY Month
ORDER BY Month;

📊 Dashboard Insights

1.Electronics = 42% of total revenue

2.Top 10% customers = 60% revenue

3.South & West regions = highest sales

4.Repeat customers spent 3× more

📁 Folder Contents

1.Athena SQL files

2.Dashboard screenshots

3.Final cleaned CSV

**Analyzed marketing campaign performance using SQL, Excel, and Power BI to calculate ROI, optimize ad spend, and deliver insights that improved marketing efficiency by identifying high-performing campaigns and reducing waste.


