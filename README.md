# 📊 StorePulse — Sales Analytics Dashboard

> A full end-to-end Power BI dashboard built on the Superstore Sales dataset, transforming 9,800+ orders into actionable retail business insights.

---

## 🖼️ Dashboard Preview

<img width="1259" height="797" alt="image" src="https://github.com/user-attachments/assets/fd71e480-fc66-44ff-8f11-103589f089f8" />


---

## 📁 Project Structure

```
StorePulse-Sales-Analytics/
│
├── README.md
├── StorePulse.pbix              ← Power BI dashboard file
├── dataset/
│   └── superstore_sales.csv     ← Raw dataset
└── screenshots/
    ├── dashboard_overview.png
    ├── gauge_visual.png
    └── category_breakdown.png
```

---

## 🎯 Project Overview

StorePulse is a sales analytics dashboard that gives business stakeholders a complete view of retail performance across regions, categories, customer segments, and time — all in one page.

**Dataset:** Superstore Sales
**Tool:** Microsoft Power BI Desktop
**Skills applied:** Power Query · DAX · Data Modeling · Dashboard Design

---

## 🔢 Dataset Summary

| Metric | Value |
|---|---|
| Total Orders | ~9,800 |
| Total Sales | $2.26M |
| Unique Customers | 793 |
| Unique Products | 1,861 |
| Categories | 3 (Technology, Furniture, Office Supplies) |
| Sub-Categories | 17 |
| Regions | 4 (West, East, Central, South) |
| Date Range | 2015 – 2018 |

---

## ⚙️ Power Query — Data Transformation

All transformations were done in Power Query before loading data into the model:

| Step | Description |
|---|---|
| Fix date types | Converted `Order Date` and `Ship Date` from text to Date format |
| Delivery Days | Custom column: `Ship Date - Order Date` |
| Delivery Speed Tier | Conditional: Fast (< 3 days) · Normal (3–5 days) · Slow (5+ days) |
| Sales Tier | Conditional: Small (< $100) · Medium ($100–$500) · Large ($500+) |
| Remove nulls | Filtered out 11 rows with missing Postal Code values |
| Text cleanup | Trimmed whitespace from Customer Name and Product Name columns |

---

## 📐 DAX Measures

```dax
Total Sales = SUM(train[Sales])

Total Orders = COUNTROWS(train)

Avg Order Value = DIVIDE([Total Sales], [Total Orders])

Avg Delivery Days = AVERAGE(train[Delivery Days])

% of Total Sales =
DIVIDE([Total Sales],
    CALCULATE([Total Sales], ALL(train)))

Top Customer =
CONCATENATEX(
    TOPN(1, VALUES(train[Customer Name]),
        [Total Sales], DESC),
    train[Customer Name])

Top Region =
CONCATENATEX(
    TOPN(1, VALUES(train[Region]),
        [Total Sales], DESC),
    train[Region])



```



## 💡 Key Insights

- Technology leads at $827K (36.6% of total sales)
- Phones & Chairs are the top performing sub-categories
- Sales grew consistently from 2015 to 2018, peaking at $0.7M
- Standard Class dominates shipments at ~6,000 orders
- Sales Pulse Gauge shows $2.26M against a $3M maximum — 75% of target


## 🛠️ Tools & Technologies

- **Microsoft Power BI Desktop**
- **Power Query (M Language)** — for ETL and data transformation
- **DAX (Data Analysis Expressions)** — for calculated measures
- **Superstore Sales Dataset** — publicly available retail dataset

---

## 👤 Author

**Habiba Mohamed**
[LinkedIn Profile](https://www.linkedin.com/in/habiba-mohamed-340992273/) 
