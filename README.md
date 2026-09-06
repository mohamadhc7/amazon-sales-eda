# Amazon Sales EDA (India)

## Overview
Exploratory data analysis of an Amazon India sales dataset, covering data cleaning, visualization, and business insights on shipping patterns, product categories, and regional order distribution.

## Objective
Understand how orders break down by shipping service level, product category, state, and city — and turn those patterns into actionable business recommendations.

## Dataset
- **Source:** [Amazon Sale Report (Kaggle)](https://www.kaggle.com/datasets/thedevastator/unlock-profits-with-e-commerce-sales-data)
- **Rows:** ~128,975 orders (128,942 after cleaning)
- **Time period:** March 31, 2022 – June 29, 2022 (about 3 months)
- **Row representation:** Each row is a unique Amazon order, including shipping destination (state, city), delivery type (Standard/Expedited), and product category.
- **Limitations:** Covers a single country (India) and single platform (Amazon). No cost, pricing margin, or delivery-time data is included — conclusions are limited to order volume and category patterns, not profitability or delivery performance.

## Tools
- Python
- pandas
- matplotlib
- Jupyter Notebook

## Methodology
1. Loaded the raw CSV and inspected structure (`.info()`, `.describe()`, `.dtypes`, `.nunique()`)
2. Cleaned inconsistent categorical data (see Data Cleaning below)
3. Grouped and counted orders across four dimensions: shipping service level, category, state, and city
4. Visualized each as a bar chart
5. Interpreted results into findings and business recommendations

## Data Cleaning

**Ship-state:**
- Casing issue: State names were inconsistently formatted (mix of uppercase and lowercase), so the entire column was converted to uppercase for consistency.
- Misspelling: "RAJSTHAN" was misspelled instead of "RAJASTHAN" — replaced with the correct spelling.
- Duplicate naming: "NEW DELHI" was being counted separately from "DELHI" — merged into "DELHI" for a more accurate count.
- Missing values: 33 rows had no ship-state value — dropped, as they were a small fraction of the dataset.

**Ship-city:**
- Casing issue: City names were inconsistently formatted — converted to uppercase for consistency.
- Duplicate naming: "BANGALORE" was being counted separately from "BENGALURU" (the city's official renamed version) — merged into "BENGALURU" for a more accurate count.

## Analysis

**1. Orders by Shipping Service Level**
**2. Orders by Product Category**
**3. Top 10 States by Order Volume**
**4. Top 15 Cities by Order Volume**

*(See `notebooks/Amazon sale vis.ipynb` for the charts.)*

## Key Findings
1. Expedited shipping makes up the majority of orders (~69%), while Standard accounts for the remaining ~31%.
2. Set and kurta are the two most shipped categories, together making up about 78% of all orders, while no other category exceeds ~12%.
3. Maharashtra has the highest number of shipped orders (~17%) among all 31 states/UTs, though no single state holds a majority.
4. Bengaluru receives the highest number of orders nationally (~10%), ahead of other major cities, but does not account for a majority.

## Recommendations
1. Given that most deliveries are Expedited, a business might consider improving Standard delivery speed to reduce the gap between the two options.
2. Given the dominance of Set and kurta, a business might consider running promotions on lower-performing categories (Saree, Dupatta, Bottom) to boost their sales.
3. Given Maharashtra's lead in order volume, a business might consider prioritizing warehouse or fulfillment capacity there to maintain fast delivery as demand grows.
4. Given Bengaluru's high order volume, a business might consider setting up a local distribution hub to reduce delivery times in that city.

*Note: These are inferences based on order-volume patterns, not proven facts — no cost or delivery-time data was available to confirm impact.*

## How to Reproduce
1. Clone this repository
2. Install dependencies: `pip install pandas matplotlib`
3. Open `notebooks/Amazon sale vis.ipynb` in Jupyter
4. Run all cells in order
