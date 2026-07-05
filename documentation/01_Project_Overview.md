# 01 — Project Overview

## Project Title
**Sales & Callcenter Performance Dashboard** — a 2026 Sales & Call-Center Performance Report built in Power BI.

## Purpose

This project analyzes a full year (2026) of product sales alongside call-center support activity, giving a single view of **commercial performance** (sales, revenue) and **operational performance** (calls handled, handle time) across products, locations, months, and quarters.

## Objectives

- Track sales and revenue trends across the year, by location, month, quarter, and product
- Monitor call-center workload (calls handled, handle time) alongside sales activity to spot correlations between demand and support load
- Give stakeholders a single, slicer-driven report instead of separate sales and operations reports
- Demonstrate a clean, dynamic-title DAX pattern that keeps every chart contextually labeled as filters change

## Scope

- **Time period:** January – December 2026 (12 months, 4 quarters)
- **Geography:** 4 locations — Bangalore, Delhi, Kolkatta, Mumbai
- **Products:** 8 categories — Smartphone, Laptops, Desktops, Tablets, Ipods, Ipad, Camera, XBox
- **Granularity:** Product × Month (96 records)

## Tools Used

| Tool | Purpose |
|---|---|
| Power BI Desktop | Data modeling, DAX, report/dashboard build |
| DAX | Dynamic slicer-aware measures and KPI aggregations |
| Power Query (assumed source prep) | Shaping the raw and unpivoted (`Indicators`) tables |

## Deliverable

A single-page interactive Power BI dashboard (see [`screenshots/dashboard_page_1.png`](../screenshots/dashboard_page_1.png)) with four global slicers (Month, Quarter, Location, Product) driving nine linked visual groups.

---
Next: [02 — Business Requirements](02_Business_Requirements.md)
