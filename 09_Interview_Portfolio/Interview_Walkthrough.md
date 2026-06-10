# 10-Minute Interview Walkthrough
## HireFlow AI — Junior / Associate BA Portfolio

| Field | Value |
|-------|-------|
| **Document ID** | WALK-HFA-2026-001 |
| **Version** | 3.0 |
| **Duration** | 10 minutes |
| **Audience** | Recruiters, hiring managers, BA interviewers |

---

## How to Use This Guide

Follow this **nine-step path** when a reviewer has limited time. Lead with business analysis work — not technical build depth.

**Opening line:**

> "HireFlow AI is a portfolio case study. I documented it end-to-end as a Business Analyst: stakeholders, requirements, process flows, user stories, wireframes, reporting needs, and traceability."

---

## Step 1 — Business Case (1 min)

**File:** [01_Business_Context/Business_Case.md](../01_Business_Context/Business_Case.md)

**Say:** The hiring process is slow and manual. Recruiters spend too much time screening. HR lacks pipeline visibility. The business case frames why change is needed.

**Key line:** "I started with the business problem, not the technology."

---

## Step 2 — Stakeholder Analysis (1 min)

**File:** [02_Stakeholder_Analysis/Stakeholder_Matrix.md](../02_Stakeholder_Analysis/Stakeholder_Matrix.md)

**Say:** Eight stakeholder groups — each with pain points that later became requirements. Recruiters need speed; HR needs visibility; Compliance needs explainable AI.

**Key line:** "Every requirement traces back to a person and a problem."

---

## Step 3 — BRD (1.5 min)

**File:** [03_Business_Requirements/BRD.md](../03_Business_Requirements/BRD.md)

**Say:** Open the BRD structure. Show two or three sample requirements — AI screening, explainable scores, executive reporting.

**Key line:** "This is what the business needs the system to do — before any design or build."

---

## Step 4 — Process Flow (1 min)

**File:** [04_Process_Modeling/Process_Flows.md](../04_Process_Modeling/Process_Flows.md)

**Say:** AS-IS pain vs TO-BE improvement across screening, scheduling, and evaluation. Process modeling showed where time was lost.

**Key line:** "I mapped the workflow before specifying screens or reports."

---

## Step 5 — User Stories (1 min)

**Files:**
- [05_User_Stories_and_Acceptance/User_Stories.md](../05_User_Stories_and_Acceptance/User_Stories.md)
- [05_User_Stories_and_Acceptance/Acceptance_Criteria.md](../05_User_Stories_and_Acceptance/Acceptance_Criteria.md) *(optional — one Gherkin example)*

**Say:** Read one user story aloud. Show how acceptance criteria make it testable.

**Key line:** "Stories translate business rules into deliverable, testable units."

---

## Step 6 — Figma Screens (1.5 min)

**Files:**
- [07_UX_Prototype/Prototype_Demo_Guide.md](../07_UX_Prototype/Prototype_Demo_Guide.md)
- Screenshots in [assets/screenshots/](../assets/screenshots/)

| Screen | Image |
|--------|-------|
| Login | `login-screen.png` |
| Recruiter Dashboard | `recruiter-dashboard.png` |
| Candidate List | `candidate-list.png` |
| Candidate Details | `candidate-details.png` |
| Job Requisition | `job-requisition.png` |
| Reports Dashboard | `reports-dashboard.png` |

**Say:** Walk through 2–3 screens. Wireframes show how requirements become a usable recruiter workflow — AI-ranked candidates, explainable scores, pipeline KPIs.

**Key line:** "I don't build production UI — I specify what users need to see and do."

---

## Step 7 — Dashboard (1 min)

**Files:**
- [assets/dashboard/executive-hiring-dashboard.png](../assets/dashboard/executive-hiring-dashboard.png)
- [08_Data_and_Reporting/Dashboard_Overview.md](../08_Data_and_Reporting/Dashboard_Overview.md)
- [08_Data_and_Reporting/KPI_Definitions.md](../08_Data_and_Reporting/KPI_Definitions.md) *(one KPI definition if asked)*

**Say:** One executive dashboard for CHRO and HR leadership. Six KPIs, hiring funnel, department trend, recruiter performance. You defined *what* to measure — not built the BI layer.

**Key line:** "Reporting requirements and KPI definitions drive what leadership needs to see."

---

## Step 8 — RTM (1 min)

**File:** [06_Traceability_and_Validation/RTM.md](../06_Traceability_and_Validation/RTM.md)

**Say:** Show one traceability row — stakeholder need → requirement → user story → validation.

**Key line:** "I can follow the thread from a business need to how we'd accept it."

---

## Step 9 — Presentation (30 sec)

**File:** [09_Interview_Portfolio/Presentation_Deck.md](Presentation_Deck.md)

**Say:** Offer to present slides if they prefer. Close with resume bullets from [Resume_Project_Section.md](Resume_Project_Section.md).

**Close:** "Happy to deep-dive into one requirement chain, one process flow, or one screen."

---

## Quick Reference — Folder Map

| # | Step | Folder |
|---|------|--------|
| 1 | Business Case | `01_Business_Context/` |
| 2 | Stakeholders | `02_Stakeholder_Analysis/` |
| 3 | BRD | `03_Business_Requirements/` |
| 4 | Process Flow | `04_Process_Modeling/` |
| 5 | User Stories | `05_User_Stories_and_Acceptance/` |
| 6 | Figma Screens | `07_UX_Prototype/` + `assets/screenshots/` |
| 7 | Dashboard | `08_Data_and_Reporting/` + `assets/dashboard/` |
| 8 | RTM | `06_Traceability_and_Validation/` |
| 9 | Presentation | `09_Interview_Portfolio/` |

---

## Do Not Lead With

| Topic | Why |
|-------|-----|
| ROI / NPV / payback figures | Sounds like Finance or PM |
| Full SQL library, DDL, ERD | Archived — sounds like DBA |
| FRD, SRS, Power BI DAX | Archived — sounds like Architect / BI developer |
| Jira backlog, risk register, release plan | Archived — sounds like PM / Scrum Master |
| Requirement ID labels on dashboards | Interviewers want business metrics, not traceability codes on visuals |

**Depth topics** (SRS, full SQL, UAT cases): mention verbally if asked — not published in this repository.

---

*10-minute path for Junior / Associate BA interviews*
