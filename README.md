# Power BI Analytics Dashboard — Sales & Operations Performance

**Author:** Shanmuga Priya Gnanasekaran  
**Tools:** Power BI Desktop, DAX, Excel  
**Domain:** Sales Performance, Pipeline Analysis, KPI Reporting  
**Status:** Completed — academic and self-directed project  

---

## Overview

This repository documents a Power BI analytics solution designed to give business stakeholders a single, real-time view of sales performance, pipeline health and operational KPIs — replacing disconnected spreadsheets and manual reporting.

The dashboard was built as part of my Master of Business Analytics at Deakin University and extended independently to simulate a real enterprise reporting environment.

---

## Business Problem

The organisation had no centralised reporting tool. Sales managers were producing individual Excel reports weekly, finance was running separate pivot tables, and leadership had no live view of pipeline or revenue trends. Key problems:

- Reporting took 3–4 hours per week per team manually
- No single version of truth — numbers differed between teams
- No visibility of pipeline risk or underperforming segments
- Executive decisions were based on data that was 1–2 weeks old

---

## Solution

A multi-page Power BI dashboard connecting to a central data model, delivering:

- Live KPI cards (revenue, pipeline value, conversion rate, average deal size)
- Trend analysis across monthly and quarterly periods
- Drill-down by region, product category and sales representative
- Automated alerts when KPIs fall below threshold
- A clean executive summary page requiring zero technical knowledge to read

---

## Dashboard Pages

### Page 1 — Executive Summary
High-level KPIs for leadership. Designed for a 30-second read.

| Metric | Value (Sample) |
|---|---|
| Total Revenue (YTD) | $4.2M |
| Pipeline Value | $1.8M |
| Win Rate | 38% |
| Avg Deal Size | $24,500 |
| Deals Closing This Month | 12 |

### Page 2 — Sales Performance by Region
- Bar chart: revenue by region (East, West, North, South)
- Map visual: geographic distribution of deals
- Slicer: filter by quarter, product line, rep name
- KPI card: % variance against target per region

### Page 3 — Pipeline Analysis
- Funnel chart: leads → qualified → proposal → negotiation → closed
- Conversion rate at each stage
- Average days in each pipeline stage
- Risk flagging: deals stalled for 30+ days highlighted in amber

### Page 4 — Trend Analysis
- Line chart: monthly revenue vs target (12-month rolling)
- Revenue forecast using DAX time intelligence functions
- YoY comparison overlay
- Seasonality annotations

### Page 5 — Individual Rep Performance
- Table: rep name, deals closed, revenue, win rate, avg deal size
- Conditional formatting: green/amber/red against target
- Sparklines: 6-month trend per rep

---

## Key DAX Measures

```dax
Total Revenue = SUM(FactSales[DealValue])

Revenue YTD = TOTALYTD([Total Revenue], DimDate[Date])

Win Rate = 
DIVIDE(
    COUNTROWS(FILTER(FactSales, FactSales[Stage] = "Closed Won")),
    COUNTROWS(FactSales),
    0
)

YoY Growth % = 
DIVIDE([Total Revenue] - [Revenue PY], [Revenue PY], 0)

Deals at Risk = 
COUNTROWS(
    FILTER(
        FactSales,
        FactSales[Stage] <> "Closed Won" &&
        DATEDIFF(FactSales[LastActivityDate], TODAY(), DAY) > 30
    )
)
```

---

## Skills Demonstrated

- Power BI data modelling (star schema, relationships, calculated tables)
- DAX — time intelligence, iterators, CALCULATE, FILTER, DIVIDE
- Dashboard design for multiple stakeholder audiences
- Requirements gathering — translating business questions into visual answers
- Data storytelling — structuring a dashboard so insight is immediate
- Business analysis — identifying the reporting gap and designing the solution

---

## Files in this Repository
