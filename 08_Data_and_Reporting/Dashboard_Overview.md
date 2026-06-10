# Dashboard Overview — Executive Hiring Dashboard
## HireFlow AI — BA Portfolio

| Field | Value |
|-------|-------|
| **Document ID** | DASH-BA-HFA-2026-002 |
| **Version** | 3.0 |
| **Purpose** | Executive dashboard requirements for CHRO and HR leadership |
| **Dashboard preview** | [assets/dashboard/executive-hiring-dashboard.png](../assets/dashboard/executive-hiring-dashboard.png) |
| **Archived Power BI build** | [`_archive/Data_and_Reporting_Full/`](../_archive/Data_and_Reporting_Full/) |

---

## 1. Dashboard Strategy

The portfolio defines **one Executive Hiring Dashboard** for CHRO and HR leadership — not separate recruiter or compliance dashboards.

| Dashboard | User | Business question |
|-----------|------|-------------------|
| **Executive Hiring Dashboard** | CHRO, VP TA, HR Manager | "Are we hiring efficiently and moving candidates through the funnel successfully?" |

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

## 3. BA Interview Demo (2 minutes)

1. Open [executive-hiring-dashboard.png](../assets/dashboard/executive-hiring-dashboard.png)
2. Walk through KPI row — define one metric from [KPI_Definitions.md](KPI_Definitions.md) (e.g., Time to Hire)
3. Show hiring funnel — where candidates drop off between Applied and Hired
4. Show recruiter table — who is converting candidates efficiently
5. Reference [Business_SQL_Examples.md](Business_SQL_Examples.md) only if asked how you validated a KPI

**Key line:** "I defined what leadership needs to measure and see — the dashboard reflects reporting requirements, not a BI engineering deliverable."

---

## 4. Related artifacts

| Artifact | Role |
|----------|------|
| [KPI_Definitions.md](KPI_Definitions.md) | Formulas and owners |
| [Reporting_Requirements.md](Reporting_Requirements.md) | Report catalog |
| [Business_SQL_Examples.md](Business_SQL_Examples.md) | Sample validation queries |
| [Data_Model.md](Data_Model.md) | Conceptual data entities |

---

*One dashboard only | Technical Power BI build files archived in `_archive/Data_and_Reporting_Full/power-bi/`*
