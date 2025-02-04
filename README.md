# SQL-Projects
Restaurant Orders Data Analysis using SQL

📌 Project Overview

This project analyzes a restaurant's order data, providing insights into customer preferences, high-spending orders, and sales trends. The analysis is performed using SQL queries to extract meaningful patterns from the data.

📂 Dataset

The dataset consists of two primary tables:

menu_items: Contains details of menu items, including name, category, and price.

order_details: Stores order information, including date, time, and items purchased.

Key Questions Answered

What were the least and most ordered items? Which categories do they belong to?

What do high-spending orders look like? Which items were included?


🔧 SQL Queries Used

📌 Menu Table Analysis
# View the menu table
SELECT * FROM menu_items;

# Find the number of items on the menu
SELECT COUNT(*) FROM menu_items;

# Find the least and most expensive item
SELECT * FROM menu_items ORDER BY price DESC;

# Count number of Italian dishes
SELECT COUNT(*) FROM menu_items WHERE category = 'Italian';

# Average dish price within each category
SELECT category, AVG(price) AS avg_price FROM menu_items GROUP BY category;


📌 Order Details Analysis
# View order details
SELECT * FROM order_details;

# Date range of orders
SELECT MIN(order_date), MAX(order_date) FROM order_details;

# Total number of orders
SELECT COUNT(DISTINCT order_id) FROM order_details;

# Orders with the most items
SELECT order_id, COUNT(item_id) AS item_count
FROM order_details
GROUP BY order_id
ORDER BY item_count DESC;


📌 Joining Menu & Order Data for Insights
# Combine order details with menu items
SELECT * FROM order_details od
LEFT JOIN menu_items mi ON od.item_id = mi.menu_item_id;

# Most and least ordered items
SELECT item_name, COUNT(order_details_id) AS num_orders
FROM order_details od
LEFT JOIN menu_items mi ON od.item_id = mi.menu_item_id
GROUP BY item_name
ORDER BY num_orders DESC;

# Top 5 highest-spend orders
SELECT order_id, SUM(price) AS total_spend
FROM order_details od
LEFT JOIN menu_items mi ON od.item_id = mi.menu_item_id
GROUP BY order_id
ORDER BY total_spend DESC
LIMIT 5;


# Restaurant Order Insights

## Overview
This analysis explores order trends from a restaurant database by examining the most and least ordered items, highest spending orders, and category-wise distribution.

---

## Key Insights

### 1. Category-Wise Order Distribution
- Italian cuisine had the highest number of orders with **26 items**.
- Asian cuisine followed with **17 items**.
- Mexican and American categories had **16 and 10 items**, respectively.

### 2. Highest Spending Orders
- The **top 5 highest-spending orders** ranged from **$185 to $192**.
- Order **#440** had the highest total spend of **$192.15**.

### 3. Most Purchased Items
- **Hamburger** was the most ordered item with **622 orders**.
- Other popular items:
  - Edamame: **620 orders**
  - Korean Beef Bowl: **588 orders**
  - Cheeseburger: **583 orders**
  - French Fries: **571 orders**

### 4. Top Revenue-Generating Items
- **Korean Beef Bowl** generated the highest revenue of **$10,554.60**.
- Other high-earning items:
  - Spaghetti & Meatballs: **$8,436.50**
  - Tofu Pad Thai: **$8,149.00**
  - Cheeseburger: **$8,132.85**
  - Hamburger: **$8,054.90**

### 5. Least Ordered Items
- The most popular items were from the **American and Asian categories**.
- Some items were ordered far less frequently, which may require promotions or discounts to boost sales.

---

## Conclusion
- Italian cuisine leads in total orders, but Asian cuisine also has high demand.
- American fast food items dominate in popularity.
- Korean Beef Bowl and Spaghetti & Meatballs generate the highest revenue.
- Orders above $190 contribute significantly to overall revenue.

This analysis can help with menu optimization, inventory planning, and marketing strategy improvements.



