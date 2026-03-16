# 🛒 E-Commerce Sales Dashboard

A Power BI dashboard analyzing U.S. e-commerce sales performance across **FY 2021–2022**, built with DAX, Power Query, and interactive visualizations.

---

## 📊 Overview

| Metric | Value |
|---|---|
| 💰 Total Sales | $23.16 Million |
| 📈 Total Profit | $2.61 Million |
| 🧾 Profit Margin | 11.3% |
| 📦 Total Orders | 113,270 |
| 👥 Unique Customers | 42,047 |
| 🗺️ States Covered | 49 U.S. States |
| 📅 Period | Jan 2021 – Dec 2022 |

---

## 📁 Files in This Repository

```
├── ECOMMERCE_SALES_DASHBOARD.pbix     # Power BI dashboard file
├── ecommerce_data.csv                 # Main transactional dataset (113K rows)
├── ecommerce_data_excel.xlsx          # Excel version of the dataset
├── us_state_long_lat_codes.csv        # State lat/long for map visuals
├── Final_Back.jpg                     # Dashboard background image
└── IMPORTANT_POINT_TO_NOTE.docx       # Setup notes for Power BI import
```

---

## 🗂️ Dataset Columns

| Column | Description |
|---|---|
| `customer_id` | Unique customer identifier |
| `category_name` | Product category (Office Supplies, Furniture, Technology) |
| `customer_segment` | Consumer / Corporate / Home Office |
| `customer_state / region` | Geographic location |
| `order_date` | Date of order placement |
| `delivery_status` | On time / Late / Advance / Canceled |
| `shipping_type` | Standard / Second / First / Same Day |
| `sales_per_order` | Revenue per order |
| `profit_per_order` | Profit per order |
| `order_quantity` | Units ordered |

---

## ⚙️ Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/ecommerce-sales-dashboard.git
cd ecommerce-sales-dashboard
```

### 2. Open in Power BI
- Open `ECOMMERCE_SALES_DASHBOARD.pbix` in **Power BI Desktop**
- If prompted, update the data source path to your local folder

### 3. Important Notes ⚠️
> From `IMPORTANT_POINT_TO_NOTE.docx`:
- Make sure the `order_date` field has the data type set to **Date** in Power BI
- Verify that **all dates are fully imported** in both SQL and Power BI before refreshing

### 4. Refresh Data
- Go to **Home → Refresh** to load the latest data

---

## 🧮 DAX Measures

```dax
Total Sales = SUM(ecommerce_data[sales_per_order])

Total Profit = SUM(ecommerce_data[profit_per_order])

Profit Margin = DIVIDE([Total Profit], [Total Sales], 0)

Total Orders = COUNTROWS(ecommerce_data)
```

### Date Table
```dax
DateTable =
ADDCOLUMNS(
    CALENDAR(DATE(2021, 1, 1), DATE(2022, 12, 31)),
    "Year",    YEAR([Date]),
    "Month",   FORMAT([Date], "MMMM"),
    "Quarter", "Q" & ROUNDUP(MONTH([Date]) / 3, 0)
)
```
> Mark this table as a **Date Table** via Table Tools → Mark as Date Table

---

## 📈 Key Insights

- 🥇 **Office Supplies** is the top category — $13.9M (60% of revenue)
- 🌍 **West region** leads geographically at $7.4M
- 🏆 **California** is the #1 state with $4.65M in sales
- 👤 **Consumer segment** drives 51.8% of all revenue
- ⚠️ **54.8% of orders had late delivery** — the biggest operational issue
- 📅 **October 2022** was the strongest month at $1.11M

---

## 🗺️ Dashboard Visuals

- KPI Cards — Sales, Profit, Margin, Orders
- Bar Chart — Sales by Category
- Donut Chart — Customer Segment split
- Map Visual — Revenue by U.S. State
- Line Chart — Monthly Sales Trend (2021 vs 2022)
- Delivery Status Breakdown
- Slicers — Year, Region, Category, Segment

---

## 🛠️ Tech Stack

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=flat&logo=microsoft&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-217346?style=flat&logo=microsoftexcel&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=mysql&logoColor=white)

---

## 📄 License

This project is for educational and portfolio purposes.
