# Fashion Sales Data Analysis using SQL & Python

## Objective
Analyze fashion retail transaction and inventory data to uncover sales performance trends, identify top revenue-generating product categories, and evaluate customer purchasing behavior to inform inventory management and marketing strategies.

---

## Dataset Description
The dataset is structured across relational entities stored in `DataPenjualanFashion.xlsx`:
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

