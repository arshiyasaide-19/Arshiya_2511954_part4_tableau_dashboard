# Part 4: Tableau Executive Dashboard & Data Storytelling

## Business Problem Summary
The retail leadership team needs an executive dashboard to monitor sales performance, profitability, customer segments, category performance, shipping performance, discount impact, and return patterns. The dashboard should help leadership identify business opportunities and risks — not just display charts.

---

## Dataset Description
- **File**: `data/dashboard_sales_data.xlsx`
- **Rows**: 4,200 orders
- **Date Range**: 2024–2025
- **Columns**: 20 fields

| Field | Type | Description |
|---|---|---|
| order_id | Text | Unique order identifier |
| order_date | Date | When the order was placed |
| ship_date | Date | When the order was shipped |
| customer_id | Text | Customer identifier |
| customer_segment | Text | Consumer / Corporate / Home Office |
| region | Text | North / South / East / West |
| state | Text | Indian state |
| city | Text | City |
| category | Text | Furniture / Office Supplies / Technology |
| sub_category | Text | Product sub-category |
| product_name | Text | Product name |
| ship_mode | Text | Second Class / Standard Class / First Class / Same Day |
| sales | Number | Order revenue |
| quantity | Number | Units ordered |
| discount | Number | Discount percentage (0–1) |
| profit | Number | Order profit (can be negative) |
| return_flag | Binary | 1 = returned, 0 = not returned |
| delivery_days | Number | Days between order and ship date |
| customer_rating | Number | Customer satisfaction rating (32 missing) |
| campaign_channel | Text | Traffic source (24 missing) |

---

## Tableau Workbook Description

**File**: `tableau/executive_dashboard.twbx`

The workbook contains 7 individual sheets and 1 executive dashboard:

| Sheet | Purpose |
|---|---|
| Sales Trend | Monthly sales and profit line chart |
| Regional Performance | Bar chart + map by region and state |
| Category Profitability | Bar chart by category and sub-category profit |
| Customer Segment | Grouped bar chart by segment |
| Shipping Performance | Delivery days and order value by ship mode |
| Discount vs Profit | Scatter plot showing discount-profit relationship |
| Return Analysis | Highlight table showing return rates by category and segment |

---

## Calculated Fields Created

| Field | Formula |
|---|---|
| Profit Margin | SUM([Profit]) / SUM([Sales]) |
| Cost | SUM([Sales]) - SUM([Profit]) |
| Average Order Value | SUM([Sales]) / COUNT([Order ID]) |
| Return Rate | SUM([Return Flag]) / COUNT([Order ID]) |
| Shipping Delay Bucket | IF [Delivery Days] <= 1 THEN "Same Day" ELSEIF [Delivery Days] <= 3 THEN "Fast (2–3 days)" ELSEIF [Delivery Days] <= 5 THEN "Standard (4–5 days)" ELSE "Slow (6+ days)" END |

---

## Dashboard Components

- **4 KPI Cards**: Total Sales, Total Profit, Profit Margin %, Overall Return Rate
- **7 chart views** as listed above
- **5 interactive filters**: Region, Category, Customer Segment, Order Date, Ship Mode

---

## Filters and Interactions Used

- Region filter: affects all views simultaneously
- Category filter: affects category, sub-category, and scatter plot views
- Customer Segment filter: affects segment and return analysis views
- Date range filter: affects trend and all aggregate views
- Dashboard action: clicking a region on the map filters all other charts to that region

---

## Key Business Insights

1. Technology generates 84% of total profit — the business depends on one category
2. South region outperforms East and West by ~25% in sales
3. Discounts above 30% are loss-making on average
4. Furniture has a 7.67% return rate — more than double Technology
5. Organic traffic generates more sales than all paid channels combined
6. Same Day shipping correlates with the highest average order value
7. Monthly sales have a clear Q2 dip (April–June) that needs a campaign response
8. All three customer segments perform similarly — no single segment is over-relied upon

---

## Dashboard Story Summary

The business is profitable and growing, but three risks need leadership attention: over-reliance on Technology for profit, loss-making deep discounts, and high Furniture return rates. South region success should be studied and replicated. See `outputs/dashboard_story.md` for the full narrative.

---

## Assumptions and Limitations
1. 32 missing customer_rating values excluded from rating-based analysis
2. 24 missing campaign_channel values treated as unknown in channel analysis
3. Profit can be negative (heavily discounted orders) — this is retained as-is, not cleaned
4. Data covers 2024–2025 only — multi-year trends are not available
5. Cost of customer acquisition per channel is unknown — Organic channel ROI cannot be fully assessed

---

## Screenshots Included

| File | Shows |
|---|---|
| `screenshots/full_dashboard.png` | Complete executive dashboard |
| `screenshots/sales_trend_view.png` | Monthly sales and profit line chart |
| `screenshots/regional_performance_view.png` | Regional map |
| `screenshots/category_profitability_view.png` | Category and sub-category profit bar chart |
| `screenshots/filter_interaction_view.png` | Dashboard with a filter applied |
