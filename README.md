# Pizza_Sales


PIZZA SALES SQL QUERIES
A. KPI’s
1. Total Revenue:
SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;
 
**2. Average Order Value**
SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales
 
**3. Total Pizzas Sold**
SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales
 
**4. Total Orders**
SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales
 
**5. Average Pizzas Per Order**
SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2))
AS Avg_Pizzas_per_order
FROM pizza_sales
 
**B. Daily Trend for Total Orders**
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
GROUP BY DATENAME(DW, order_date)
Output:
 
**C. Monthly Trend for Orders**
select DATENAME(MONTH, order_date) as Month_Name, COUNT(DISTINCT order_id) as Total_Orders
from pizza_sales
GROUP BY DATENAME(MONTH, order_date)Output
 


**D. % of Sales by Pizza Category**
SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category
Output
 
**E. % of Sales by Pizza Size**
SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY pizza_size
Output
 

**F. Total Pizzas Sold by Pizza Category**
SELECT pizza_category, SUM(quantity) as Total_Quantity_Sold
FROM pizza_sales
WHERE MONTH(order_date) = 2
GROUP BY pizza_category
ORDER BY Total_Quantity_Sold DESC
Output
 
**G. Top 5 Pizzas by Revenue**
SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue DESC
 
**H. Bottom 5 Pizzas by Revenue**
SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue ASC
 
**I. Top 5 Pizzas by Quantity**
SELECT Top 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold DESC
Output
 
**J. Bottom 5 Pizzas by Quantity**
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold ASC
Output
 



**K. Top 5 Pizzas by Total Orders**
SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders DESC
 
**L. Borrom 5 Pizzas by Total Orders**
SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders ASC
 
**NOTE**
If you want to apply the pizza_category or pizza_size filters to the above queries you can use WHERE clause. Follow some of below examples
SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
WHERE pizza_category = 'Classic'
GROUP BY pizza_name
ORDER BY Total_Orders ASC

**Business Problem**
The pizza restaurant chain lacked visibility into its key sales metrics, order patterns, and product performance. Decision-makers needed a comprehensive understanding of daily operations and customer preferences to improve marketing strategies, inventory planning, and menu design.

**Goal of the Dashboard**
The main objective of the dashboard is to:

Monitor overall sales performance.

Identify high and low-performing products.

Understand customer ordering behavior by time, size, and category.

Drive data-informed decisions to optimize revenue and operational efficiency.

**Key Visuals and Chart Details**
Visual	Description
KPI Cards	Displays Total Revenue, Total Orders, Avg Order Value, Total Pizzas Sold, and Avg Pizzas per Order.
Daily Order Trend (Line Chart)	Visualizes how total orders vary by day of the week, helping identify peak days.
Monthly Order Trend (Column Chart)	Shows monthly order distribution, useful for seasonal analysis.
Pie Chart: Sales by Category	Percentage contribution of each pizza category to total revenue.
Pie Chart: Sales by Size	Highlights revenue share by pizza sizes (S, M, L, XL).
Bar Chart: Pizzas Sold by Category (Feb)	Focuses on the quantity sold for each category in a specific month.
Top/Bottom 5 Pizzas by Revenue (Bar Chart)	Ranks best and worst performing pizzas in terms of revenue.
Top/Bottom 5 Pizzas by Quantity	Displays quantity-based performance of pizzas, revealing popular choices.
Top/Bottom 5 Pizzas by Orders	Shows pizza popularity by order count.

Business Impact and Insights
Product Optimization: Identifying underperforming pizzas enables the business to modify or remove items from the menu.

Sales Growth Strategy: Recognizing top-selling categories and sizes helps target promotions effectively.

Inventory Planning: Understanding daily and monthly demand patterns ensures efficient stock management.

Customer Behavior Analysis: Average pizzas per order and size/category preferences help customize offerings.

Revenue Improvement: Monitoring order values and category contributions supports strategic pricing and bundling.


![Darshborad Preview](https://github.com/vishalsn33/Pizza_Sales/blob/main/Home%20Dashboard.png)







