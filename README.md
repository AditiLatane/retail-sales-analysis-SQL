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

**Q2.** Write a SQL query to retrieve all transactions where the category is 'Clothing' and the quantity sold is more than 4 in the month of Nov-2022.

**Q3.** Calculate total sales for each category

**Q4.** Find the average age of customers who purchased items from the *Beauty* category

**Q5.** Find all transactions where total sale is greater than 1000

**Q6.** Find the total number of transactions made by each gender in each category

**Q7.** Calculate the average sale for each month and identify the best-selling month for each year

**Q8.** Find the top 5 customers based on highest total sales

**Q9.** Find the number of unique customers who purchased items from each category

**Q10.** Write a SQL query to create each shift and number of orders (Example Morning <12, Afternoon Between 12 & 17, Evening >17)

**Q11.** Find Top 2 Customers per Category

**Q12.** Calculate Month-over-Month (MoM) Sales Growth

**Q13.** Find Running Total per Customer

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

⭐ If you liked this project, feel free to star the repository!
