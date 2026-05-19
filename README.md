# 📊 Power BI — Superstore Sales Dashboard
## 📌 Project Overview

This project is an end-to-end **Business Intelligence Dashboard** built using **Power BI Desktop**.  
The goal was to analyze Superstore Sales data and extract meaningful business insights that help decision-makers understand sales performance, profitability, and customer behavior across different regions and product categories.

---

## 🎯 Business Objectives

- Track overall **Sales, Profit, and Order trends**
- Identify **top-performing products and regions**
- Detect **loss-making sub-categories** despite high sales
- Analyze **Year-over-Year (YOY) growth**
- Understand **customer segments and shipping behavior**

---

## 📂 Dataset Details

| Field | Details |
|---|---|
| **Dataset Name** | Sample Superstore Sales Dataset |
| **Source** | Kaggle |
| **Author** | Vivek Chouhan |
| **Records** | ~10,000 rows |
| **Format** | CSV |
| **Link** | [Kaggle Dataset](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final) |

---

## 🛠️ Tools & Technologies Used

| Tool | Purpose |
|---|---|
| **Power BI Desktop** | Dashboard Development |
| **Power Query Editor** | Data Cleaning & Transformation |
| **DAX (Data Analysis Expressions)** | Calculated Measures & KPIs |
| **Data Modeling** | Table Relationships & Date Table |
| **Kaggle** | Data Source |

---

## ⚙️ Data Preparation Steps

### Power Query Transformations:
- Changed **Order Date** and **Ship Date** to correct Date format
- Changed **Sales, Profit, Discount** to Decimal Number
- Changed **Quantity** to Whole Number
- Removed null values from key columns
- Created custom **Delivery Days** column:
```
= [Ship Date] - [Order Date]
```

### Data Modeling:
- Created a **Custom Date Table** using DAX:
```dax
DateTable = CALENDAR(MIN('Sample - Superstore'[Order Date]), MAX('Sample - Superstore'[Order Date]))
```
- Added **Year, Month, MonthNo, Quarter** columns to Date Table
- Created **Active Relationship** between DateTable[Date] and Orders[Order Date]

---

## 📐 DAX Measures Created

```dax
Total Sales = SUM('Sample - Superstore'[Sales])

Total Profit = SUM('Sample - Superstore'[Profit])

Total Orders = DISTINCTCOUNT('Sample - Superstore'[Order ID])

Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0) * 100

Avg Discount = AVERAGE('Sample - Superstore'[Discount])

Total Quantity = SUM('Sample - Superstore'[Quantity])

YOY Sales Growth =
DIVIDE(
    [Total Sales] - CALCULATE([Total Sales], SAMEPERIODLASTYEAR(DateTable[Date])),
    CALCULATE([Total Sales], SAMEPERIODLASTYEAR(DateTable[Date])),
    0
) * 100
```

---

## 📊 Dashboard Pages

### Page 1 — Executive Summary
- KPI Cards: Total Sales, Total Profit, Profit Margin %, Total Orders
- Line Chart: Monthly Sales Trend
- Bar Chart: Sales by Region
- Donut Chart: Sales by Customer Segment

### Page 2 — Product Analysis
- Bar Chart: Top 10 Products by Sales
- Tree Map: Sales by Category & Sub-Category
- Scatter Plot: Sales vs Profit by Sub-Category
- Table: Sub-Category Performance with Conditional Formatting

## 💡 Key Business Insights

- 📈 **Technology** category generates the **highest profit margin**
- 🌍 **West Region** leads in overall sales performance
- ⚠️ **Tables and Bookcases** sub-categories show **negative profit** despite decent sales
- 🚚 **Standard Class** is the most frequently used shipping mode
- 👥 **Consumer segment** contributes the most to total revenue
- 📅 **Sales peak** during Q4 (October - December) every year

---

## 📁 Repository Structure

```
Superstore-Sales-Dashboard/
│
├── 📊 Superstore-Sales-Dashboard.pbix   ← Power BI Project File
├── 📄 README.md                          ← Project Documentation
├── 📁 Screenshots/                       ← Dashboard Screenshots
│   ├── 01_Executive_Summary.png
│   ├── 02_Product_Analysis.png
└── 📁 Dataset/
    └── Sample-Superstore.csv             ← Raw Data File
```

## 🚀 How to Open This Project

1. Download and install **Power BI Desktop** (Free) from [here](https://powerbi.microsoft.com/desktop)
2. Clone or download this repository
3. Open the file: `Superstore-Sales-Dashboard.pbix`
4. Explore 2 dashboard pages!

---

## 👨‍💻 About Me

I am a passionate **Data Analyst** with expertise in:
- Power BI Dashboard Development
- DAX & Data Modeling
- Data Cleaning & Transformation
- Business Intelligence & Reporting
- Excel, SQL, Python for Data Analysis

📧 **Open to work** — Currently looking for **Data Analyst opportunities in Saudi Arabia & GCC Region**

---

## 🔗 Connect With Me

1-https://github.com/Kashif95435
2-https://www.linkedin.com/in/kashif-data-science/

⭐ **If you find this project helpful, please give it a Star!** ⭐
