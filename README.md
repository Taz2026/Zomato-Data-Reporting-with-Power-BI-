### Zomato Data Reporting with Power BI

A comprehensive, multi-page business intelligence report delivering deep performance insights across global restaurant data - analysed by Location, Cost, Ratings, and Cuisines.

📌 Project Overview

This project delivers an end-to-end business intelligence solution built on the Zomato restaurant dataset, transforming raw data into actionable insights through a fully interactive Power BI dashboard. The report empowers stakeholders and data enthusiasts to explore restaurant performance metrics across cities, cuisine categories, pricing tiers, and customer engagement levels.
This dashboard uses Power Query for data transformation, a structured data model, and optimized DAX measures to provide a comprehensive analytical framework for the food & hospitality domain. The solution is designed to reflect real-world BI development standards - from raw data ingestion through to polished, executive-ready reporting.

🎯 Business Objectives

* Identify top-performing cities and restaurants by rating, votes, and average cost.
* Analyze the correlation between the average cost for two and customer ratings.
* Determine the most popular cuisine types by city and overall market share.
* Compare online ordering vs. offline order volumes and their impact on ratings.
* Evaluate the influence of table booking availability on restaurant performance.
* Segment restaurants into cost categories (Budget, Mid-Range, Premium) for pricing analysis.
* Track voting trends as a proxy for customer engagement and restaurant visibility.

🛠️ Tech Stack & Tools

| Tool / Technology | Purpose |
| :--- | :--- |
| **Power BI Desktop** | Dashboard development & report publishing |
| **DAX (Data Analysis Expressions)** | Custom measures, KPIs, and calculated columns |
| **Power Query (M Language)** | Data ingestion, transformation, and cleansing |
| **CSV / Excel** | Source data format |
| **GitHub** | Version control and project collaboration |

📂 Dataset Description

**Source**: Zomato Dataset — Kaggle

| Column Name | Description |
| :--- | :--- |
| `Restaurant Name` | Name of the restaurant |
| `City` | City where the restaurant is located |
| `Cuisines` | Types of cuisine offered (comma-separated) |
| `Average Cost for Two` | Approximate dining cost for two people (INR) |
| `Currency` | Currency of the cost value |
| `Has Online Delivery` | Whether online delivery is available (Yes/No) |
| `Has Table Booking` | Whether table reservation is supported (Yes/No) |
| `Aggregate Rating` | Overall customer rating (0-5 scale) |
| `Rating Text` | Categorical rating label (e.g., Excellent, Good, Average) |
| `Votes` | Total number of customer votes/reviews |
| `Locality` | Neighbourhood or locality within the city |
| `Country Code` | Numeric country identifier |

⚙️ Data Transformation & Modeling

**Power Query (ETL Steps)**

1. **Data Import** — Loaded CSV files into Power Query Editor
2. **Null Handling** — Removed or replaced null values in `Cuisines`, `Rating`, and `Votes` columns
3. **Data Type Correction** — Cast `Aggregate Rating` to Decimal, `Votes` to Whole Number, and `Average Cost for Two` to Currency
4. **Column Renaming** — Renamed raw column headers to business-friendly labels
5. **Cuisine Splitting** — Used `Split Column by Delimiter` to extract the primary cuisine type for each restaurant
6. **Cost Category Column** — Added a conditional column to classify restaurants as Budget (< £500), Mid-Range (£500–£1500), or Premium (> £1500)
7. **Rating Band Column** — Grouped ratings into bands: Poor (< 2.5), Average (2.5–3.4), Good (3.5–3.9), Very Good (4.0–4.4), Excellent (≥ 4.5)
8. **Country Lookup Table** — Created a reference table mapping `Country Code` to `Country Name`.

**Data Model**

The model follows a **Star Schema** design:

* **Fact Table**: `Restaurants` — contains transactional and performance metrics
* **Dimension Tables**: `dim_City` , `dim_Cuisine` , `dim_Country` , `dim_CostCategory`
* Relationships are single-directional, with referential integrity enforced
* A dedicated _`Measures` table houses all DAX calculations for a clean model organisation

📐 DAX Measures & Calculations

| Measure Name | Description |
| :--- | :--- |
| `Total Restaurants` | `COUNTROWS(Restaurants)` — Total count of restaurants in the filtered context |
| `Average Rating` | `AVERAGE(Restaurants[Aggregate Rating])` — Mean rating across selected filters |
| `Total Votes` | `SUM(Restaurants[Votes])` — Aggregate customer engagement metric |
| `% Online Delivery` | Percentage of restaurants offering online delivery |
| `% Table Booking` | Percentage of restaurants with table reservation capability |
| `Avg Cost for Two` | `AVERAGE(Restaurants[Average Cost for Two])` — Mean dining cost |
| `Top Cuisine by Votes` | Identifies the cuisine with the highest vote share using `TOPN` + `RANKX` |
| `Rating vs Cost Correlation` | Calculated column comparing cost tier against rating band for scatter analysis |

📊 Dashboard Features & Visuals

**Report Pages**

1. 🏠 Executive Overview

* **KPI Cards**: Total Restaurants, Average Rating, Total Votes, Average Cost for Two
* **Donut Chart**: Online Delivery vs. Dine-in split
* **Bar Chart**: Top 10 Cities by Restaurant Count
* **Slicers**: City, Cuisine Type, Rating Band, Cost Category

2. 🌆 City-Level Analysis

* **Map Visual**: Restaurant density by city (bubble size = vote count)
* **Column Chart**: Average Rating by City
* **Matrix Table**: City vs. Cuisine cross-tabulation with conditional formatting
* **Drill-through**: Navigate from city to individual restaurant details

3. 🍜 Cuisine Breakdown

* **Horizontal Bar Chart**: Top 15 Cuisines by Total Votes
* **Treemap**: Cuisine market share by restaurant count
* **Line & Clustered Column**: Average Cost vs. Average Rating by Cuisine

4. 💰 Pricing & Ratings Deep Dive

* **Scatter Chart**: Average Cost for Two vs. Aggregate Rating
* **Funnel Chart**: Restaurant count by Rating Text category
* **Card Visuals**: Budget, Mid-Range, and Premium segment KPIs

💡 Key Insights & Findings

* 🏙️ **Mumbai, Delhi, and Bangalore** account for over 60% of all restaurants in the dataset, with Delhi having the highest average votes per restaurant.
* 🍛 **North Indian** cuisine is the most prevalent across metro cities, appearing in over 35% of restaurant menus.
* ⭐ Restaurants with **online delivery** enabled have, on average, **22% more votes** than offline-only restaurants.
* 💸 **Mid-range restaurants** (£500–£1500) consistently outperform the Budget and Premium tiers in aggregate ratings, suggesting the best perceived value.
* 📋 Only **12% of restaurants** offer table booking, yet they carry an average rating **0.4 points higher** than those without.
* 🌟 The **Excellent** rating band (≥ 4.5) accounts for just 8% of all restaurants, concentrated heavily in Premium cost categories.

🗂️ Project Structure

```text
Zomato-Data-Reporting-with-Power-BI/
├── dataset/
│   ├── zomato.csv
│   └── Country-Code.xlsx
├── screenshots/
│   ├── 01_executive_overview.png
│   ├── 02_city_analysis.png
│   └── 03_cuisine_breakdown.png
├── Zomato_Data_Report.pbix
└── README.md





















