# Retail Sales Analysis (SQL Project)

##  Project Overview

This project focuses on analyzing retail sales data to uncover insights related to sales performance, customer behavior, revenue trends, and profitability. The analysis includes data cleaning, exploratory data analysis (EDA), profitability analysis, and answering real-world business questions using SQL.

---

## Problem Statement

Retail businesses generate large volumes of transactional data daily, but raw data alone does not provide actionable insights. Without proper cleaning, structuring, and analysis, it becomes difficult to understand customer behavior, identify top-performing products, track revenue trends, and measure profitability.

The challenge is to transform raw retail sales data into meaningful insights that can support data-driven decision-making, such as improving sales performance, optimizing inventory, and understanding customer purchasing patterns.

---
##  Steps performed 
##  (1) Data Cleaning

Since the dataset is imported from a CSV file, data types of all columns are finalized to avoid further complications during analysis.

### 1. Column Renaming

* Renamed 2 columns for better clarity and consistency

### 2. Data Type Standardization

* IDs & Numbers
* Dates & Time
* Text Columns
* Monetary Columns

---

## (2) Exploratory Data Analysis (EDA)

### 1. Overview of Data

* Understanding data structure and basic information

### 2. Data Quality Checks

* Checking uniqueness
* Checking null values
* Checking duplicate records

### 3. Descriptive Statistics

* Minimum values
* Maximum values
* Average values

### 4. Categorical Distribution

* Sales by category
* Gender distribution

### 5. Revenue Analysis

* Total revenue
* Revenue by category
* Revenue by gender

### 6. Time-Based EDA

* Daily sales
* Monthly sales
* Peak sales hours

### 7. Customer-Level EDA

* Top customers
* Average sales per customer

## 8. Profitability Analysis

* Profit per transaction
* Profit by category
* Profit by gender

## 9. Outlier Detection

* Identification of very high sales values

---

##  (3) Answering Business Questions

**Q1.** Retrieve all columns for sales made on 2022-11-05
```sql
SELECT *
FROM retail_sales
WHERE sale_date = '2022-11-05';

```

**Q2.** Write a SQL query to retrieve all transactions where the category is 'Clothing' and the quantity sold is more than 4 in the month of Nov-2022.
```sql
SELECT *
FROM retail_sales
WHERE category = 'Clothing'
  AND quantity > 4
  AND MONTH(sale_date) = 11
  AND YEAR(sale_date) = 2022;
```

**Q3.** Calculate total sales for each category
```sql
SELECT category,
       SUM(total_sale) AS total_sales
FROM retail_sales
GROUP BY category;
```

**Q4.** Find the average age of customers who purchased items from the *Beauty* category
```sql
SELECT AVG(age) AS avg_age
FROM retail_sales
WHERE category = 'Beauty';
```

**Q5.** Find all transactions where total sale is greater than 1000
```sql
SELECT *
FROM retail_sales
WHERE total_sale > 1000;
```

**Q6.** Find the total number of transactions made by each gender in each category
```sql
SELECT gender,
       category,
       COUNT(transaction_id) AS total_transactions
FROM retail_sales
GROUP BY gender, category
ORDER BY gender, category;
```

**Q7.** Calculate the average sale for each month and identify the best-selling month for each year

Average sale per month

```sql
SELECT YEAR(sale_date) AS years,
       MONTH(sale_date) AS months,
       AVG(total_sale) AS avg_sales
FROM retail_sales
GROUP BY years, months;
```

Best-selling month per year

```sql
WITH monthly_sales AS (
    SELECT YEAR(sale_date) AS years,
           MONTH(sale_date) AS months,
           SUM(total_sale) AS total_sales
    FROM retail_sales
    GROUP BY years, months
),
ranked_sales AS (
    SELECT years,
           months,
           total_sales,
           DENSE_RANK() OVER (PARTITION BY years ORDER BY total_sales DESC) AS rn
    FROM monthly_sales
)
SELECT *
FROM ranked_sales
WHERE rn = 1;
```
**Q8.** Find the top 5 customers based on highest total sales
```sql
SELECT customer_id,
       SUM(total_sale) AS total_spent
FROM retail_sales
GROUP BY customer_id
ORDER BY total_spent DESC
LIMIT 5;
```


**Q9.** Find the number of unique customers who purchased items from each category
```sql
SELECT category,
       COUNT(DISTINCT customer_id) AS unique_customers
FROM retail_sales
GROUP BY category;
```

**Q10.** Write a SQL query to create each shift and number of orders (Example Morning <12, Afternoon Between 12 & 17, Evening >17)
```sql
SELECT
    CASE
        WHEN HOUR(sale_time) < 12 THEN 'Morning'
        WHEN HOUR(sale_time) > 17 THEN 'Evening'
        ELSE 'Afternoon'
    END AS shift,
    COUNT(transaction_id) AS total_orders
FROM retail_sales
GROUP BY shift;
```

**Q11.** Find Top 2 Customers per Category
```sql
SELECT category,
       customer_id,
       total_spent,
       rn AS rank
FROM (
    SELECT category,
           customer_id,
           SUM(total_sale) AS total_spent,
           DENSE_RANK() OVER (PARTITION BY category ORDER BY SUM(total_sale) DESC) AS rn
    FROM retail_sales
    GROUP BY category, customer_id
) t
WHERE rn <= 2
ORDER BY category, rn;
```

**Q12.** Calculate Month-over-Month (MoM) Sales Growth
```sql
SELECT yr_month,
       total_sales,
       LAG(total_sales) OVER (ORDER BY yr_month) AS prev_month_sales,
       ROUND(
           ((total_sales - LAG(total_sales) OVER (ORDER BY yr_month))
           / LAG(total_sales) OVER (ORDER BY yr_month)) * 100,
           2
       ) AS mom_growth_pct
FROM (
    SELECT DATE_FORMAT(sale_date, '%Y-%m') AS yr_month,
           SUM(total_sale) AS total_sales
    FROM retail_sales
    GROUP BY yr_month
) t
ORDER BY yr_month;
```

**Q13.** Find Running Total per Customer
```sql
SELECT customer_id,
       sale_date,
       total_sale,
       SUM(total_sale) OVER (
           PARTITION BY customer_id
           ORDER BY sale_date
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
       ) AS running_total
FROM retail_sales;
```

---

## (4) Tools & Technologies

* MySQL Workbench 
* CSV Dataset (shape = (2000, 11))

---

## (5) Key Learnings

* Practical use of SQL for business-driven analysis
* Handling real-world retail data
* Applying EDA techniques to derive insights
* Writing optimized queries using aggregations and window functions

---
## Importance of this project

* Improves decision-making by providing clear insights into sales performance, customer behavior, and revenue trends.
* Identifies growth opportunities by highlighting top-performing products, categories, customers, and peak sales periods.
* Enhances profitability analysis by tracking revenue, costs (COGS), and detecting high-value or abnormal transactions.

---

⭐ If you liked this project, feel free to star the repository!
