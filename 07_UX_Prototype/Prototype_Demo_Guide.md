# Prototype Demo Script — 6 Screens
## HireFlow AI | One-Page Interview Walkthrough

| Field | Value |
|-------|-------|
| **Document ID** | DEMO-HFA-2026-002 |
| **Duration** | 5–6 minutes |
| **Prerequisite** | Figma prototype built per [Figma_Implementation_Package.md](Figma_Implementation_Package.md) |
| **GitHub screenshots** | [assets/screenshots/](../assets/screenshots/) (six PNGs for interview walkthrough) |
| **Starting frame** | `01 — Login` |

**Opening (15 sec):**  
> "This is a clickable Figma prototype — not production UI. I built it to show how requirements from the BRD and user stories become screens recruiters and HR would actually use."

---

## Demo Flow

| # | Click | Screen | Time | Say this | Point at | Requirements |
|---|-------|--------|------|----------|----------|--------------|
| 1 | **Sign In** | Login | 30s | "Recruiters need secure access. SSO buttons reflect enterprise login — I captured that in the BRD, not as a design preference." | Google / Microsoft SSO | BR-009 · FR-AUTH-003 · US-AUTH-003 |
| 2 | *(lands on Dashboard)* | Recruiter Dashboard | 45s | "Main pain point: no pipeline visibility. These four KPIs and the funnel come from reporting requirements — open reqs, active pipeline, time-to-hire, offer acceptance." | KPI cards + funnel chart | BR-031, BR-033 · US-JOB-010 · RR-001 · KPI-006 |
| 3 | **+ New Requisition** | Job Requisition | 45s | "Every hire starts with a documented requisition. Knockout rules and required skills map to BR-018. Submit goes to HR for approval — that's BUS-001, not publish yet." | Skills tags, knockout checkboxes, Submit button | BR-019, BR-018 · US-JOB-001 · BUS-001 |
| 4 | *(back via prototype or sidebar)* **Candidates** or table row **Sr. Developer** | Candidate List | 60s | "This is the core workflow change — AI ranks 42 applicants by match score. Recruiter reviews top matches first instead of reading every resume. Default sort is score descending." | Score badges, Rank column, 8/10 skills | BR-002, BR-003 · US-AIS-001, US-AIS-005 |
| 5 | **Alex Chen** row | Candidate Details | 75s | "Compliance needed explainable AI — every score has a rationale. Skills grid shows matched vs missing. If the recruiter disagrees, Override opens a justification field — that's BUS-003 for audit." | AI rationale quote, skills ✅/❌, Override Score | BR-017, BR-005 · US-AIS-004, US-AIS-007 · BUS-003 |
| 6 | Sidebar **Reports** | Reports Dashboard | 45s | "HR tracks hiring health from reporting requirements — funnel conversion, applied vs hired. I defined what to measure in KPI definitions; this screen shows what the dashboard needs to display." | Funnel chart, Applied 842 / Hired 38 / 4.5% | BR-031 · US-RPT-001, US-RPT-002 · RR-001, RR-002 |

**Close (15 sec):**  
> "Six screens trace back to the BRD, user stories, and RTM. I can open any requirement ID and show the chain to acceptance criteria. Happy to go deeper on one screen or the traceability matrix."

---

## Click Path (set in Figma)

```
Login → Sign In → Dashboard → + New Requisition → (Submit toast) → Dashboard
                              → Candidates → Alex Chen → (Back optional)
                              → Reports
```

**If short on time:** Skip step 3 (Job Requisition). Go Dashboard → Candidates → Details → Reports.

**If extra time:** On P4, open Override modal and read validation message aloud.

---

## Before You Present

| Check | ✓ |
|-------|---|
| Prototype opens on Login frame | |
| All 6 hotspots tested (Sign In, New Req, Candidates, row, Reports) | |
| Sticky notes with BR/US IDs visible on frames | |
| Backup: [assets/screenshots/](../assets/screenshots/) or [Wireframes.md](Wireframes.md) | |

---

## If Asked

| Question | Answer + show |
|----------|---------------|
| "Where's HR approval?" | "After Submit on Job Requisition — BUS-001. HR Approval Queue is out of scope for this 6-screen demo; it's documented in process flows." |
| "Did you design or build this?" | "I specified wireframes and this Figma plan from requirements. A UX designer would polish visuals; my deliverable is traceable screen requirements." |
| "How do you validate this UI?" | Acceptance criteria in `05_User_Stories_and_Acceptance/` — e.g. US-AIS-004 Gherkin scenarios. |
| "Candidate experience?" | "Candidate apply and AI interview are Phase 2 — annotated in process flows, not in this recruiter-focused prototype." |

---

## Do Not Say

- ROI, NPV, or dollar savings while demoing screens  
- "I built the API / database / Power BI"  
- Exact counts (155 stories, 150 SQL queries)  

---

*One-page script · 6 screens only · Full build spec: Figma_Implementation_Package.md*
