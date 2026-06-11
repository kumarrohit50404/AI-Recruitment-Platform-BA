# Business Requirements Document (BRD)
## HireFlow AI — Portfolio Case Study

**Author:** Rohit Kumar | Business Analyst

This BRD captures **representative business requirements** for the HireFlow AI recruitment platform case study. Requirements are prioritized using MoSCoW and traceable to stakeholders.

**Priority:** M = Must Have | S = Should Have

---

## 1. Screening & Candidate Management

| ID | Requirement | Priority | Stakeholder |
|----|-------------|----------|-------------|
| BR-002 | Reduce manual resume screening time through AI-assisted ranking | M | Recruiter |
| BR-003 | Rank candidates against job requirements with match scores | M | Recruiter |
| BR-017 | Provide explainable AI rationale for each screening score | M | Compliance |
| BR-018 | Support knockout rules for minimum qualifications on requisitions | M | HR Manager |
| BR-038 | Prevent duplicate candidate profiles across requisitions | S | Recruiter |

---

## 2. Authentication & Access

| ID | Requirement | Priority | Stakeholder |
|----|-------------|----------|-------------|
| BR-009 | Support enterprise SSO login for recruiters and HR users | M | HR Manager |
| BR-010 | Maintain audit logs for critical actions including AI overrides | M | Compliance |

---

## 3. Hiring Workflow

| ID | Requirement | Priority | Stakeholder |
|----|-------------|----------|-------------|
| BR-004 | Support end-to-end workflow from requisition through offer | M | HR Manager |
| BR-019 | Job requisition creation with HR approval before publishing | M | HR Manager |
| BR-021 | Allow candidates to apply online through career portal | M | Candidate |
| BR-023 | Integrate with calendar systems for interview scheduling | M | Recruiter |
| BR-027 | Provide structured digital scorecards for interview evaluation | M | Interview Panel |
| BR-029 | Generate offer letters from templates and track acceptance | M | HR Manager |

---

## 4. Reporting & Analytics

| ID | Requirement | Priority | Stakeholder |
|----|-------------|----------|-------------|
| BR-031 | Provide executive dashboard with core hiring KPIs | M | HR Manager |
| BR-033 | Track time-to-hire by department and recruiter | M | HR Manager |
| RR-001 | Hiring pipeline funnel report (Applied through Hired) | M | HR Manager |
| RR-004 | Recruiter performance comparison report | S | HR Manager |
| RR-006 | Offer acceptance rate trend report | M | HR Manager |

---

## 5. Compliance

| ID | Requirement | Priority | Stakeholder |
|----|-------------|----------|-------------|
| BR-005 | Support AI hiring bias audit and compliance reporting | M | Compliance |
| BR-012 | Reduce average time-to-hire compared to current manual process | M | HR Manager |

---

## 6. Key Business Rules

| ID | Rule |
|----|------|
| BUS-001 | Job requisition must be approved by HR Manager before publishing |
| BUS-003 | AI score below threshold auto-filters candidate unless recruiter overrides with justification |
| BUS-004 | Minimum two panel evaluations required before offer stage |

---

## 7. Sample Non-Functional Requirements

| ID | Requirement | Target |
|----|-------------|--------|
| NFR-001 | Page load time for recruiter screens | Under 3 seconds |
| NFR-011 | New recruiter can complete core tasks after brief onboarding | Same day |
| NFR-012 | Application meets basic accessibility standards | WCAG 2.1 AA (target) |

---

*Representative requirements for portfolio review. Extended requirement catalog retained locally.*
