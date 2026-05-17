# Business Requirements Document — Sales Performance Dashboard

**Project:** Power BI Sales & Operations Analytics Dashboard  
**Author:** Shanmuga Priya Gnanasekaran  
**Version:** 1.0  
**Date:** 2024  

---

## 1. Business Context

The sales and operations teams were operating without a centralised reporting solution. Weekly performance reporting was produced manually in Excel by individual team leads, resulting in inconsistent numbers, delayed insights and significant time cost.

This BRD captures the requirements gathered through stakeholder interviews and workshop sessions with the Sales Manager, Finance Lead and Executive Sponsor.

---

## 2. Stakeholders

| Stakeholder | Role | Reporting Need |
|---|---|---|
| CEO / Executive team | Strategic oversight | High-level KPIs, trend, forecast |
| Sales Manager | Operational management | Rep performance, pipeline health |
| Finance Lead | Revenue tracking | Revenue vs target, YTD, YoY |
| Sales Representatives | Individual performance | Personal targets, deal status |

---

## 3. Business Requirements

### BR-001 — Single source of truth
**As a** sales manager,  
**I want** one dashboard that all teams refer to,  
**So that** there are no conflicting numbers across Excel files.

**Acceptance criteria:**
- Dashboard connects to a single data source
- All teams access the same version
- Manual Excel reporting process is retired

---

### BR-002 — Executive KPI summary
**As an** executive,  
**I want** to see revenue, pipeline and win rate at a glance,  
**So that** I can assess business health in under 30 seconds.

**Acceptance criteria:**
- KPI cards visible on first page load
- No filtering required to see top-level numbers
- Cards show current period value and variance against target

---

### BR-003 — Pipeline risk visibility
**As a** sales manager,  
**I want** to see deals stalled for 30+ days,  
**So that** I can intervene before they are lost.

**Acceptance criteria:**
- Stalled deals flagged in amber
- Filter available to view stalled deals only
- Deal owner and last activity date visible

---

### BR-004 — Regional drill-down
**As a** sales director,  
**I want** to filter all metrics by region,  
**So that** I can identify underperforming territories.

**Acceptance criteria:**
- Region slicer applies across all visuals simultaneously
- Map visual shows geographic distribution
- Regional variance against target clearly visible

---

### BR-005 — Time period comparison
**As a** finance lead,  
**I want** to compare this year's revenue against prior year,  
**So that** I can report growth accurately to the board.

**Acceptance criteria:**
- YoY comparison available on trend page
- YTD figure shown alongside prior YTD
- Growth percentage calculated automatically

---

## 4. Non-Functional Requirements

| Requirement | Detail |
|---|---|
| Performance | Dashboard pages load within 3 seconds |
| Usability | Non-technical users can navigate without training |
| Maintainability | DAX measures documented and data model maintained |
| Security | Row-level security — reps see only their own data |

---

## 5. Out of Scope

- Real-time streaming data (daily refresh is sufficient)
- Mobile-optimised layout (desktop only for Phase 1)

---

## 6. Sign-off

| Role | Name | Status |
|---|---|---|
| Executive Sponsor | — | Approved |
| Sales Manager | — | Approved |
| BA / Project Lead | Shanmuga Priya Gnanasekaran | Completed |
