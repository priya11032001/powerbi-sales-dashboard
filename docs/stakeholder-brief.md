# Stakeholder Brief — Dashboard Design Decisions

**Project:** Power BI Sales & Operations Dashboard  
**Author:** Shanmuga Priya Gnanasekaran  

This document explains what each dashboard page was designed for, who uses it, and the design decisions made based on stakeholder feedback.

---

## Page 1 — Executive Summary

**Designed for:** CEO, General Manager, Board  
**Time budget:** 30 seconds  

**Design decisions:**
- No slicers or filters — executives should not have to interact to get their answer
- Four KPI cards only: Revenue YTD, Pipeline Value, Win Rate, Deals Closing This Month
- Large font, high contrast — readable on a projected screen in a boardroom
- Trend sparkline on each card shows direction at a glance

**Stakeholder feedback:**
> "I don't want to have to click anything. I just want to open it and know if we're on track." — CEO

---

## Page 2 — Sales Performance by Region

**Designed for:** Sales Director, Regional Managers  
**Time budget:** 5–10 minutes  

**Design decisions:**
- Region slicer on left — first thing a regional manager does is filter to their territory
- Map visual gives geographic intuition
- Bar chart ranked by revenue descending — problem regions immediately obvious
- % vs target shown as green/amber/red — no mental calculation required

**Stakeholder feedback:**
> "I need to know which regions are behind before the Monday call." — Sales Director

---

## Page 3 — Pipeline Analysis

**Designed for:** Sales Manager, Sales Team  
**Time budget:** Daily check, 5 minutes  

**Design decisions:**
- Funnel chart chosen — conversion loss at each stage is visually obvious
- Deals at Risk table prominently placed — most actionable insight on this page
- Amber highlighting on 30+ day stall — not red, deal is at risk not lost yet
- Deal owner column included — accountability is immediate

**Stakeholder feedback:**
> "I need to know which deals need a nudge before they go cold." — Sales Manager

---

## Page 4 — Trend Analysis

**Designed for:** Finance Lead, Sales Director  
**Time budget:** Weekly review, 15 minutes  

**Design decisions:**
- 12-month rolling line chart — enough history to see seasonality
- Prior year overlay in muted colour — current year stands out, prior year is context
- YoY % annotated directly on chart — no mental calculation needed
- Forecast line as dotted extension — shows trajectory if trend continues

**Stakeholder feedback:**
> "I need to show the board whether this year is better than last year." — Finance Lead

---

## Page 5 — Rep Performance

**Designed for:** Sales Manager, Individual Sales Reps  
**Time budget:** Weekly 1:1 meetings  

**Design decisions:**
- Row-level security applied — reps only see their own row when logged in
- Manager view shows all reps — toggled by role not slicer
- Green/amber/red conditional formatting against target
- Sparkline per rep shows 6-month trend — not just where they stand today

**Stakeholder feedback:**
> "I don't want my reps comparing themselves to each other in the meeting." — Sales Manager

---

## Key Design Principles Applied

1. Design for the audience not the data — each page strips away everything that audience does not need
2. Make the insight obvious — colour, position and size guide the eye to what matters
3. Reduce cognitive load — if a user has to calculate something mentally, the dashboard has failed
4. Respect the time budget — executives get 30-second pages, analysts get 15-minute pages
