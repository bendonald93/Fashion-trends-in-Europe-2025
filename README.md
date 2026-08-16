Project Title: Fashion Sales Data Analysis using SQL & Python

Objective

Analyze fashion retail transaction and inventory data to uncover sales performance trends, identify top revenue-generating product categories, and evaluate customer purchasing behavior to inform inventory management and marketing strategies.

Dataset Description

The dataset is structured across relational entities stored in DataPenjualanFashion.xlsx:

SalesItems: Contains transactional records including order IDs, transaction dates, customer IDs, product IDs, order quantities, applied discounts, and net order totals.

ProductItems: Contains product details including SKU codes, item names, product categories, unit prices, supplier details, and stock inventory levels.

1. Key SQL Insights
Overall Business Performance & KPIs
SELECT 
    COUNT(DISTINCT TransactionID) AS total_orders,
    COUNT(DISTINCT CustomerID) AS total_customers,
    SUM(TotalAmount) AS total_revenue,
    ROUND(AVG(TotalAmount), 2) AS avg_order_value
FROM SalesItems;
2. Revenue & Volume by Product Category
SELECT 
    p.Category,
    COUNT(s.TransactionID) AS total_units_sold,
    SUM(s.TotalAmount) AS revenue,
    ROUND(AVG(s.Discount), 2) AS avg_discount_rate
FROM SalesItems s
JOIN ProductItems p ON s.ProductID = p.ProductID
GROUP BY p.Category
ORDER BY revenue DESC;
3. Monthly Sales Growth & Revenue Trends
SELECT 
    strftime('%Y-%m', s.TransactionDate) AS sales_month,
    COUNT(DISTINCT s.TransactionID) AS monthly_orders,
    SUM(s.TotalAmount) AS monthly_revenue
FROM SalesItems s
GROUP BY sales_month
ORDER BY sales_month ASC;
4. Inventory Turnover & Stock Availability
SELECT 
    p.ProductName,
    p.Category,
    p.StockQuantity,
    COALESCE(SUM(s.Quantity), 0) AS units_sold
FROM ProductItems p
LEFT JOIN SalesItems s ON p.ProductID = s.ProductID
GROUP BY p.ProductID
ORDER BY units_sold DESC;
Key Findings
Key Findings

Revenue Drivers: A minority of core fashion categories account for the vast majority of total sales revenue, highlighting key anchor products.

Discount Sensitivity: Higher discount rates correlate with elevated order volume, though net revenue margins require monitoring during major promotional periods.

Seasonality: Transaction volume peaks during key retail periods, signaling optimal windows for targeted promotional campaigns and stock replenishment.
