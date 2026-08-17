# Fashion Sales Data Analysis using SQL & Python

## Project Overview
This project provides an end-to-end exploratory data analysis of fashion retail sales and inventory data using **Python**, **Pandas**, and **SQLite**. By executing structured SQL queries directly within an in-memory SQLite database, this analysis reveals overall business performance, sales distribution across channels, and product catalog details.

---

## Dataset Overview (`DataSet.xlsx`)
The analysis relies on two sheets loaded from the `DataSet.xlsx` file:

* **`SalesItems`**: Transaction records including sales quantities, unit prices, total item revenues, sales channels, and campaign references.
* **`ProductItems`**: Catalog details including product IDs, product names, categories, brand info, catalog prices, cost prices, and target demographics.

---

## Tech Stack & Libraries
* **Language:** Python
* **Database Engine:** SQLite / `sqlite3`
* **Data Processing & I/O:** `pandas`, `openpyxl`
* **Data Visualization:** `matplotlib`, `seaborn`
* **Analysis Notebook:** `Fashion_Sales_Analysis.ipynb`

---

## Project Structure & Workflow
The analysis is self-contained within **`Fashion_Sales_Analysis.ipynb`**, structured into three modular steps:

1. **Environment Setup & Database Initialization:** Installs required packages (`seaborn`, `openpyxl`), reads Excel data into Pandas DataFrames, and populates an in-memory SQLite database.
2. **SQL Query Execution:** Runs SQL queries to evaluate key performance metrics:
   * Overall Business KPIs (Total Transactions, Units Sold, Revenue, Average Order Value)
   * Revenue breakdown by Sales Channel and Marketing Campaigns
   * Product Catalog Breakdown by Category and Gender
   * Transaction volume analysis by quantity purchased
3. **Data Visualization:** Generates clean bar charts using `seaborn` to display revenue streams and catalog distribution visually.

---

## Key SQL Insights Summary

| Metric / Query | Focus |
| :--- | :--- |
| **Overall Business KPIs** | Evaluates total sales revenue, total units sold, and average transaction value. |
| **Sales Performance by Channel** | Compares total revenue and volume generated across different sales channels. |
| **Catalog Breakdown** | Analyzes product depth across categories and gender segments along with average pricing. |

---

## How to Run the Notebook

### 1. Web / Browser (JupyterLite or Try Jupyter)
1. Upload **`DataSet.xlsx`** and **`Fashion_Sales_Analysis.ipynb`** into the workspace sidebar.
2. Select **Python (Pyodide)** as the kernel when prompted.
3. Run each cell sequentially (**Shift + Enter**).

### 2. Local Setup
1. Clone this repository:
   ```bash
   git clone [https://github.com/bendonald93/Fashion-trends-in-Europe-2025.git](https://github.com/bendonald93/Fashion-trends-in-Europe-2025.git)
   cd Fashion-trends-in-Europe-2025
