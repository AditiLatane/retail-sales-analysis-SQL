# Retail Sales Analysis (SQL Project)

##  Project Overview

This project focuses on analyzing retail sales data to uncover insights related to sales performance, customer behavior, revenue trends, and profitability. The analysis includes data cleaning, exploratory data analysis (EDA), profitability analysis, and answering real-world business questions using SQL.

---

##  (1)Data Cleaning

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

---

## 8. Profitability Analysis

* Profit per transaction
* Profit by category
* Profit by gender

---

## 9. Outlier Detection

* Identification of very high sales values

---

##  Answering Business Questions

1. Retrieve all columns for sales made on **2022-11-05**
2. Retrieve all transactions where:

   * Category is *Clothing*
   * Quantity sold is more than 4
   * Month is November 2022
3. Calculate total sales (`total_sale`) for each category
4. Find the average age of customers who purchased items from the *Beauty* category
5. Find all transactions where `total_sale` is greater than **1000**
6. Find the total number of transactions (`transaction_id`) made by each gender in each category
7. Calculate the average sale for each month and identify the **best-selling month** for each year
8. Find the **top 5 customers** based on highest total sales
9. Find the number of **unique customers** who purchased items from each category
10. Create sales shifts and count number of orders:

    * Morning (< 12)
    * Afternoon (12–17)
    * Evening (> 17)
11. Find **Top 2 Customers per Category**
12. Calculate **Month-over-Month (MoM) Sales Growth**
13. Find **Running Total per Customer**

---

## 🛠️ Tools & Technologies

* MySQL Workbench 
* CSV Dataset (shape = (2000, 11))

---

## 📈 Key Learnings

* Practical use of SQL for business-driven analysis
* Handling real-world retail data
* Applying EDA techniques to derive insights
* Writing optimized queries using aggregations and window functions

---

⭐ If you liked this project, feel free to star the repository!
