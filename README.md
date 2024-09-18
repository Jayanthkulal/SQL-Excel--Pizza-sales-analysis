# SQL-Excel-Pizza-sales-analysis

## Overview
This project is a comprehensive analysis of pizza sales data using SQL and Excel. The dataset provides insights into total revenue, average order values, best and worst-selling pizzas, sales trends, and more. The dashboard, created in Excel, visualizes the results of the analysis, helping to inform business decisions.

## Features
 - Key Performance Indicators (KPIs): IncludesTotal Revenue, Average Order Value, Total Pizza Sold, Total Orders, and Average Pizzas Per Order.
  
- Busiest Days & Time: Analysis of days and times with the highest number of orders.
  
- Sales by Category & Size: Breakdowns of pizza sales by category (e.g., Chicken, Classic, Veggie) and size (Medium, Large, Extra Large).
  
- Best & Worst Sellers: Identifies the top 5 best-selling and bottom 5 worst-selling pizzas based on total pizzas sold.
  
- Hourly and Daily Trends: Visualizes the distribution of orders across different hours of the day and days of the week.

## Dataset

dataset used for this task is Pizza sales excel file 

Dataset: [Pizza sales](https://github.com/Jayanthkulal/SQL-Excel--Pizza-sales-analysis/blob/main/pizza_sales%20excel%20file.xlsx)

## SQL Queries Used
Sql Quries used for find out some KPI as below:

Document: [Sql Queries](https://github.com/Jayanthkulal/SQL-Excel--Pizza-sales-analysis/blob/main/Pizza%20Sales%20SQL%20queries.docx)

   - Total Revenue: select sum(total_price) as total_revenue from [pizza_sales excel file].
 
   -  Average Order Value: select sum(total_price) / COUNT(DISTINCT ORDER_ID) as average_order_value FROM [pizza_sales excel file].

   -  Total Pizza Sold: select sum(quantity) as total_pizza_sold from [pizza_sales excel file].

   - Total Orders: select count( distinct order_id) as total_orders from [pizza_sales excel file].

- Average Pizzas Per Order: select cast(cast(sum(quantity) as decimal(10,2)) / cast(COUNT(distinct order_id)as decimal(10,2)) as decimal(10,2)) as avg_piza_per_order from [pizza_sales excel file].

- Daily Trend of Total Orders: select DATENAME(dw, order_date)as order_date, count(distinct order_id) as total_order from [pizza_sales excel file] group by  DATENAME(dw, order_date).

- Hourly Trend of Total Orders: select DATEPART(hour, order_time) as order_hour,count(distinct order_id) as total_order from [pizza_sales excel file] group by DATEPART(hour, order_time) order by DATEPART(hour, order_time).

- Percentage of Sales by Pizza Category: select pizza_category, cast(sum(total_price)as decimal(10,2)) as total_sales,CAST(sum(total_price)*100/
 (select sum(total_price) from [pizza_sales excel file]) AS DECIMAL(10,2)) AS PCT
 from [pizza_sales excel file]  group by  pizza_category.

- Percentage of Sales by Pizza Size: select pizza_size, cast(sum(total_price)as decimal(10,2)) as total_sales, cast(sum(total_price)*100/(select sum(total_price) 
 from [pizza_sales excel file] where DATEPART(QUARTER, order_date)=1) as decimal(10,2)) as pct
from [pizza_sales excel file] where DATEPART(QUARTER, order_date)=1 group by  pizza_size 
order by pct desc.

- total pizza sold by pizza category: SELECT PIZZA_CATEGORY, SUM(quantity) AS TOTAL_SALES FROM [pizza_sales excel file] GROUP BY pizza_category ORDER BY SUM(quantity) DESC.

- top 5 best sellers by total pizzas sold: select top 5 pizza_name, sum(quantity) as total_sales from [pizza_sales excel file]
group by pizza_name order by sum(quantity) desc,

- bottom 5 sellers by total pizzas sold: select top 5 pizza_name, sum(quantity) as total_sales from [pizza_sales excel file]
group by pizza_name order by sum(quantity) asc.

## Data Preparation For the visualization 

Data Cleaning for the dataset was done in excel  as follows:
- created Total order coloum separately to ease the dashboard preparation( In order to find the distinct total order)
- Created order day coloumn
- Removed Unnecessary columns.
- Removed Unnecessary rows.
- Each of the columns in the table were validated to have the correct data type.

## Visualization
The following visualizations were created using Excel:

- KPI Cards - Displaying Total Revenue, Average Order Value, Total Pizza Sold, Total Orders, and Average Pizzas per Order.
- Bar Charts - Showing the daily and hourly trends of total orders.
- Pie Charts - Displaying the percentage of sales by pizza category and pizza size.
- Horizontal Bar Charts - Highlighting total pizza sold by category and the top 5 best-selling pizzas.

## Dasboard 
  Pizza sales Analysis

  View Dshboard - [Excel Pizza sales analysis](https://github.com/Jayanthkulal/SQL-Excel--Pizza-sales-analysis/blob/main/Excel%20project%20-%20Pizza%20sales.xlsx)

  ![Screenshot 2024-09-15 224017](https://github.com/user-attachments/assets/8d7c8195-0168-4f39-a7c1-15941e1f92a0)


  ## Insights

  - Total Revenue: $70,397 generated from 1,840 orders.

  - Average Order Value: Each order generates an average of $38.26.

  -  High-Order Days: Thursday, Friday, and Saturday have the highest number of orders.

   - Peak Order Times: Maximum orders occur between 12 PM and 1 PM, indicating lunch hours as the peak time for pizza sales.

   - Classic Pizzas account for the majority of sales, with 1,286 pizzas sold.

   - The Barbecue Chicken Pizza is the top seller with 231 pizzas sold, followed by The Hawaiian Pizza (217) and Thai Chicken Pizza (213).

   - The Brie Carre Pizza is the least popular with just 46 pizzas sold, followed by Calabrese Pizza (65) and Spinach Supreme Pizza (71).

   - Order Peaks: Orders peak at 12 PM and continue to be strong until around 8 PM, after which they gradually decline.

   - Pizza Category Contribution: The Classic pizza category leads sales, followed by Veggie pizzas. The other categories like Chicken and Supreme make up a smaller portion 
     but are still significant.

   - Size Contribution: Large pizzas dominate the size distribution with nearly half the total sales. Offering combo deals on large pizzas could further drive revenue.












