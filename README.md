# sales-analytics-dashboard
Interactive sales data analytics platform tracking regional KPIs, growth trends, and pipeline metrics.
# Enterprise Sales Intelligence Dashboard

An interactive executive BI dashboard and reporting engine built with a zero-server footprint using Tailwind CSS, Chart.js, and an optimized CSV parsing engine.

To launch the system, simply open **`index.html`** in any modern web browser.

---

## 📊 Cross-Platform Formula Matrix

Use these matching formulas to sync data rules and metric calculations across your other enterprise tech stacks:

### 1. Total Revenue
* **Python (Pandas):** `total_revenue = df['Total_Sales'].sum()`
* **Power BI (DAX):** `Total Revenue = SUM(Sales[Total_Sales])`
* **SQL:** `SELECT SUM(Total_Sales) AS Total_Revenue FROM Sales;`
* **Excel:** `=SUM(K:K)` *(Assumes Total_Sales is in Column K)*

### 2. Net Profit Margin
* **Python (Pandas):** `net_profit_margin = (df['Profit'].sum() / df['Total_Sales'].sum()) * 100`
* **Power BI (DAX):** `Net Profit Margin = DIVIDE(SUM(Sales[Profit]), SUM(Sales[Total_Sales]), 0)`
* **SQL:** `SELECT (SUM(Profit) / SUM(Total_Sales)) * 100 AS Net_Profit_Margin_Pct FROM Sales;`
* **Excel:** `=SUM(N:N)/SUM(K:K)` *(Assumes Profit is in Col N and Total_Sales is in Col K; format cell as %)*

### 3. Average Order Value (AOV)
* **Python (Pandas):** `aov = df['Total_Sales'].mean()`
* **Power BI (DAX):** `AOV = DIVIDE(SUM(Sales[Total_Sales]), DISTINCTCOUNT(Sales[Order_ID]), 0)`
* **SQL:** `SELECT AVG(Total_Sales) AS Average_Order_Value FROM Sales;`
* **Excel:** `=AVERAGE(K:K)`

---

## 🗺️ Data Schema Requirements

If uploading a custom dataset using the **📁 Upload Data CSV** option, format your CSV file with these exact column headers:

| Column Name | Data Type | Example Value |
| :--- | :--- | :--- |
| `Order_ID` | String / Int | `1001` |
| `Order_Date` | Date (`YYYY-MM-DD`) | `2026-01-15` |
| `Customer_Name` | String | `Acme Corp` |
| `City` | String | `New York` |
| `Region` | String | `East` |
| `Product_Category` | String | `Technology` |
| `Product_Name` | String | `Cloud Server Pro` |
| `Sales_Rep` | String | `Alice` |
| `Units_Sold` | Integer | `5` |
| `Unit_Price` | Numeric | `500` |
| `Total_Sales` | Numeric | `2500` |
| `Payment_Method` | String | `Credit Card` |
| `Discount_%` | Numeric | `10` |
| `Profit` | Numeric | `600` |

---

## 🚀 Quick Start

1. **Clone the repository:**
   ```bash
   git clone <your-repo-url>
