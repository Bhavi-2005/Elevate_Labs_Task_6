# Elevate_Labs_Task_6
# Task 6: Sales Trend Analysis Using Aggregations

## 📊 Objective
The objective of this task is to analyze monthly revenue and order volume from a sales dataset using SQL aggregation functions. The task focuses on grouping sales data by year and month to uncover trends and performance patterns over time.

## 🧰 Tools Used
- SQLite (via DB Browser for SQLite)
- Excel (for data cleaning and preprocessing)
- SQL

## 📁 Files Included

- `Task_6_Sales_Trend_Analysis_Using_Aggregations.sql`  
  Contains the SQL script used to analyze monthly revenue and order volume using SQLite functions like `strftime()`, `SUM()`, and `COUNT(DISTINCT)`.

- `online_sales.csv`  
  Cleaned dataset used for analysis. The columns in the CSV file are:
  - `order_id` – Unique ID for each order
  - `order_date` – Date of the order (`YYYY-MM-DD` format)
  - `amount` – Total amount (revenue) of the order
  - `product_id` – Product identifier

- `Task_6_screenshort.PNG`  
  Screenshot showing the SQL query execution and result from DB Browser for SQLite.

---

## 📌 SQL Query Overview

```sql
-- Monthly Revenue and Order Volume Analysis
SELECT
    strftime('%Y', order_date) AS year,
    strftime('%m', order_date) AS month,
    SUM(amount) AS total_revenue,
    COUNT(DISTINCT order_id) AS total_orders
FROM
    online_sales
WHERE
    order_date IS NOT NULL AND amount > 0
GROUP BY
    year, month
ORDER BY
    year, month;

📈 Output Summary
-This query returns a table with:
-year – Extracted from order_date
-month – Extracted from order_date
-total_revenue – Sum of amount per month
-total_orders – Count of unique order_id per month

Example:

year	month total_revenue	total_orders
2010	12	   10432.75	       120
2011 	01	   9832.60	       108
2011	02  	 12045.50      	 135

🧠 Key Learnings
How to group data by year and month using strftime() in SQLite.

Usage of aggregate functions like SUM() and COUNT(DISTINCT ...).

Difference between COUNT(*) and COUNT(DISTINCT col).

Importance of cleaning data before importing into SQLite (e.g., date format, removing currency symbols).

Gained confidence in performing time-series revenue analysis using SQL.


