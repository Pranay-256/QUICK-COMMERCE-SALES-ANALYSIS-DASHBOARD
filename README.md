# 🛒 Prime Mart Sales and Customer Analysis Dashboard

An interactive and business-focused **Power BI Dashboard** developed to analyze Prime Mart's retail sales performance, customer retention and churn behavior, product contribution, store-wise sales trends, and Year-over-Year (YOY) business growth.

This project demonstrates complete Business Intelligence workflow including:

- ETL Process
- Data Cleaning & Transformation
- Data Modeling
- DAX Calculations
- Time Intelligence & Month Intelligence
- Customer Retention & Churn Analysis
- Interactive Dashboard Design
- KPI Reporting
- Stakeholder Meeting Simulation & Business Insights Generation

---

# 🏢 What We Did for the Business

As part of this project, a full **stakeholder meeting simulation** was conducted where Claude AI acted as a Prime Mart stakeholder and asked live, unscripted questions based on the dashboard. I  answered each question by deeply analysing the data in real time like a business analyst — uncovering insights that were not pre-prepared.

### Key Business Findings Delivered:

- 📦 **Supply Chain Risk Identified** — A January 2025 sales campaign caused product stock depletion, resulting in a **-32.1% quantity drop** and **-25.7% order drop** in February. The root cause was traced to aggressive monthly targets exceeding supplier capacity.

- 🔄 **Customer Retention Crisis Flagged** — With a **62.05% churn rate** in 2025, it was found that 1,250 out of 2,010 previous year customers were lost. The February stockout was identified as the primary driver of permanent customer switching.

- 📍 **Narendra Nagar Geographical Insight** — The top revenue store (+93.4% YOY growth) was discovered to be a **trekking supply stop** in Uttarakhand, not a standard retail location. Its 100% churn is natural due to the transient customer base. Word-of-mouth was identified as its only marketing channel.

- ⭐ **Premium Dominance Confirmed** — Premium and High-Priced categories together contribute **64% of total revenue**, while Budget products contribute only 4% and dilute brand image.

- 💡 **7-Point Strategic Action Plan Delivered** — Covering loyalty programs, supply chain stabilisation, premium product focus, new customer offers, sustainable marketing, NPS tracking, and steady monthly revenue targeting.

---

# 📌 Project Objective

The objective of this project is to help businesses monitor and analyze retail performance using interactive visualizations and KPIs.

The dashboard helps stakeholders:

- Track total sales and revenue performance
- Analyze customer purchasing behavior
- Compare current year vs previous year performance
- Identify top contributing products and customers
- Monitor transaction trends
- Analyze location-wise store sales
- Track customer retention and churn rates
- Segment customers into New and Returning groups
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
| Time Intelligence Functions | YOY & MOM Analysis |

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
Imported raw retail datasets into Power BI.

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

# 📊 Dashboard Pages

## Page 1 — Sales Performance Analysis

## Page 2 — Customer Retention and Churn Analysis

---

# ✅ KPI Cards

### Sales Performance Page
- Total Sales
- Total Quantity
- Customers
- Avg Revenue Per Customer
- Total Orders
- Total Stores

### Customer Retention Page
- New Customers
- Returning Customers
- Customer Retention Rate %
- Customer Churn Rate %
- New Customers Revenue
- Returning Customers Revenue
- Avg Revenue by New Customer
- Avg Revenue by Returning Customer

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
| Bar Chart | Area-wise Sales & Store Rankings |
| Donut Chart | Price Bucket Analysis & New vs Returning Revenue |
| Clustered Bar Chart | New vs Returning Customers Yearly Trend |
| Area Line Chart | New vs Returning Customers Monthly Trend |
| Funnel Visual | Customer Retention Funnel |

---

# 🧠 Key Business Insights

Using this dashboard, businesses can:

- Identify top-performing products
- Track yearly growth trends
- Analyze customer contribution
- Monitor regional sales performance
- Compare transaction types
- Detect low-performing areas
- Track customer retention and churn rates
- Identify revenue from new vs returning customers
- Support data-driven decision making

---

# 🖼️ Dashboard Preview

## Sales Performance Analysis

![Dashboard Image 1](Images/image%201.png)

---

## Customer Retention and Churn Analysis

![Dashboard Image 2](Images/image%202.png)

---

# 📌 DAX Measures Used

## General KPIs

```DAX
TOTAL SALES              = SUM(fact_table[total_price])
TOTAL QUANTITY           = SUM(fact_table[quantity])
CUSTOMERS                = DISTINCTCOUNT(fact_table[customer_key])
AVG UNIT PRICE           = AVERAGE(fact_table[unit_price])
Total Stores             = DISTINCTCOUNT(fact_table[store_key])
Total Transactions       = COUNTROWS(fact_table)
AVG REVENUE PER CUSTOMER = DIVIDE([TOTAL SALES], [CUSTOMERS], 0)
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

## New vs Returning Customers Example Measure

```DAX
NEW CUSTOMERS = 
VAR currentyear      = SELECTEDVALUE(dim_time[Year])
VAR prevyear         = currentyear - 1
VAR currentcustomers = CALCULATETABLE(VALUES(fact_table[customer_key]), dim_time[year] = currentyear)
VAR prevcustomers    = CALCULATETABLE(VALUES(fact_table[customer_key]), ALL(dim_time), dim_time[year] = prevyear)
RETURN
IF(ISBLANK(prevyear), "NA",
    COUNTROWS(EXCEPT(currentcustomers, prevcustomers)))
```

---

## Customer Retention Rate

```DAX
CUSTOMER RETENTION RATE % = 
VAR prevyear          = SELECTEDVALUE(dim_time[year]) - 1
VAR lastyearcustomers = CALCULATE(DISTINCTCOUNT(fact_table[customer_key]), ALL(dim_time), dim_time[year] = prevyear)
VAR RC                = [RETURNING CUSTOMERS]
VAR RR                = DIVIDE(RC, lastyearcustomers, 0)
RETURN RR
```

---

# 🚀 Project Highlights

✅ Complete ETL Workflow  
✅ Time Intelligence & Month Intelligence Analysis  
✅ Hybrid Star Schema Modeling  
✅ Interactive Dual-Page Dashboard Design  
✅ YOY & MOM KPI Analysis  
✅ Tooltip Reporting  
✅ Advanced DAX Calculations  
✅ Customer Retention & Churn Analysis  
✅ New vs Returning Customer Segmentation  
✅ Stakeholder Meeting Simulation  
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
- Customer Retention Analytics
- KPI Reporting
- Dashboard Design
- Business Storytelling

---

# ⚠️ Disclaimer

The name **Prime Mart** used in this project is entirely fictional and has been chosen solely to give the project a realistic, business-like identity. It does not target, represent, or intend any resemblance to any real business, brand, or organization. All datasets used are completely imaginary and do not reflect the actual operations or financials of any real company. This project was created purely for **educational and portfolio purposes**.

---

# 📌 Conclusion

The Prime Mart Sales and Customer Analysis Dashboard transforms raw retail data into meaningful business insights through interactive visualizations, advanced KPI analysis, and real-world stakeholder simulation.

This project demonstrates practical implementation of:

- Data Cleaning & Transformation
- Data Modeling
- Time Intelligence & Month Intelligence
- Customer Retention & Churn Analysis
- Interactive Reporting
- Business Analytics & Stakeholder Communication

The dashboard helps businesses make data-driven decisions by providing clear visibility into sales performance, customer trends, retention health, and operational insights.

---

# 👨‍💻 Author

**Pranay Jha**

If you liked this project, feel free to ⭐ the repository.
