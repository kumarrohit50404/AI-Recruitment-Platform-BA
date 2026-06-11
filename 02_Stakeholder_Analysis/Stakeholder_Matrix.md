# Stakeholder Analysis Matrix
## HireFlow AI — Portfolio Case Study

**Author:** Rohit Kumar | Business Analyst

---

## 1. Stakeholder Overview

| Stakeholder | Type | Influence | Interest | Primary need |
|-------------|------|-----------|----------|--------------|
| **Recruiter** | Internal / End user | Medium | High | Faster screening, ranked candidates, easy scheduling |
| **HR Manager** | Internal / End user | High | High | Pipeline visibility, approvals, hiring KPIs |
| **Candidate** | External / End user | Low | High | Clear application status, fair process, easy scheduling |
| **Interview Panel** | Internal / End user | Medium | Medium | Structured evaluation, calendar coordination |
| **Compliance** | Internal / Governance | High | High | Explainable AI, audit trail, bias monitoring |

---

## 2. Stakeholder Profiles

### Recruiter

**Pain points:** Manual resume screening takes most of the week; hard to prioritize applicants; scheduling requires many emails.

**Goals:** Review AI-ranked shortlists first; schedule interviews quickly; track requisition pipeline.

**Requirements influenced:** BR-002, BR-003, BR-023, BR-038

---

### HR Manager

**Pain points:** No real-time hiring dashboard; offer approvals slow; inconsistent evaluation across teams.

**Goals:** Monitor funnel and time-to-hire; approve requisitions and offers; compare recruiter performance.

**Requirements influenced:** BR-004, BR-019, BR-031, BR-033, RR-001, RR-004

---

### Candidate

**Pain points:** Unclear application status; long wait between stages; difficult interview scheduling.

**Goals:** Apply online easily; receive stage notifications; self-schedule when possible.

**Requirements influenced:** BR-021

---

### Interview Panel

**Pain points:** Unstructured feedback; calendar conflicts; delayed scorecard submission.

**Goals:** Standard scorecard; clear interview schedule; submit evaluation promptly.

**Requirements influenced:** BR-027, BR-023, BUS-004

---

### Compliance

**Pain points:** Cannot explain AI screening decisions; limited audit evidence; bias risk in hiring.

**Goals:** Explainable AI scores; immutable audit logs; monitoring for adverse impact.

**Requirements influenced:** BR-005, BR-010, BR-017, BUS-003

---

## 3. Stakeholder Conflicts & Resolution

| Conflict | Resolution documented as |
|----------|------------------------|
| Recruiter wants speed vs. Compliance wants explainability | BR-017 explainable rationale + BR-010 audit logs + recruiter override with justification (BUS-003) |
| HR wants dashboards vs. Recruiter wants simple workflow | Separate executive dashboard (BR-031) and recruiter-focused screens in wireframes |

