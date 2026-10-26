Amazon E-commerce Sales Analysis | Power BI
Overview

This project analyzes about 120,000 Amazon India orders (April to June 2022) to understand where revenue comes from and where the business loses orders. I cleaned the raw data, built a star-schema data model, wrote DAX measures, and designed a 3-page interactive dashboard with a final page of insights and recommendations.

Dashboard Preview

Page 1: Overview & Category Analysis

Overview page

Page 2: Cancellations & Geography

Cancellations and geography page

Page 3: Key Insights & Recommendations

Key insights

Business Questions
What is the sales trend over time?
Which product categories generate the most revenue, and which have the highest average order value?
What is the overall cancellation rate, and does it change with fulfilment method or category?
Which cities generate the most revenue?
How does order volume vary by day of the week?
How much revenue comes from business (B2B) buyers compared with regular (B2C) customers?

Dataset
Source: Amazon Sale Report (Kaggle)
Size: about 120,000 orders
Main fields: Order ID, Date, Status, Amount, Category, Size, SKU, Fulfilment, ship-city, ship-state, B2B
Data Model (Star Schema)

One fact table connected to three dimension tables:

Amazon Sale Report (fact table): orders and amounts
Dim_Date: calendar table built with DAX
Dim_Product: one row per SKU (Category, Size, Style, ASIN)
Dim_Location: one row per city and state, joined through a LocationKey

All relationships are one-to-many with single-direction filtering.

What I Did?
Power Query: fixed an inconsistent text-formatted date column (trim, clean, then convert using locale), kept meaningful blanks instead of deleting them, and created the product and location dimension tables

Data modeling: split a flat file into a fact table and three dimensions

DAX measures: Total Sales, Total Orders, Average Order Value, Cancelled Orders, and Cancellation Rate

Visualization: KPI cards, trend line, bar charts, and slicers for date and category

Key Insights and Recommendations:
Sales fell from about 29M in April to about 23M in June. Check whether promotions ended or June data is incomplete. (March was excluded from the trend because the data contains only one day of it.)

Set is the top category and drives the largest share of revenue. Keep it well stocked and avoid depending on only a few categories.

Saree has the highest average order value (about 850) but is not a top seller. A promotion test could show whether it lifts revenue.

About 14% of orders are cancelled, and Merchant-fulfilled orders are cancelled more often than Amazon-fulfilled ones in every category, with Saree the highest. Review seller shipping and stock practices.

Bengaluru leads city sales, followed by Hyderabad and Mumbai. Prioritize marketing and delivery capacity there.
Limitations

The data covers only about three months, so year-over-year analysis is not possible.

Saree is a small category by volume, so its high average order value and cancellation rate should be validated before acting on them.
Files in this Repository
*.pbix: the Power BI project file (open with Power BI Desktop)

page1.png, page2.png, insights.png: dashboard screenshots
