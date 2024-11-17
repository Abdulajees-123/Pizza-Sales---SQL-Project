# Pizza-Sales---SQL-Project
Pizza Sales - SQL Project For Data Analysis

## Project Overview
This project demonstrates an in-depth analysis of pizza sales data using SQL. It includes calculations of key performance indicators (KPIs), trends analysis, and revenue distribution, providing actionable insights to enhance sales performance.

## Key Features
## A. KPI
1. Total Revenue

        SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;
   <img src ="https://github.com/Abdulajees-123/Pizza-Sales---SQL-Project/blob/main/Total_Revenue.png" class="center">

3. Average Order Value
   
        SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales;
   <img src ="https://github.com/Abdulajees-123/Pizza-Sales---SQL-Project/blob/main/AverageOrderValue.png" class="center">

5. Total Pizzas Sold

        SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales;
<img src ="https://github.com/Abdulajees-123/Pizza-Sales---SQL-Project/blob/main/Total_Pizza_Sold.png" class="center">

6. Total Orders

        SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales;
<img src ="https://github.com/Abdulajees-123/Pizza-Sales---SQL-Project/blob/main/Total_Orders.png" class="center">

8. Average Pizzas Per Order
   
        SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
        CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2)) AS Avg_Pizzas_per_order
        FROM pizza_sales;
<img src = "https://github.com/Abdulajees-123/Pizza-Sales---SQL-Project/blob/main/Avg_Pizza_per_Order.png" class="center">

## B. Daily Trends For Total Orders
Analyze how orders vary across days of the week:

    SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
    FROM pizza_sales
    GROUP BY DATENAME(DW, order_date);
<img src = "https://github.com/Abdulajees-123/Pizza-Sales---SQL-Project/blob/main/Daily_Trend_For_Total_Orders.png"  class="center">
 
## C. Monthly Trend For Orders
Identify monthly trends to optimize seasonal strategies:

    SELECT DATENAME(MONTH, order_date) AS Month_Name, COUNT(DISTINCT order_id) AS Total_Orders 
    FROM pizza_sales
    GROUP BY DATENAME(MONTH, order_date);
<img src = "https://github.com/Abdulajees-123/Pizza-Sales---SQL-Project/blob/main/Monthly_trend_For_Orders.png" class="center">
    
## D. % of Sales by Pizza Category
Understand revenue contribution by category:  

    SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) AS total_revenue,
    CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM pizza_sales) AS DECIMAL(10,2)) AS PCT
    FROM pizza_sales
    GROUP BY pizza_category;
<img src = "https://github.com/Abdulajees-123/Pizza-Sales---SQL-Project/blob/main/%25%20Of%20Sales%20by%20Pizza%20Category.png" class="center">

## E. % of Sales by Pizza Size
Analyze revenue distribution across different pizza sizes:

    SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) AS total_revenue,
    CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM pizza_sales) AS DECIMAL(10,2)) AS PCT
    FROM pizza_sales
    GROUP BY pizza_size
    ORDER BY pizza_size;
 <img src = "https://github.com/Abdulajees-123/Pizza-Sales---SQL-Project/blob/main/%25%20of%20Sales%20by%20Pizza%20Size.png" class="center">

## F. Total Pizzas Sold by Pizza Category
Find the most popular pizza categories during February:

    SELECT pizza_category, SUM(quantity) AS Total_Quantity_Sold 
    FROM pizza_sales
    WHERE MONTH(order_date) = 2
    GROUP BY pizza_category
    ORDER BY Total_Quantity_Sold DESC;
<img src = "https://github.com/Abdulajees-123/Pizza-Sales---SQL-Project/blob/main/Total%20Pizzas%20Sold%20by%20Pizza%20Category.png" class="center">

## G. Top & Bottom Pizzas by Revenue
Top 5

    SELECT TOP 5 pizza_name, SUM(total_price) AS Total_Revenue 
    FROM pizza_sales 
    GROUP BY pizza_name 
    ORDER BY Total_Revenue DESC;
 <img src ="https://github.com/Abdulajees-123/Pizza-Sales---SQL-Project/blob/main/Top%205%20Pizzas%20by%20Revenue.png"  class="center">  

Bottom 5

    SELECT TOP 5 pizza_name, SUM(total_price) AS Total_Revenue 
    FROM pizza_sales 
    GROUP BY pizza_name 
    ORDER BY Total_Revenue ASC;
<img src ="https://github.com/Abdulajees-123/Pizza-Sales---SQL-Project/blob/main/Bottom%205%20Pizzas%20by%20Revenue.png" class="center">  

## H. Top & Bottom Pizzas by Quantity 
Top 5

    SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold 
    FROM pizza_sales 
    GROUP BY pizza_name 
    ORDER BY Total_Pizza_Sold DESC;
  <img src = "https://github.com/Abdulajees-123/Pizza-Sales---SQL-Project/blob/main/Top%205%20Pizzas%20by%20Quantity.png" class="center">   

Bottom 5

    SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold 
    FROM pizza_sales 
    GROUP BY pizza_name 
    ORDER BY Total_Pizza_Sold ASC;
  <img src = "https://github.com/Abdulajees-123/Pizza-Sales---SQL-Project/blob/main/Bottom%205%20Pizzas%20by%20Quantity.png" class="center">    

## I. Top & Bottom Pizzas by Orders
Top 5

    SELECT TOP 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders 
    FROM pizza_sales 
    GROUP BY pizza_name 
    ORDER BY Total_Orders DESC;
<img src = "https://github.com/Abdulajees-123/Pizza-Sales---SQL-Project/blob/main/Top%205%20Pizzas%20by%20Total%20Orders.png" class="center">   
 
Bottom 5

    SELECT TOP 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders 
    FROM pizza_sales 
    GROUP BY pizza_name 
    ORDER BY Total_Orders ASC;
 <img src = "https://github.com/Abdulajees-123/Pizza-Sales---SQL-Project/blob/main/Bottom%205%20Pizzas%20by%20total%20Orders.png"  class="center">  

## J. Filtering Insights
Apply filters to queries for more granular analysis. Example: Filter by pizza category:

    SELECT TOP 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders 
    FROM pizza_sales 
    WHERE pizza_category = 'Classic' 
    GROUP BY pizza_name 
    ORDER BY Total_Orders ASC;


##Project Goals

This project aims to:

Identify trends and patterns in pizza sales.
Enhance business strategies through data-driven insights.
Optimize product offerings based on customer preferences.








