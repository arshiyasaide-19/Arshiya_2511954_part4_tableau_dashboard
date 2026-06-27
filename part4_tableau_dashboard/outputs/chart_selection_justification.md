# Chart Selection Justification

Every chart in the dashboard was chosen to answer a specific business question — not for decoration. Below is the reasoning behind each one.

---

## 1. Sales Trend View — Line Chart

**Business question it answers**: How are sales changing month by month?

**Why a line chart**: Line charts are the best tool for showing change over time. The eye naturally follows the line and instantly sees rises, falls, and turning points. A bar chart would work too, but a line chart is cleaner when you have 20+ time points.

**Fields used**:
- X-axis: Order Date (Month)
- Y-axis: SUM(Sales)
- Second line: SUM(Profit) — shown in a different colour for comparison

**Design principle applied**: Dual-axis used carefully — sales and profit share the same time axis but profit uses a secondary Y-axis so both lines are visible without one dominating.

**Mistake avoided**: Did not use an area chart — area charts can exaggerate the visual size of small changes and are harder to read when two measures overlap.

---

## 2. Regional Performance View — Map

**Business question it answers**: Which region generates the most sales and profit?

**A map**: A geographic map shows where in the country each region is located, which adds context that a plain bar chart cannot. Colour intensity on the map shows sales concentration at state level.

**Fields used**:
- Map: State on detail, SUM(Sales) on colour

**Mistake avoided**: Did not use a pie chart — pie charts make it hard to compare similar-sized slices and cannot show two measures simultaneously.

---

## 3. Category Profitability View — Bar Chart (with sub-category breakdown)

**Business question it answers**: Which categories and sub-categories are driving or hurting profit?

**Why a bar chart**: Profit values need to be compared directly. A bar chart with positive and negative values (profit can be negative for heavily discounted items) clearly shows which sub-categories are loss-making.

**Fields used**:
- X-axis: SUM(Profit)
- Y-axis: Sub-category
- Colour: Category (so Technology, Furniture, Office Supplies each have their own colour)

**Design principle applied**: Sorted by profit descending so loss-making sub-categories appear at the bottom — leadership can immediately see the red bars without scrolling.

**Mistake avoided**: Did not use a treemap — treemaps are great for part-of-whole analysis but make it hard to read exact values or compare similar-sized items.

---

## 4. Customer Segment View — Grouped Bar Chart

**Business question it answers**: Which customer segment buys the most, generates the most profit, and returns the most?

**Why a grouped bar chart**: When comparing the same measures (sales, profit, return rate) across multiple groups (Consumer, Corporate, Home Office), a grouped bar chart puts all comparisons side by side for easy reading.

**Fields used**:
- X-axis: Customer Segment
- Y-axis: SUM(Sales), SUM(Profit), AVG(Return Flag)
- Colour: Measure type

**Design principle applied**: Consistent colour per measure across all groups — green for profit, blue for sales, red for return rate.

**Mistake avoided**: Did not use a stacked bar — stacked bars are good for part-of-whole but make it hard to compare individual segments across measures.

---

## 5. Shipping Performance View — Bar Chart + Table

**Business question it answers**: Which shipping mode is fastest and which is most used? Do faster shipping modes lead to higher sales?

**Why a bar chart for delivery days**: Comparing average delivery days across 4 ship modes is a direct comparison — a bar chart is the clearest tool.

**Why a summary table**: A table alongside the chart shows exact numbers (average order value, order count) that are hard to read precisely from a bar chart.

**Fields used**:
- Ship Mode on rows
- AVG(Delivery Days) on columns
- Shipping Delay Bucket on colour (from calculated field)

**Design principle applied**: Colour-coded by delivery speed (green = fast, red = slow) so the message is instantly visible without reading the axis.

**Mistake avoided**: Did not use a line chart — delivery speed by ship mode is a categorical comparison, not a time series.

---

## 6. Discount vs Profit View — Scatter Plot

**Business question it answers**: Is there a relationship between how much we discount and how much profit we make?

**Why a scatter plot**: Scatter plots are specifically designed to show the relationship between two continuous numeric variables. Every dot is one order — you can see the whole pattern at once.

**Fields used**:
- X-axis: Discount
- Y-axis: Profit
- Colour: Category (to see if the discount-profit relationship differs by category)
- Reference line: Zero profit line (horizontal) to show loss-making orders

**Design principle applied**: A reference line at Profit = 0 immediately separates profitable orders (above) from loss-making orders (below). Category colour reveals that most negative-profit orders come from Furniture.

**Mistake avoided**: Did not use a line chart — a line chart implies time or order, which is not the relationship being shown here.

---

## 7. Return Analysis View — Highlight Table (Heat Map)

**Business question it answers**: Where are returns concentrated — by category, region, or customer segment?

**Why a highlight table**: A highlight table (also called a heat map) shows a grid of values with colour intensity — the darker the colour, the higher the return rate. It is the most efficient way to show a matrix of values across two dimensions simultaneously.

**Fields used**:
- Rows: Category
- Columns: Customer Segment or Region
- Colour: AVG(Return Flag) — green to red scale
- Label: Formatted percentage

**Design principle applied**: Red = high return rate, green = low. The colour scale is immediately intuitive — no legend reading required to understand the danger zones.

**Mistake avoided**: Did not use a bar chart for this — a bar chart can only show one dimension at a time. A highlight table shows both dimensions (category AND segment) simultaneously in one compact view.

---

## Dashboard Layout Principles Applied

1. **Clear title at the top**: "Retail Executive Dashboard — Sales & Profitability Overview"
2. **KPI cards at the top row**: Total Sales, Total Profit, Profit Margin %, Return Rate — four numbers leadership checks every time they open the dashboard
3. **Filters on the right or top**: Region, Category, Customer Segment, Date Range, Ship Mode — all interactive
4. **Logical flow top-to-bottom**: KPIs → Time trend → Regional → Category → Segment → Operations (Shipping, Returns)
5. **Consistent colour palette**: Blue tones for sales/volume, green for profit, red for risk/returns
6. **No 3D charts**: 3D charts distort perception and make values harder to compare accurately — none used
7. **No pie charts**: With more than 3 segments, pie charts become unreadable — bar charts used instead throughout
