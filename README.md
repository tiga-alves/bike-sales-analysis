# Bike Shop Sales Analysis

## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data import from SQL server to Power BI](#data-import-from-sql-server-to-power-bi)
- [Data Cleaning and Preparation using Power Query](#data-cleaning-and-preparation-using-power-query)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Dashboard Preview](#dashboard-preview)
- [Results and Findings](#results-and-findings)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [References](#references)

### Project Overview

This data analysis project aims to provide insights into the sales performance of a bike shop over the years of 2021 and 2022. By analyzing various aspects of the sales data, we seek to identify trends, make data-driven recommendations, and gain a deeper understanding of the company's performance.

### Data Sources

- Sales Data of 2021: The dataset "bike_share_yr_0.csv" contains detailed information about each sale made by the company during 2021.
- Sales Data of 2022: The dataset "bike_share_yr_1.csv" contains detailed information about each sale made by the company during 2022.
- Cost table of 2021 and 2022: The dataset "cost_table.csv" contains the price table and COGS(Cost of Goods) of 2021 and 2022.

### Tools

- SQL Server - Database Creation
  - [Download here](https://www.microsoft.com/pt-br/sql-server/sql-server-downloads)
- PowerBI - Data Cleaning and reports.
  - [Download here](https://www.microsoft.com/pt-br/download/details.aspx?id=58494)

### Data import from SQL server to Power BI

![image](https://github.com/user-attachments/assets/e00106a1-994b-4faf-b574-ce6b95b6186e)


### Data Cleaning and Preparation using Power Query

In the initial data preparation phase, I've performed the following tasks:
1. Data loading and inspection.
2. Handling missing values.
3. Data cleaning and formatting.

### Exploratory Data Analysis

EDA involved exploring the sales data base on below key performance metrics, such as:

- Hourly Revenue Analysis
- Profit and Revenue Trends
- Seasonal Revenue
- Rider Demographics

### Data Analysis

Include some interesting code/features worked with, such as:

- Revenue as being the total amount of money the business earns from its normal business activities, such as sales of goods and services.

- Profit as being the amount of money that remains after all expenses have been deducted from revenue. It represents the financial gain of the business.

```sql
with cte as (
select * from bike_share_yr_0
union all
select * from bike_share_yr_1)

select 
dteday,
season,
a.yr,
weekday,
hr,
rider_type,
riders,
price,
COGS,
riders * price as revenue,
riders * price - COGS * riders as profit
from cte a
left join cost_table b
on a.yr = b.yr
```


### Dashboard Preview

![image](https://github.com/user-attachments/assets/d75e1999-17b0-4fc3-95f1-2805ec39af24)


### Results and Findings

The analysis results are summarized as follows:

![image](https://github.com/user-attachments/assets/077265bd-eda2-4aab-8ce3-21f3f0499a0a)

   
1. The company's sales steadly increased from 2021 to 2022.
2. There was a 25% price increase.
3. Even with a 25% price increase, there was a 64% increase in demand by looking at the total number of riders for 2021 and 2022.


### Recommendations

- Based on the analysis, I recommend the following actions:
  - Invest in marketing and promotions during peak sales seasons to maximize revenue.
  - Conservative increase: An increase in the range of 10-15% could test the market's response without risking a significant loss of customers.
    - If the price in 2022 was $4.99, as 10% increase would make a new price about %5.49.
    - A 15% increase would set the price at aproximately $5.74.

### Limitations

There were no limitations during the project execution.

### References

1. [SQL for Business Intelligence: Turning Data into Insights](https://medium.com/@sqlfundamentals/sql-for-business-intelligence-turning-data-into-insights-c4d7a73d5af7)
2. [SQL Common Table Expression (CTE)](https://hightouch.com/sql-dictionary/sql-common-table-expression-cte)
3. [Stack Overflow](https://stack.com)
