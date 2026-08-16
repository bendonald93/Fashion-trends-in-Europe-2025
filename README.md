# Fashion Sales Data Analysis using SQL & Python

## Objective
Analyze fashion retail transaction and inventory data to uncover sales performance trends, identify top revenue-generating product categories, and evaluate customer purchasing behavior to inform inventory management and marketing strategies.

---

## Dataset Description
The dataset is structured across relational entities stored in `DataSet.xlsx`:
* **SalesItems:** Contains transactional records including order IDs, transaction dates, customer IDs, product IDs, order quantities, applied discounts, and net order totals.
* **ProductItems:** Contains product details including SKU codes, item names, product categories, unit prices, supplier details, and stock inventory levels.

---

## Key SQL Insights

### 1. Overall Business Performance & KPIs
```sql
SELECT 
    COUNT(DISTINCT TransactionID) AS total_orders,
    COUNT(DISTINCT CustomerID) AS total_customers,
    SUM(TotalAmount) AS total_revenue,
    ROUND(AVG(TotalAmount), 2) AS avg_order_value
FROM SalesItems;
```
### 2. Sales & Revenue Performance by Product Category
```sql
SELECT 
    p.Category,
    COUNT(s.TransactionID) AS total_units_sold,
    SUM(s.TotalAmount) AS revenue,
    ROUND(AVG(s.Discount), 2) AS avg_discount_rate
FROM SalesItems s
JOIN ProductItems p ON s.ProductID = p.ProductID
GROUP BY p.Category
ORDER BY revenue DESC;
```
### 3. Monthly Sales Growth & Revenue Trend
```sql
SELECT 
    strftime('%Y-%m', s.TransactionDate) AS sales_month,
    COUNT(DISTINCT s.TransactionID) AS monthly_orders,
    SUM(s.TotalAmount) AS monthly_revenue
FROM SalesItems s
GROUP BY sales_month
ORDER BY sales_month ASC;
```
### 4. Inventory Stock vs. Top Selling Products
```sql
SELECT 
    p.ProductName,
    p.Category,
    p.StockQuantity,
    COALESCE(SUM(s.Quantity), 0) AS units_sold
FROM ProductItems p
LEFT JOIN SalesItems s ON p.ProductID = s.ProductID
GROUP BY p.ProductID
ORDER BY units_sold DESC
LIMIT 10;
```

## Key Findings & Business Recommendations
* **Top Revenue Drivers**: Sales are heavily concentrated in primary fashion categories; targeted marketing should focus on these high-margin core lines.
* **Discount Impact**: Promotional discount periods correlate with higher order volumes, but discounting strategies must be balanced to protect overall operating argins.
* **Stock Optimization**: Combining sales velocity data with remaining stock levels helps prevent stockouts on high-demand items while identifying slow-moving inventory.

## Tech Stack & Tools
* **Language**: Python
* **Database Engine**: SQLite / sqlite3
* **Data Processing**: pandas, openpyxl
* **Visualization**: matplotlib, seaborn
* **Platform**: Jupyter Notebook / GitHub
