# Wireframes — Summary
## HireFlow AI Prototype (6 Screens)

**Author:** Rohit Kumar | Business Analyst Portfolio Project

This summary describes the six prototype screens documented for the HireFlow AI case study. Screenshots are in [`assets/screenshots/`](../assets/screenshots/).

---

## Screen Overview

| # | Screen | Primary user | Business purpose |
|---|--------|--------------|------------------|
| 1 | Login | Recruiter / HR | Secure enterprise access (SSO) |
| 2 | Recruiter Dashboard | Recruiter | Pipeline KPIs and quick actions |
| 3 | Candidate List | Recruiter | AI-ranked applicants for a requisition |
| 4 | Candidate Details | Recruiter | Score, skills match, explainable AI rationale |
| 5 | Job Requisition | Recruiter | Create requisition with skills and knockout rules |
| 6 | Reports Dashboard | HR Manager | Hiring funnel and conversion metrics |

---

## Screen 1 — Login

- Email/password and enterprise SSO (Google, Microsoft)
- Maps to BR-009 authentication requirements

![Login](../assets/screenshots/login-screen.png)

---

## Screen 2 — Recruiter Dashboard

- Open requisitions, active pipeline, quick links to candidates and new requisition
- Entry point after login

![Recruiter Dashboard](../assets/screenshots/recruiter-dashboard.png)

---

## Screen 3 — Candidate List

- Table of applicants sorted by AI match score
- Recruiter reviews top candidates first (BR-002, BR-003)

![Candidate List](../assets/screenshots/candidate-list.png)

---

## Screen 4 — Candidate Details

- AI score with matched/missing skills
- Explainable rationale and override option (BR-017)
- Application stage stepper

![Candidate Details](../assets/screenshots/candidate-details.png)

---

## Screen 5 — Job Requisition

- Job title, department, skills tags, knockout rules
- Submit routes to HR approval — not published immediately (BUS-001)

![Job Requisition](../assets/screenshots/job-requisition.png)

---

## Screen 6 — Reports Dashboard

- Hiring funnel: Applied → Screened → Interview → Offer → Hired
- Summary KPIs aligned to executive dashboard metrics

![Reports Dashboard](../assets/screenshots/reports-dashboard.png)

---

## Traceability

Each screen traces to requirements in the BRD and sample user stories in `User_Stories_Sample.md`.

*Detailed wireframe specifications and Figma build notes are retained locally for reference.*
