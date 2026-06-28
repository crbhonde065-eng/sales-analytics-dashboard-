# sales-analytics-dashboard
Interactive sales data analytics platform tracking regional KPIs, growth trends, and pipeline metrics.

# 📊 Sales Analytics Dashboard (FY 2025)

A high-performance, responsive, dark-themed **Sales Analytics Dashboard** built for tracking **India Operations** across multiple regions, categories, and sales representatives. This dashboard replicates the analytical capacity of enterprise Power BI architectures using a lightweight, native web stack backed by a pre-computed data engineering pipeline.

---

## 🚀 Live Features

* **Slicer / Filter Simulation:** Dynamic filtering across 5 core dimensions: Month, Category, Region, Sales Representative, and City.
* **KPI Scorecards:** Top-level metrics calculating Total Revenue, Total Profit, Profit Margin %, Total Orders, and Units Sold dynamically.
* **Deep-Dive Visualization Matrix:**
    * *Monthly Revenue by Category:* Stacked Bar chart tracking continuous performance.
    * *Revenue vs Profit Trend:* Line chart assessing margin health over time.
    * *Category Mix & Payment Methods:* High-fidelity breakdown via interactive Donut/Doughnut charts.
    * *Geographic & Product Tracking:* Sorted cross-filtering horizontal bar charts.
    * *Sales Rep Leaderboard:* Visual progress bars mapping ranking, volume, and individual margins.
* **Granular Transaction Log:** Interactive ledger revealing real-time table modifications based on user criteria.

---

## 🛠️ Data Pipeline & Architecture

To populate the pre-computed telemetry (`const FULL`) inside the application, an end-to-end data processing workflow was implemented from raw corporate transactional records.
### 1. Excel Prototyping & Formula Verification
Before scaling data into code, initial mockups, baseline verification, and logical sanity checks were calculated in Excel using complex matrix formulas:
* **Average Order Value Baseline:**
  ```excel
  =SUM(G2:G1288) / COUNTA(A2:A1288)
  =SUMIFS(Sales_Amount, Category_Range, "Electronics", Region_Range, "South")
  =IFERROR((Profit_Amount / Sales_Amount), 0)
  SQL
  SELECT 
    DATE_FORMAT(order_date, '%Y-%m') AS month_key,
    category,
    SUM(units_sold * unit_price) AS raw_sales,
    SUM(sales_amount) AS final_revenue,
    SUM(profit) AS net_profit,
    COUNT(DISTINCT order_id) AS total_orders
FROM sales_master
WHERE FY = '2025'
GROUP BY 1, 2
ORDER BY 1 ASC;
Python
import pandas as pd
import json

df = pd.read_csv("sales_data_2025.csv")

# Pre-aggregating high-performance data structures for ChartJS
full_aggregates = {
    "totalSales": float(df["sales"].sum()),
    "totalProfit": float(df["profit"].sum()),
    "totalOrders": int(df["o"].nunique()),
    "category": {
        "labels": df.groupby("cat")["sales"].sum().index.tolist(),
        "sales": df.groupby("cat")["sales"].sum().values.tolist(),
        "profit": df.groupby("cat")["profit"].sum().values.tolist()
    }
}
print(json.dumps(full_aggregates, indent=2))

