# Requirements Traceability Matrix (RTM)
## HireFlow AI — Portfolio Case Study

**Author:** Rohit Kumar | Business Analyst

---

## 1. Purpose

This matrix shows **sample traceability** from business requirements to user stories and how each need would be validated. It demonstrates BA practice of linking stakeholder needs to testable acceptance criteria.

**Trace path:** Requirement → User Story (Sample) → Validation approach

---

## 2. Sample Traceability Rows

| Req ID | User Story (Sample) | Validation approach |
|--------|---------------------|---------------------|
| BR-009 | Story 1 — User Login | Secure login succeeds; role-based access applied; failed login shows error |
| BR-002 | Story 2 — Candidate Search | AI-ranked list loads; sorted by score; screening time reduced vs manual |
| BR-003 | Story 2 — Candidate Search | Match score 0–100 displayed per candidate |
| BR-017 | Story 7 — Explainable AI Score | Rationale visible; override requires justification |
| BR-018 | Story 8 — Job Requisition | Knockout rules captured on requisition before screening |
| BR-023 | Story 3 — Interview Scheduling | Calendar slots shown; invites sent on confirmation |
| BR-027 | Story 4 — Candidate Evaluation | Scorecard submitted; composite score visible to HR |
| BR-031 | Story 5 — Hiring Dashboard | Executive KPI cards and funnel render for HR Manager |
| BR-033 | Story 5 — Hiring Dashboard | Time-to-hire visible by department and recruiter filter |
| BR-004 | Story 6 — Offer Tracking | Offer sent via portal; status updates through hire stage |
| BR-019 | Story 8 — Job Requisition | Requisition pending until HR approval |
| BR-021 | Story 2 — Candidate Search | Candidate applies via portal; appears in pipeline |
| BR-010 | Story 7 — Explainable AI Score | Override logged in audit trail |
| BR-005 | Story 7 — Explainable AI Score | Bias audit inputs available for compliance review |
| RR-001 | Story 5 — Hiring Dashboard | Funnel counts match pipeline stages in dashboard |
| RR-006 | Story 6 — Offer Tracking | Acceptance rate updates after offer decision |
| BUS-003 | Story 2 — Candidate Search | Auto-filter below threshold unless override |
| BUS-004 | Story 4 — Candidate Evaluation | Offer blocked until minimum panel evaluations complete |

---

## 3. Coverage Notes

| Area | Sample rows | Linked stories |
|------|-------------|----------------|
| Screening & AI | 6 | Stories 2, 7, 8 |
| Workflow & offers | 4 | Stories 6, 8 |
| Scheduling & evaluation | 3 | Stories 3, 4 |
| Reporting | 2 | Story 5 |
| Compliance & audit | 3 | Stories 1, 7 |

