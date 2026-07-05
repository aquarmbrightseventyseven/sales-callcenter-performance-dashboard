# 04 — Data Model

## Model Summary

| Property | Value |
|---|---|
| Tables | 2 (`Raw Data`, `Indicators`) |
| Relationships | None — both tables are independent, self-contained extracts |
| Compatibility level | 1600 |
| Total measures | 13 |

## Table: `Raw Data` (96 rows)

| Column | Data Type | Description |
|---|---|---|
| `Sale Month` | Text | Full month name (e.g. "January") |
| `Product` | Text | Product category (8 distinct values) |
| `Location` | Text | City (4 distinct values) |
| `Calls Handled` | Integer | Number of support calls handled |
| `Average Handle Time` | Integer | Average handle time per call (seconds) |
| `Sales` | Integer | Units sold |
| `Revenue` | Number | Revenue generated |
| `Total Handle Time` | Integer | Total handle time across calls (seconds) |
| `Month` | Integer | Numeric month (1–12) for chronological sorting |
| `First Characters` | Text | 3-letter month abbreviation (axis labels) |
| `Month name` | Text | Slicer-friendly month text |
| `Quarter` | Text | Q1–Q4 |
| `Handle Time` | Number | Handle time in minutes (`Total Handle Time / 60`) |

## Table: `Indicators` (480 rows)

| Column | Data Type | Description |
|---|---|---|
| `Sale Month` | Text | Month name |
| `Product` | Text | Product category |
| `Location` | Text | City |
| `Indicator` | Text | One of: `Sales`, `Revenue`, `Calls Handled`, `Average Handle Time`, `Total Handle Time` |
| `Value` | Number | Value of the named indicator |

This long-format table exists purely to power combo charts that need to plot multiple metrics of different scales on one visual.

## Why No Relationships?

Both tables cover the exact same grain (Product × Month, exploded further by Location within `Indicators`), so there was no need for a star-schema join — each table is queried independently by the visuals that need its specific shape. This keeps the model simple at the cost of some duplication between the two tables' underlying source queries.

## Cardinality Reference

- 4 Locations × 8 Products × 12 Months = 384 possible combinations
- Actual `Raw Data` row count = 96 (Product × Month grain, one Location value assigned per row — not a full cross-join)
- `Indicators` = 96 × 5 indicators = 480 rows

---
Previous: [03 — Data Preparation](03_Data_Preparation.md) · Next: [05 — DAX Measures](05_DAX_Measures.md)
