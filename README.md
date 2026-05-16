# 🛒 Quick Commerce Sales Analysis Dashboard

An interactive and business-focused **Power BI Dashboard** developed to analyze quickcommerce sales performance, customer behavior, product contribution, store-wise sales trends, and Year-over-Year (YOY) business growth.

This project demonstrates complete Business Intelligence workflow including:

- ETL Process
- Data Cleaning & Transformation
- Data Modeling
- DAX Calculations
- Time Intelligence
- Interactive Dashboard Design
- KPI Reporting
- Business Insights Generation

---

# 📌 Project Objective

The objective of this project is to help businesses monitor and analyze ecommerce performance using interactive visualizations and KPIs.

The dashboard helps stakeholders:

- Track total sales and revenue performance
- Analyze customer purchasing behavior
- Compare current year vs previous year performance
- Identify top contributing products and customers
- Monitor transaction trends
- Analyze location-wise store sales
- Generate business insights for decision making

---

# 🧰 Tools & Technologies Used

| Tool | Purpose |
|---|---|
| Power BI | Dashboard Development |
| Power Query | ETL & Data Transformation |
| DAX | Measures & Calculations |
| Excel / CSV | Data Source |
| Data Modeling | Relationship Management |
| Time Intelligence Functions | YOY Analysis |

---

# 📂 Dataset Structure

The project follows a dimensional data modeling approach.

## Fact Table

- `fact_table`

## Dimension Tables

- `dim_customer`
- `dim_item`
- `dim_store`
- `dim_trans`
- `dim_time`
- `Calendar_table`

---

# ⚙️ ETL Process

The project follows a complete ETL pipeline:

## 1️⃣ Extract
Imported raw ecommerce datasets into Power BI.

## 2️⃣ Transform
Performed data cleaning using Power Query:

- Removed null values
- Corrected data types
- Standardized columns
- Cleaned inconsistent records
- Validated key columns

## 3️⃣ Load
Loaded transformed datasets into Power BI for modeling and analysis.

---

# 🏗️ Data Modeling

The data model contains:

- One Fact Table
- Multiple Dimension Tables

The structure resembles a **Hybrid Star Schema**, because an additional Calendar Table was created for Time Intelligence calculations.

### Relationships Created

| From Table | To Table | Relationship |
|---|---|---|
| dim_customer | fact_table | One-to-Many |
| dim_item | fact_table | One-to-Many |
| dim_store | fact_table | One-to-Many |
| dim_trans | fact_table | One-to-Many |
| dim_time | fact_table | One-to-Many |
| Calendar_table | dim_time | One-to-Many |

---

# 📅 Calendar Table

A dedicated Calendar Table was created to enable:

- SAMEPERIODLASTYEAR()
- YOY Analysis
- Time Intelligence Calculations

```DAX
Calendar_table = 
CALENDAR(
    MIN('dim_time'[order_date]),
    MAX('dim_time'[order_date])
)
```

---

# 📊 Dashboard Features

## ✅ KPI Cards

- Total Sales
- Total Quantity
- Customers
- Avg Unit Price
- Total Orders
- Total Stores

---

## ✅ YOY KPI Analysis

YOY KPIs compare current year performance with previous year performance.

Included KPIs:

- YOY Sales
- YOY Quantity
- YOY Customers
- YOY Avg Price
- YOY Orders
- YOY Stores

### Special Feature

When hovering over YOY KPIs:

- Previous Year KPIs are displayed
- Easy comparison between current year and previous year
- Positive 📈 and Negative 📉 growth indicators

Implemented using **Power BI Tooltip Page**.

---

# 🎛️ Interactive Slicers

The dashboard contains interactive slicers for:

- Year & Quarter
- Order Hour
- Transaction Type
- Store Location Hierarchy

---

# 📈 Visualizations Used

| Visualization | Purpose |
|---|---|
| KPI Cards | Business Performance Tracking |
| Line Chart | Monthly Sales Trend |
| Matrix Table | Customer Contribution Analysis |
| Map Visual | Store Location Sales |
| Bar Chart | Area-wise Sales |
| Donut Chart | Price Bucket Analysis |
| Product Matrix | Product Contribution Analysis |

---

# 🧠 Key Business Insights

Using this dashboard, businesses can:

- Identify top-performing products
- Track yearly growth trends
- Analyze customer contribution
- Monitor regional sales performance
- Compare transaction types
- Detect low-performing areas
- Support data-driven decision making

---

# 🖼️ Dashboard Preview

## Dashboard Image 1

![Dashboard Image 1](Images/image%201.png)

---

## Dashboard Image 2

![Dashboard Image 2](Images/image%202.png)

---

## Dashboard Image 3

![Dashboard Image 3](Images/image%203.png)

---

# 📌 DAX Measures Used

## General KPIs

```DAX
TOTAL SALES = SUM(fact_table[total_price])

TOTAL QUANTITY = SUM(fact_table[quantity])

CUSTOMERS = DISTINCTCOUNT(fact_table[customer_key])

AVG UNIT PRICE = AVERAGE(fact_table[unit_price])

Total Stores = DISTINCTCOUNT(fact_table[store_key])

Total Transactions = COUNTROWS(fact_table)
```

---

## YOY Example Measure

```DAX
% YOY SALES = 
VAR PY = [PY SALES]
VAR A = DIVIDE([TOTAL SALES], PY) - 1
VAR LABEL = FORMAT(A, "#0.0%")

RETURN
IF(
    ISBLANK(PY),
    "NA",
    IF(
        A = 0,
        "0.0%",
        LABEL &
        SWITCH(
            TRUE(),
            A > 0, "📈",
            A < 0, "📉"
        )
    )
)
```

---

# 🚀 Project Highlights

✅ Complete ETL Workflow  
✅ Time Intelligence Analysis  
✅ Hybrid Star Schema Modeling  
✅ Interactive Dashboard Design  
✅ YOY KPI Analysis  
✅ Tooltip Reporting  
✅ Advanced DAX Calculations  
✅ Business Insights Generation  

---

# 📚 Skills Demonstrated

- Power BI
- Power Query
- DAX
- Data Modeling
- Data Visualization
- Business Intelligence
- Time Intelligence
- KPI Reporting
- Dashboard Design

---

# 📌 Conclusion

The Ecommerce Sales Analysis Dashboard transforms raw ecommerce data into meaningful business insights through interactive visualizations and advanced KPI analysis.

This project demonstrates practical implementation of:

- Data Cleaning
- Data Transformation
- Data Modeling
- Time Intelligence
- Interactive Reporting
- Business Analytics

The dashboard helps businesses make data-driven decisions by providing clear visibility into sales performance, customer trends, and operational insights.

---

# 👨‍💻 Author

**Pranay Jha**

If you liked this project, feel free to ⭐ the repository.
