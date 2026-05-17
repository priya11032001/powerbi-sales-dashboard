# DAX Measures Library

**Project:** Power BI Sales & Operations Dashboard  
**Author:** Shanmuga Priya Gnanasekaran  

All measures used in this dashboard, grouped by category with plain-English explanations.

---

## Revenue Measures

```dax
Total Revenue = 
SUM(FactSales[DealValue])
```
Sums all deal values in the current filter context. Responds to all slicers.

```dax
Revenue YTD = 
TOTALYTD([Total Revenue], DimDate[Date])
```
Accumulates revenue from Jan 1 of the current year to the selected date.

```dax
Revenue PY = 
CALCULATE(
    [Total Revenue],
    SAMEPERIODLASTYEAR(DimDate[Date])
)
```
Returns revenue for the equivalent period in the prior year — used for YoY comparison.

```dax
YoY Growth % = 
DIVIDE(
    [Total Revenue] - [Revenue PY],
    [Revenue PY],
    0
)
```
DIVIDE used instead of division operator to handle zero gracefully.

```dax
Revenue vs Target % = 
DIVIDE([Total Revenue], SUM(Targets[TargetValue]), 0)
```

---

## Pipeline Measures

```dax
Pipeline Value = 
CALCULATE(
    SUM(FactSales[DealValue]),
    FactSales[Stage] <> "Closed Won" &&
    FactSales[Stage] <> "Closed Lost"
)
```

```dax
Win Rate = 
DIVIDE(
    COUNTROWS(FILTER(FactSales, FactSales[Stage] = "Closed Won")),
    COUNTROWS(FILTER(FactSales, 
        FactSales[Stage] = "Closed Won" || 
        FactSales[Stage] = "Closed Lost"
    )),
    0
)
```
Only counts closed deals in the denominator — open deals are not yet won or lost.

```dax
Deals at Risk = 
COUNTROWS(
    FILTER(
        FactSales,
        FactSales[Stage] <> "Closed Won" &&
        FactSales[Stage] <> "Closed Lost" &&
        DATEDIFF(FactSales[LastActivityDate], TODAY(), DAY) > 30
    )
)
```

```dax
Avg Deal Size = 
AVERAGEX(
    FILTER(FactSales, FactSales[Stage] = "Closed Won"),
    FactSales[DealValue]
)
```
AVERAGEX iterates row by row — more reliable than AVERAGE when filtering is needed.

---

## Time Intelligence Measures

```dax
Revenue Rolling 3M = 
CALCULATE(
    [Total Revenue],
    DATESINPERIOD(DimDate[Date], LASTDATE(DimDate[Date]), -3, MONTH)
)
```

```dax
MoM Change = 
[Total Revenue] - 
CALCULATE([Total Revenue], PREVIOUSMONTH(DimDate[Date]))
```

```dax
Closing This Month = 
CALCULATE(
    COUNTROWS(FactSales),
    FILTER(
        FactSales,
        MONTH(FactSales[CloseDate]) = MONTH(TODAY()) &&
        YEAR(FactSales[CloseDate]) = YEAR(TODAY()) &&
        FactSales[Stage] <> "Closed Won" &&
        FactSales[Stage] <> "Closed Lost"
    )
)
```

---

## Design Notes

- All measures use DIVIDE() instead of / to prevent divide-by-zero errors
- Time intelligence functions require a properly marked date table
- CALCULATE() modifies filter context — the most powerful function in DAX
- FILTER() iterates a table row by row — use only when needed as it is slower
