# Zara Sales Analysis Dashboard using Power BI

This project presents a comprehensive sales analysis dashboard for the retail brand Zara. The dashboard was developed using Microsoft Power BI to transform raw transactional data from a CSV file into actionable insights.

## 📊 Live Dashboard

![Zara Sales Dashboard](image.png)
*(Note: Replace `image.png` with the path to your dashboard screenshot in the repository.)*

## 🎯 Project Overview

The primary objective of this project was to analyze Zara's sales data to identify key performance indicators (KPIs), understand customer behavior, evaluate the effectiveness of promotional activities, and assess the overall product portfolio. The final output is an interactive, single-page dashboard designed for strategic decision-making.

## ⚙️ Project Steps

The development process was structured into three main phases:

### 1. Data Loading and Preparation (Power Query)
The process began with connecting to the `zara_columns_fixed.csv` source file. In the Power Query Editor, the following steps were taken to clean and prepare the data for analysis:

* **Column Renaming:** For better readability and business context, columns were renamed:
    * `terms` -> `Sub-Category`
    * `Sales Volume` -> `Units Sold`
    * `section` -> `Gender`
* **Calculated Column:** A new column `Revenue` was created to calculate the total revenue for each transaction. This is a fundamental metric for performance analysis.
    * **Formula:** `Revenue = 'Zara'[Price] * 'Zara'[Units Sold]`

### 2. Data Modeling & DAX Measures
After loading the data into the model, several DAX (Data Analysis Expressions) measures were created to aggregate data and define the core KPIs for the dashboard.

#### Key Measures:
```dax
-- Calculates the sum of all revenue from the 'Revenue' column.
Total Revenue = SUM('Zara'[Revenue])
```
```dax
-- Calculates the total number of products sold.
Total Units Sold = SUM('Zara'[Units Sold])
```
```dax
-- Calculates the average selling price across all products.
Average Price = AVERAGE('Zara'[Price])
```
```dax
-- Counts the number of unique products in the catalog.
Number of Products = DISTINCTCOUNT('Zara'[Product ID])
```
```dax
-- A utility measure to create a transparent background for visuals, enhancing design flexibility.
BG Transparent = "rgba(255, 255, 255, 0)"
```

### 3. Visualization and Dashboard Design
The final step was to design an intuitive and insightful dashboard. The layout is organized into three sections:

* **KPI Cards:** Four cards at the top provide an immediate overview of the main metrics: `Total Revenue`, `Total Units Sold`, `Number of Products`, and `Average Price`.

* **Slicers:** Interactive slicers for `Gender`, `Sub-Category`, and `Promotion` allow users to filter the entire report dynamically.

* **Core Visuals:**
    1.  **Total Revenue by Sub-Category (Clustered Bar Chart):** This visual ranks product categories by their revenue contribution, immediately highlighting the most profitable segments.
    2.  **Total Units Sold by Gender and Promotion (Clustered Column Chart):** This chart compares the sales volume between men's and women's sections and breaks it down by promotional and non-promotional sales, answering key questions about marketing effectiveness.
    3.  **Average Price vs. Total Units Sold (Scatter Plot):** This powerful visual provides a product portfolio analysis, mapping each sub-category based on its price point and sales volume to identify "stars," "cash cows," and other strategic segments.

## 📈 Key Insights from the Dashboard

* **Top Performers:** "Jeans" and "Sweaters" are the highest-grossing product categories, making them central to the business's revenue stream.
* **Brand Strength:** For both men's and women's sections, non-promotional items generate a higher volume of sales, indicating strong brand loyalty and perceived value.
* **Portfolio Balance:** The product mix shows a clear distinction between high-volume, accessibly-priced items (like "Jeans") and higher-priced, lower-volume categories (like "Jackets" and "Shoes"), indicating a balanced portfolio.

## 🛠️ Tools Used

* **Microsoft Power BI:** For data modeling, analysis, and visualization.
* **DAX (Data Analysis Expressions):** For creating custom calculations and measures.
* **Power Query:** For data cleaning and transformation.
