# Business Insights — Executive Dashboard

## Dataset Overview
- **4,200 orders** across 4 regions, 3 categories, 4 customer segments
- **Date range**: 2024–2025
- **Total Sales**: ~₹216.8 million | **Total Profit**: ~₹33.3 million

---

## Calculated Fields Created in Tableau

| Field Name | Formula | Why It's Useful |
|---|---|---|
| Profit Margin | SUM([Profit]) / SUM([Sales]) | Shows what percentage of every rupee of sales becomes profit |
| Cost | SUM([Sales]) - SUM([Profit]) | Estimates cost of goods — useful for profitability analysis |
| Average Order Value | SUM([Sales]) / COUNT([Order ID]) | Measures how much each order is worth on average |
| Return Rate | SUM([Return Flag]) / COUNT([Order ID]) | Shows what percentage of orders are returned |
| Shipping Delay Bucket | IF [Delivery Days] <= 1 THEN "Same Day" ELSEIF [Delivery Days] <= 3 THEN "Fast (2–3 days)" ELSEIF [Delivery Days] <= 5 THEN "Standard (4–5 days)" ELSE "Slow (6+ days)" END | Groups delivery times into meaningful business buckets |

---

## Insight 1 — Sales Trend: Growth Is Uneven

**Observation**: Monthly sales peaked in July–August 2025 (₹10.7M and ₹10.9M respectively) but dipped sharply in April and June 2025 (₹7.2M and ₹7.3M).

**Data Evidence**: July 2025 = ₹10.66M vs April 2025 = ₹7.19M — a 48% gap between best and worst months.

**Business Interpretation**: Revenue is volatile month-to-month. The Q2 2025 dip (April–June) suggests a seasonal slowdown or campaign gap that should be investigated.

**Recommended Action**: Investigate what campaigns or events drove the July–August peak and plan similar initiatives during the Q2 period next year to smooth the revenue curve.

---

## Insight 2 — Regional Performance: South Leads, East and West Lag

**Observation**: The South region generates the most sales (₹64.7M) and profit (₹10.0M). East and West regions both sit around ₹48.9M — roughly 25% lower than South.

**Data Evidence**: South = ₹64.7M sales | North = ₹54.6M | East = ₹48.9M | West = ₹48.9M.

**Business Interpretation**: South region stores or customer base are significantly more productive. This could be due to higher population density, stronger brand presence, or better store locations.

**Recommended Action**: Study the South region's customer acquisition and retention strategy and consider replicating it in East and West.

---

## Insight 3 — Category Profitability: Technology Dominates

**Observation**: Technology generates 71% of total profit (₹28.0M out of ₹33.3M) despite not being the only category. Furniture and Office Supplies contribute far less.

**Data Evidence**: Technology profit = ₹28.0M | Furniture = ₹3.6M | Office Supplies = ₹1.7M.

**Business Interpretation**: Technology products have significantly higher margins. The business is heavily dependent on one category for profit health. If Technology demand falls, overall profitability will be severely impacted.

**Recommended Action**: Invest more in Technology product range expansion. Also explore whether Furniture margins can be improved through supplier renegotiation or premium product introductions.

---

## Insight 4 — Customer Segment Behaviour: Segments Are Surprisingly Similar

**Observation**: All three customer segments (Consumer, Corporate, Home Office) have very similar total sales (~₹70–75M each) and profit (~₹11M each).

**Data Evidence**: Home Office = ₹74.5M | Consumer = ₹71.9M | Corporate = ₹70.6M.

**Business Interpretation**: The business is not over-reliant on any single customer segment, which is healthy. However, Home Office has a slightly higher return rate (6%) vs Consumer and Corporate (4%) — worth monitoring.

**Recommended Action**: Investigate why Home Office customers return products more often. It may be a product expectation or description mismatch issue that can be fixed easily.

---

## Insight 5 — Discount Impact: Heavy Discounting Destroys Profit

**Observation**: Orders with discounts above 30% generate negative average profit (–₹1,601 per order). Orders with 0–10% discounts generate ₹11,643 average profit.

**Data Evidence**: 0–10% discount → avg profit ₹11,643 | 10–20% → ₹6,336 | 20–30% → ₹3,181 | 30–40% → –₹1,601.

**Business Interpretation**: Every percentage point of discount above 20% erodes profit rapidly. Discounts over 30% are loss-making on average — the business is effectively paying customers to buy at this level.

**Recommended Action**: Implement a discount cap policy at 20% for standard orders. Any discount above 20% should require management approval with a clear business justification.

---

## Insight 6 — Shipping Performance: Same Day Is Fastest but Standard Class Is Most Used

**Observation**: Same Day delivery averages 0.4 days and has the highest average order value (₹60,428). Standard Class takes 4.71 days on average and is likely the most-used mode.

**Data Evidence**: Same Day avg delivery = 0.4 days, avg order value = ₹60,428 | Standard Class = 4.71 days, avg order value = ₹50,442.

**Business Interpretation**: Faster shipping correlates with higher order value — high-value customers tend to choose faster shipping options. This may reflect corporate or urgent buyers.

**Recommended Action**: Promote Same Day and First Class shipping options to high-value customer segments. Consider offering these as default options for orders above a certain value threshold.

---

## Insight 7 — Return Patterns: Furniture Has the Highest Return Rate

**Observation**: Furniture has a 7.67% return rate — more than double the Technology return rate (3.03%) and significantly above Office Supplies (3.65%).

**Data Evidence**: Furniture = 7.67% | Office Supplies = 3.65% | Technology = 3.03%.

**Business Interpretation**: Furniture returns are costly — they involve logistics, restocking, and potential product damage. The high return rate may indicate product quality issues, delivery damage, or poor product descriptions leading to mismatched expectations.

**Recommended Action**: Review the top returned Furniture sub-categories. Improve product photography, descriptions, and sizing guides. Consider a stricter quality check for Furniture before dispatch.

---

## Insight 8 — Campaign Channel: Organic Traffic Is the Most Valuable

**Observation**: Organic traffic generates the most sales (₹88.8M) and the most profit (₹13.4M) by a large margin. Paid advertising generates ₹40.1M — less than half of Organic.

**Data Evidence**: Organic = ₹88.8M sales | Paid = ₹40.1M | Email = ₹34.5M | Social = ₹31.1M | Referral = ₹21.2M.

**Business Interpretation**: The business benefits enormously from organic discovery — likely strong SEO, word of mouth, or brand recognition. Referral is the weakest channel and may not justify continued investment unless cost per acquisition is very low.

**Recommended Action**: Invest in content marketing and SEO to strengthen the Organic channel. Review Referral programme ROI — if cost per customer acquired is high, reallocate that budget to Email or Paid channels which generate more revenue.
