# 📊 Retail Sales Analysis Using SQL

## Project Overview
This project analyzes retail sales data using SQL to understand revenue trends, customer behavior, and payment preferences.  
The objective was to extract business insights from transactional data and identify key revenue drivers.

## Dataset Description
The dataset contains transactional sales records with the following columns:

- invoice_no
- customer_id
- gender
- age
- category
- quantity
- price
- payment_method
- invoice_date
- shopping_mall

Each row represents a single transaction.

## Business Questions Solved
- How many unique customers are there?
- What is the total revenue generated?
- Which product categories generate the highest revenue?
- Who are the top 5 highest spending customers?
- Which payment method generates the most revenue?
- How does revenue trend monthly?

## SQL Queries

### Total Unique Customers
sql
SELECT COUNT(DISTINCT customer_id) AS total_customers 
FROM sales;

### Total Revenue
sql
SELECT SUM(quantity * price) AS total_revenue 
FROM sales;

### Revenue by Category
sql
SELECT category, 
       SUM(quantity * price) AS category_revenue
FROM sales
GROUP BY category
ORDER BY category_revenue DESC;

### Top 5 Highest Spending Customers
sql
SELECT customer_id, 
       SUM(quantity * price) AS total_spent
FROM sales
GROUP BY customer_id
ORDER BY total_spent DESC
LIMIT 5;


### Revenue by Payment Method
sql
SELECT payment_method, 
       SUM(quantity * price) AS revenue
FROM sales
GROUP BY payment_method
ORDER BY revenue DESC;

### Monthly Revenue Trend
sql
SELECT 
  substr(invoice_date, 7, 4) || '-' || substr(invoice_date, 4, 2) AS sales_month,
  SUM(quantity * price) AS monthly_revenue
FROM sales
GROUP BY sales_month
ORDER BY sales_month;

## Key Insights
- Total revenue was calculated directly from transactional quantity and price.
- Certain product categories significantly outperform others in revenue contribution.
- A small group of customers contributes disproportionately to total sales.
- Payment method preferences influence revenue distribution.
- Monthly sales trends help identify seasonality patterns.

## Tools Used
- SQL
- Aggregation functions (SUM, COUNT)
- GROUP BY
- ORDER BY
- LIMIT
- String manipulation (substr)
- Revenue Analysis
- Customer Segementation
