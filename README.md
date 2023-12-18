![Alt text](relative%20path/to/img.jpg?raw=true "Title")
<a href="https://ibb.co/17MSV0G"><img src="https://i.ibb.co/xXY4v2q/Screenshot-298.png" alt="Screenshot-298" border="0"></a>

**Data Analyst Report: Pizza Sales Analysis**

**A. Key Performance Indicators (KPIs)**

1. **Total Revenue:**
   - The total revenue generated from pizza sales is calculated by summing the `total_price` field in the `pizza_sales` table.
   - Query: `SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;`

2. **Average Order Value:**
   - The average order value is calculated by dividing the total revenue by the count of distinct order IDs.
   - Query: `SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales;`

3. **Total Pizzas Sold:**
   - The total quantity of pizzas sold is obtained by summing the `quantity` field in the `pizza_sales` table.
   - Query: `SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales;`

4. **Total Orders:**
   - The total number of orders is calculated by counting the distinct order IDs in the `pizza_sales` table.
   - Query: `SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales;`

5. **Average Pizzas Per Order:**
   - The average number of pizzas per order is determined by dividing the total quantity of pizzas by the count of distinct order IDs.
   - Query: `SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2)) AS Avg_Pizzas_per_order FROM pizza_sales;`

**B. Daily Trend for Total Orders:**
   - The daily trend for total orders is presented by counting the distinct order IDs for each day of the week.
   - Query: `SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders FROM pizza_sales GROUP BY DATENAME(DW, order_date);`

**C. Monthly Trend for Orders:**
   - The monthly trend for orders is illustrated by counting the distinct order IDs for each month.
   - Query: `SELECT DATENAME(MONTH, order_date) AS Month_Name, COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales GROUP BY DATENAME(MONTH, order_date);`

**D. % of Sales by Pizza Category:**
   - The percentage of sales contributed by each pizza category is calculated based on total revenue.
   - Query: `SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue, CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM pizza_sales) AS DECIMAL(10,2)) AS PCT FROM pizza_sales GROUP BY pizza_category;`

**E. % of Sales by Pizza Size:**
   - The percentage of sales attributed to each pizza size is determined based on total revenue.
   - Query: `SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue, CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM pizza_sales) AS DECIMAL(10,2)) AS PCT FROM pizza_sales GROUP BY pizza_size ORDER BY pizza_size;`

**F. Total Pizzas Sold by Pizza Category (February):**
   - The total quantity of pizzas sold for each pizza category in the month of February is displayed.
   - Query: `SELECT pizza_category, SUM(quantity) as Total_Quantity_Sold FROM pizza_sales WHERE MONTH(order_date) = 2 GROUP BY pizza_category ORDER BY Total_Quantity_Sold DESC;`

**G. Top 5 Pizzas by Revenue:**
   - The top 5 pizzas based on total revenue are identified by summing the total price for each pizza name.
   - Query: `SELECT TOP 5 pizza_name, SUM(total_price) AS Total_Revenue FROM pizza_sales GROUP BY pizza_name ORDER BY Total_Revenue DESC;`

**H. Bottom 5 Pizzas by Revenue:**
   - The bottom 5 pizzas by revenue are determined by summing the total price for each pizza name.
   - Query: `SELECT TOP 5 pizza_name, SUM(total_price) AS Total_Revenue FROM pizza_sales GROUP BY pizza_name ORDER BY Total_Revenue ASC;`

**I. Top 5 Pizzas by Quantity:**
   - The top 5 pizzas based on total quantity sold are identified by summing the quantity for each pizza name.
   - Query: `SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold FROM pizza_sales GROUP BY pizza_name ORDER BY Total_Pizza_Sold DESC;`

**J. Bottom 5 Pizzas by Quantity:**
   - The bottom 5 pizzas by quantity sold are determined by summing the quantity for each pizza name.
   - Query: `SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold FROM pizza_sales GROUP BY pizza_name ORDER BY Total_Pizza_Sold ASC;`

**K. Top 5 Pizzas by Total Orders:**
   - The top 5 pizzas based on total orders are identified by counting the distinct order IDs for each pizza name.
   - Query: `SELECT TOP 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales GROUP BY pizza_name ORDER BY Total_Orders DESC;`

**L. Bottom 5 Pizzas by Total Orders:**
   - The bottom 5 pizzas by total orders are determined by counting the distinct order IDs for each pizza name.
   - Query: `SELECT TOP 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales GROUP BY pizza_name ORDER BY Total_Orders ASC;`

**Note:** To apply filters by pizza category or size, you can use the `WHERE` clause as exemplified in the provided query examples.
