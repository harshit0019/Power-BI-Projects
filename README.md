# 📊 Power BI Projects

This repository is a collection of Power BI dashboards and reports built across various domains. Each project highlights data-driven insights through interactive visualizations and storytelling.

---

## 📁 Contents

- `.pbix` files for each project
- `images/` — place project screenshot images here (recommended size: 1280×720)

---

## 🔍 Projects Showcase

Some of the projects in this repository include:

1. **Amazon Sales Dashboard** – Visualizing regional sales trends, seller performance, product category breakdowns, and seasonality. *(Shows advanced visualizing & dashboarding skills.)*  
   ![Amazon Sales Dashboard Placeholder](images/amazon_sales_dashboard.png)

2. **Car Sales Dashboard** – Analyzing revenue, profit margins, expense categories, dealer performance, and time-series forecasting. *(Shows advanced visualizing & dashboarding skills.)*  
   ![Car Sales Dashboard Placeholder](images/car_sales_dashboard.png)

3. **Customer Churn Analysis** – Exploratory Data Analysis (EDA) and Power BI reporting to identify drivers of churn, segment high-risk customers, and visualize cohort retention. Includes churn-rate trendlines, survival curves, and feature-impact KPI cards.  
   *EDA performed using pandas, numpy, seaborn, matplotlib; insights translated to Power BI using calculated columns, measures (DAX), and drill-through pages.*  
   ![Customer Churn Analysis Placeholder](images/customer_churn_analysis.png)

4. **Banking Risk Analysis** – End-to-end risk analytics dashboard: credit risk scoring visualization, distribution of risk bands, stress-test results, and portfolio concentration maps. EDA and feature engineering were done in Python before building interactive Power BI visuals.  
   *Highlights data cleansing, feature correlation analysis, and risk-summary KPIs.*  
   ![Banking Risk Analysis Placeholder](images/banking_risk_analysis.png)

5. **End-to-End Sales Analysis** – Complete pipeline from raw transactions to executive dashboards: ETL with Power Query, EDA and aggregation in Python, advanced DAX measures for rolling metrics, and cross-filterable visual stories for sales, margins, returns, and channels.  
   *Shows both data engineering and dashboard storytelling skills.*  
   ![End to End Sales Analysis Placeholder](images/end_to_end_sales_analysis.png)

---

## 💡 Features

- Clean and interactive dashboard designs
- Advanced DAX measures and KPIs
- Use of slicers, filters, and drill-through pages
- Time-series and geographical visualizations
- Custom themes and visuals
- EDA & preprocessing done with Python (pandas, numpy, seaborn, matplotlib) before importing to Power BI

---

## 🛠️ Tools & Technologies

- Microsoft Power BI Desktop (.pbix)
- Python (pandas, numpy, seaborn, matplotlib) for EDA and preprocessing
- DAX (Data Analysis Expressions)
- Power Query (M Language)
- External data sources (Excel, CSV, APIs)

---

## 🔬 Analysis / EDA (example workflow)

I start each project by exploring and cleaning the data with Python — this demonstrates my data-analysis skills before producing the dashboard in Power BI.

Example EDA snippet (clean, reproducible):

```python
# example_eda.py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# load
df = pd.read_csv("data/sales_data.csv", parse_dates=["order_date"])

# quick overview
print(df.info())
print(df.describe(include="all"))

# basic cleaning
df = df.dropna(subset=["order_id", "customer_id"])  # remove bad rows
df["revenue"] = pd.to_numeric(df["revenue"], errors="coerce").fillna(0)

# feature engineering
df["year"] = df["order_date"].dt.year
df["month"] = df["order_date"].dt.to_period("M")

# aggregation example
monthly = df.groupby("month").agg(
    total_revenue=pd.NamedAgg(column="revenue", aggfunc="sum"),
    orders=pd.NamedAgg(column="order_id", aggfunc="nunique")
).reset_index()

# quick viz
plt.figure(figsize=(10, 4))
plt.plot(monthly["month"].astype(str), monthly["total_revenue"])
plt.title("Monthly Revenue")
plt.xlabel("Month")
plt.ylabel("Revenue")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
