# Ad-Hoc Insights: SQL Analytics for AtliQ Hardware

SQL-driven analysis of sales, pricing, and discount data for AtliQ Hardware (a fictional India-based computer hardware manufacturer), answering 10 ad-hoc business questions posed by the company's Data Analytics Director as part of a hiring case study.

## Business Context

AtliQ Hardware sells computer hardware and accessories across APAC, EU, LATAM, and NA through multiple channels (retailer, distributor, direct). Leadership needed quick, data-backed answers to recurring business questions — market coverage, product growth, customer discounts, and sales performance — without waiting on a full reporting cycle. This project answers ten of those requests directly against the company's sales database.

## Analytical Approach

Each request is answered with a standalone SQL query against a star-schema sales database (`dim_customer`, `dim_product`, `fact_sales_monthly`, `fact_gross_price`, `fact_manufacturing_cost`, `fact_pre_invoice_deductions`). Queries use CTEs, window functions (`RANK()`), and aggregations to go from raw transactional data to direct, decision-ready answers. Results are also visualized in Power BI for stakeholder-friendly reporting.

## Tech Stack

- **SQL (MySQL syntax)** — all 10 queries in `AD Hoc SQL CODES/`
- **Power BI** — `Ad hoc Visuals.pbix` for interactive dashboards on top of the same data

## Ad-Hoc Requests Answered

1. Markets where "Atliq Exclusive" operates in the APAC region
2. % increase in unique products, 2020 vs. 2021
3. Unique product counts by segment
4. Segment with the largest unique-product growth, 2020 vs. 2021
5. Products with the highest and lowest manufacturing cost
6. Top 5 customers by average pre-invoice discount % (India, FY2021)
7. Monthly gross sales for "Atliq Exclusive"
8. Quarter of FY2020 with the highest total sold quantity (plus a labeled variant, `Request 8+.sql`)
9. Sales channel with the highest gross sales and its % contribution (FY2021)
10. Top 3 products by sold quantity in each division (FY2021)

## Key Insights

- Notebooks, accessories, and peripherals drove the most growth in unique products from 2020 to 2021.
- Flipkart received the highest average pre-invoice discount among Indian customers in FY2021.
- November 2020 was "Atliq Exclusive"'s strongest month for gross sales; March 2020 was the weakest.
- The retailer channel contributed the largest share of gross sales in FY2021.

## How to Run

1. Load the AtliQ sales schema (`dim_customer`, `dim_product`, `fact_sales_monthly`, `fact_gross_price`, `fact_manufacturing_cost`, `fact_pre_invoice_deductions`) into a MySQL instance.
2. Run any query in `AD Hoc SQL CODES/` directly against that schema — each file is commented with the original business question and expected output columns.
3. Open `Ad hoc Visuals.pbix` in Power BI Desktop to explore the same data interactively.

## Notes

- Queries that join `fact_sales_monthly` to `fact_gross_price` are matched on both `product_code` and `fiscal_year`, since unit price varies by year — joining on `product_code` alone would mix prices across years and inflate/deflate the sales totals.
