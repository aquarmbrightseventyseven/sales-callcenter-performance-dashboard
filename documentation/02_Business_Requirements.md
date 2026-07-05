# 02 — Business Requirements

## Stakeholder Questions

The dashboard was designed to answer the following business questions:

1. Which **locations** generate the most sales and revenue, and which lag behind?
2. How do sales and revenue **trend across the year** — are there seasonal peaks or troughs?
3. Which **products** are top sellers by volume vs by revenue (these can diverge)?
4. How does **call-center workload** (calls handled, handle time) track against sales activity by location, month, quarter, and product?
5. Are there **quarters** that consistently outperform or underperform?
6. Can a single report support **ad-hoc slicing** by Month, Quarter, Location, and Product without needing separate reports for each cut?

## Functional Requirements

| Requirement | Delivered via |
|---|---|
| Filter by Month, Quarter, Location, Product simultaneously | Four global slicers at the top of the report |
| KPI summary at a glance | 10 KPI cards (Sales Periods, Total/Avg/Min/Max Sales, Total/Avg/Min/Max Revenue, Calls Handled, Handle Time) |
| Sales & Revenue breakdowns | Combo bar/line charts by Location, Month, Quarter |
| Product performance ranking | Horizontal bar charts for Sales by Product and Revenue by Product |
| Call-center breakdowns | Combo bar/line charts by Location, Month, Quarter, Product |
| Titles that reflect the active filter | Dynamic DAX title measures (see [05_DAX_Measures.md](05_DAX_Measures.md)) |

## Non-Functional Requirements

- **Single page** — all insights visible without navigating between report pages
- **Consistent visual language** — a maroon/purple color palette throughout for brand consistency
- **Responsive to filters** — every visual and every chart title reacts live to slicer changes

## Out of Scope

- Forecasting / predictive analytics
- Customer-level or transaction-level drill-through
- Multi-year comparison (data covers 2026 only)

---
Previous: [01 — Project Overview](01_Project_Overview.md) · Next: [03 — Data Preparation](03_Data_Preparation.md)
