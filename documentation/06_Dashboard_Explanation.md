# 06 — Dashboard Explanation

![Dashboard](../screenshots/dashboard_page_1.png)

## Layout

The report is a single page organized into three horizontal bands:

1. **Header + Slicers** — title band with four slicers: Month, Quarter, Location, Product
2. **KPI Strip** — 10 cards summarizing the whole dataset (or current filter context)
3. **Visual Grid** — a 3×3 grid of charts covering Sales & Revenue and Calls Handled & Handle Time, each cut by Location, Month/Quarter, and Product

## KPI Strip

| Card | Meaning |
|---|---|
| Sales Period | Count of distinct Product × Month combinations (96) |
| Total Sales | Sum of units sold (38K) |
| Avg / Min / Max Sales | Distribution of sales per record (400.76 / 102 / 692) |
| Total Revenue | Sum of revenue (746.18K) |
| Avg / Min / Max Revenue | Distribution of revenue per record (7.77K / 1.31K / 16.82K) |
| Calls Handled | Total support calls (479K) |
| Handle Time | Total handle time across all calls (4.01M seconds) |

## Row 1 — By Location

- **Sales & Revenue by Location** — combo chart comparing units sold (bars) against revenue (line) per city. Delhi leads on revenue (~207K), closely followed by Kolkatta (~206K); Bangalore trails at ~148K.
- **Sales & Revenue by Month** — area/line chart showing the shape of the year, with visible peaks and dips month to month.
- **Sales by Product** — horizontal bar ranking of unit sales by product category, all clustering around 4-5K units.

## Row 2 — By Quarter / Location (Calls)

- **Sales & Revenue by Quarter** — quarterly rollup showing Q1 as the strongest quarter for both sales and revenue.
- **Calls Handled & Handle Time by Location** — combo chart pairing call volume (bars) with total handle time (line) per city; Delhi again leads on handle time (1.12M), Bangalore lowest (0.84M).
- **Revenue by Product** — horizontal bar ranking of revenue by product; notably, product revenue rank differs from unit-sales rank (see [07 — Business Insights](07_Business_Insights.md)).

## Row 3 — By Quarter / Month / Product (Calls)

- **Calls Handled & Handle Time by Quarter** — Q2 shows the lowest handle time (937K) despite consistent call volumes.
- **Calls Handled & Handle Time by Month** — a full-year trend line for operational load.
- **Calls Handled & Handle Time by Product** — per-product view showing which products drive the most support burden relative to their sales volume.

## Interaction Model

All slicers filter every visual on the page simultaneously, and — thanks to the dynamic title measures — every chart's title text updates to name the current selection, so a stakeholder screen-sharing this report never loses context even when zoomed into a single filtered view.

---
Previous: [05 — DAX Measures](05_DAX_Measures.md) · Next: [07 — Business Insights](07_Business_Insights.md)
