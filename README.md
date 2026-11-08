Power BI Module End Evaluation - Sales & Profit Analytics

A concise Power BI project focused on end-to-end data transformation, DAX modeling, and executive report design using an enterprise sales dataset.

📌 Project Overview

Dataset: SalesData_1000Rows_WithIssues_copy.csv

Objective: Clean messy source data, calculate key business metrics using DAX, and construct an interactive dashboard displaying regional distribution, product trends, and profit performance over time.

Tool: Microsoft Power BI Desktop & Power Query Editor

🛠️ Step-by-Step Implementation

Q1: Data Cleaning & Loading (Power Query)

Header Promotion: Promoted the top row to column headers to resolve text-parsing type errors.

Missing Values Handling:

Text fields (CustomerName, Region, Product): Replaced blank/null values with "Unknown".

Date & Numeric fields: Filtered out invalid null rows and standardized empty metrics.

Deduplication: Applied Remove Duplicates on OrderID to guarantee unique transactions.

Date Standardization: Converted OrderDate to Date type using the en-IN / en-GB (DD-MM-YYYY) locale.

Applied Changes: Selected Close & Apply to load the clean table into the model.

Q2: Visualizations & Analytics

a) Regional Order Distribution: Pie/Donut Chart showing order split across East, South, West, and North territories.

b) Top 5 Trending Products: Clustered Column Chart filtered using Top N = 5 by Count of OrderID (led by Monitors, Laptops, and Bookshelves).

c) Profit Trend Over Time: Continuous Line / Area Chart tracking Sum of Profit across order years to identify profitability peaks.

Q3: DAX Calculations

1. Calculated Table: EastRegionOrders

Filters and isolates all transactions originating from the East sales territory:

EastRegionOrders = 
FILTER(
    SalesData,
    SalesData[Region] = "East"
)


2. Calculated Column: ProfitCostDifference

Computes the net variance between profit and cost for each line item:

ProfitCostDifference = SalesData[Profit] - SalesData[Cost]


3. Calculated Measure: TotalProfit

Aggregates total business profit for use across visuals and KPI cards:

TotalProfit = SUM(SalesData[Profit])
