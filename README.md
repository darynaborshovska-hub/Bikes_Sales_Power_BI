# Bike Sales — Power BI Report

A Power BI report (`BikeSales_Final.pbix`) looking at bike sales performance — revenue, margins, customer profile, and returns.

## Does it have raw data in it?

**Yes.** This isn't just a report shell pointing at an external source — the `.pbix` file has its own embedded data model (a compressed ~1.9 MB internal database, the same VertiPaq/xVelocity engine Power BI always uses). That means all the tables, rows, and relationships are baked right into the file itself. Anyone who opens it in Power BI Desktop can see the actual underlying rows, not just the finished charts.

So: not a live connection to some external database, and not just cached visuals — the numbers travel with the file.

## Pages in the report

- **Executive Overview**
- **Product Insights**
- **Customer Insights**
- **Returns**
- **Product Detail**

## What's in the data model

One fact table, several dimension tables around it — a pretty standard star schema:

**`FactSales`** — the transactions themselves (order dates, and everything else rolls up from here)

**Dimension tables:**
- `DimProduct` — product name, color, size, style, material, tier, use case, price
- `DimProduct Categories` / `DimProduct Subcategories` — category & subcategory grouping
- `DimCustomer` — age bracket, gender, income, education, occupation, home ownership
- `DimTerritory` — country, region
- `DimCalendar` — full date table with year/quarter/month hierarchy

**Key measures already built in (DAX):**
- Total Sales, Sales YTD, Sales PY, YoY Growth %
- Profit, Profit Margin %
- AOV (average order value), Sales per Customer
- Total Orders, Total Customers, Units Sold
- Total Returns, Return Rate, Return Contribution %
- Avg Lead Time (days)
- Sales % in Bikes, Men / Women split

## Opening it

Needs Power BI Desktop (free) — File → Open, point it at the `.pbix`, and everything (data, model, visuals) loads as-is. No separate database connection needed to explore what's already there.

## Worth adding to the repo

- A short note on where the raw data originally came from (looks like a classic "Adventure Works"-style bike sales dataset, but worth confirming and crediting the source)
- Screenshots of a page or two, so people get a preview without opening Power BI
- If the underlying data ever needs to be reused outside Power BI, consider exporting the key tables to `.csv` alongside the `.pbix`
