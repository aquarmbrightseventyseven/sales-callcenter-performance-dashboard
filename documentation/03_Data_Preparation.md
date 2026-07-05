# 03 — Data Preparation

## Source Data

The model is built from a single conceptual dataset capturing, for each Product/Month combination: sales volume, revenue, calls handled, and handle-time metrics, broken out by location. This raw data was shaped into **two tables** to serve different visual requirements.

## Tables Produced

### `Raw Data` (96 rows — wide format)
One row per Product × Month, carrying every metric as its own column (`Sales`, `Revenue`, `Calls Handled`, `Average Handle Time`, `Total Handle Time`, `Handle Time`). This is the primary table used for KPI cards and most bar/line charts.

### `Indicators` (480 rows — long/unpivoted format)
The same underlying metrics reshaped into an **Indicator / Value** pair structure (5 indicators × 96 rows). This unpivoted shape is what allows a single combo visual to plot multiple, differently-scaled metrics (e.g. Sales alongside Revenue) by filtering on the `Indicator` column rather than needing separate measures per series.

## Derived / Calculated Columns

Several columns in `Raw Data` were derived to support formatting and sorting needs that the raw source didn't already provide:

| Column | Derivation logic |
|---|---|
| `Month` | Numeric month index (1–12), used to sort month names chronologically instead of alphabetically |
| `First Characters` | 3-letter month abbreviation, used for compact axis labels (JAN, FEB, …) |
| `Month name` | A clean text version of the month, used to drive slicers independently from any sort columns |
| `Quarter` | Q1–Q4 grouping derived from the month |
| `Handle Time` | `Total Handle Time` normalized to minutes (divided by 60) for more readable chart scales |

## Data Quality Notes

- No relationships exist between `Raw Data` and `Indicators` — they are independent, purpose-built extracts of the same source rather than a normalized star schema. This is a reasonable simplification for a report of this scope, but means any future measure changes need to be applied in **both** tables' underlying query logic to stay in sync.
- All 96 `Raw Data` rows have complete values across every column (no blanks/nulls observed during model inspection).
- Revenue is stored as decimal and calls/sales as whole integers, matching the nature of each metric.

---
Previous: [02 — Business Requirements](02_Business_Requirements.md) · Next: [04 — Data Model](04_Data_Model.md)
