# 05 — DAX Measures

The model defines **13 measures**. Only one performs a numeric aggregation directly — the KPI cards for Total/Avg/Min/Max Sales and Revenue, Calls Handled, and Handle Time are built using **implicit aggregations** on the `Raw Data` columns rather than explicit measures. The remaining 12 measures are **dynamic title generators** that keep chart titles in sync with the active slicer selection.

## Aggregation Measure

```dax
Sale = SUM('Raw Data'[Sales])
```
Total units sold — the explicit measure backing the "Sales" series in charts.

## Dynamic Title Measures

These follow a consistent two-step pattern:
1. A **"list" measure** that returns the concatenated current filter selection, falling back to a generic axis label ("Location", "Month", etc.) when nothing/everything is filtered.
2. A **"title" measure** that wraps the list in display text for the chart title.

### Location

```dax
location list =
IF(
    ISFILTERED('Raw Data'[Location]),
    CONCATENATEX(VALUES('Raw Data'[Location]), 'Raw Data'[Location], ", "),
    "Location"
)

location title  = "Sales & Revenue by " & [location list]
location title2 = "Calls Handle & Handle Time by " & [location list]
```

### Month

```dax
month list =
IF(
    ISFILTERED('Raw Data'[Month name]),
    CONCATENATEX(VALUES('Raw Data'[Month name]), 'Raw Data'[Month name], ", "),
    "Month"
)

month title  = "Sales & Revenue by " & [month list]
month title2 = "Calls Handle & Handle Time by " & [month list]
```

### Quarter

```dax
quarter list =
IF(
    ISFILTERED('Raw Data'[Quarter]),
    CONCATENATEX(VALUES('Raw Data'[Quarter]), 'Raw Data'[Quarter], ", "),
    "Quarter"
)

quarter title  = "Sales & Revenue by " & [quarter list]
quarter title2 = "Calls Handle & Handle Time by " & [quarter list]
```

### Product

```dax
product list =
IF(
    ISFILTERED('Raw Data'[Product]),
    CONCATENATEX(VALUES('Raw Data'[Product]), 'Raw Data'[Product], ", "),
    "Product"
)

product title  = "Sales by " & [product list]
product title2 = "Revenue by " & [product list]
product title3 = "Calls Handle & Handle Time by " & [product list]
```

## Why This Pattern

Each visual title updates live as the user changes the Month / Quarter / Location / Product slicers — e.g. selecting "Delhi" changes the chart title from "Sales & Revenue by Location" to "Sales & Revenue by Delhi" — giving the report a dynamic, presentation-ready feel without manually editing titles for every slicer state.

---
Previous: [04 — Data Model](04_Data_Model.md) · Next: [06 — Dashboard Explanation](06_Dashboard_Explanation.md)
