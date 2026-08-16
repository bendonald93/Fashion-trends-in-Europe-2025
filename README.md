


---

### **SQL Analysis**

**1. Business Overview & KPI Summary**
```sql
SELECT 
    COUNT(DISTINCT transaction_id) AS total_orders,
    COUNT(DISTINCT customer_id) AS total_customers,
    SUM(total_price) AS total_revenue,
    ROUND(AVG(total_price), 2) AS avg_order_value
FROM sales;

