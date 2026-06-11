# Dashboard Overview — Executive Hiring Dashboard
## HireFlow AI — Portfolio Case Study

**Author:** Rohit Kumar | Business Analyst

**Purpose:** Executive dashboard requirements for HR Manager and Hiring Leadership.

**Dashboard preview:** [executive-hiring-dashboard.png](../assets/dashboard/executive-hiring-dashboard.png)

---

## 1. Dashboard Strategy

The portfolio defines **one Executive Hiring Dashboard** for HR Manager and Hiring Leadership.

| Dashboard | User | Business question |
|-----------|------|-------------------|
| **Executive Hiring Dashboard** | HR Manager and Hiring Leadership | "Are we hiring efficiently and moving candidates through the funnel successfully?" |

---

## 2. Contents (9 visuals on one page)

| # | Visual | Type | Business purpose |
|---|--------|------|------------------|
| 1 | Total Candidates | Card | Volume entering the pipeline |
| 2 | Candidates Screened | Card | AI screening throughput |
| 3 | Interviews Completed | Card | Mid-funnel progress |
| 4 | Offers Released | Card | Late-stage pipeline |
| 5 | Offer Acceptance Rate | Card | Offer competitiveness |
| 6 | Time to Hire | Card | End-to-end hiring speed |
| 7 | Hiring Funnel | Funnel chart | Conversion drop-off by stage |
| 8 | Department Hiring Trend | Clustered column | Hiring by team over time |
| 9 | Recruiter Performance | Table | Workload and efficiency comparison |

**Global filters:** Date range, Department, Recruiter

---

## 2.1 Dashboard metrics (Jul 2025 – Jun 2026)

| Metric | Value | Notes |
|--------|-------|-------|
| Total Candidates | **952** | Application records in pipeline |
| Candidates Screened | **729** | AI screening completed |
| Interviews Completed | **102** | Completed interview rounds |
| Offers Released | **52** | Offers sent to candidates |
| Offer Acceptance Rate | **80.0%** | Target: 78% |
| Time to Hire | **23.9 days** | Applied date → hire date (average) |
| Hires | **38** | Candidates with stage = Hired |
| Funnel conversion (Applied → Hired) | **4.0%** | 38 ÷ 952 |

**Hiring funnel stages:** Applied (952) → Screened (729) → Interview (102) → Offer (52) → Hired (38)

**Data scope:** 350 unique candidates · 24 open jobs · 6 recruiters · 12 months

---

## 3. Related artifacts

| Artifact | Role |
|----------|------|
| [KPI_Definitions.md](KPI_Definitions.md) | Formulas and owners |
| [Reporting_Requirements.md](Reporting_Requirements.md) | Report catalog |
| [Business_SQL_Examples.md](Business_SQL_Examples.md) | Sample validation queries |
