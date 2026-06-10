# API Analysis — Integration Requirements
## HireFlow AI — BA Portfolio Summary

| Field | Value |
|-------|-------|
| **Document ID** | API-BA-HFA-2026-001 |
| **Purpose** | Document **integration needs** from a Business Analyst view — not API development |
| **Full specification** | [`_archive/Data_and_Reporting_Full/API_Documentation.md`](../_archive/Data_and_Reporting_Full/API_Documentation.md) (52 endpoints) |

---

## 1. BA Scope for API Analysis

Business Analysts define:
- **What** systems must integrate
- **Which data** crosses boundaries
- **Who** consumes each integration
- **When** sync is required (real-time vs batch)

This document summarizes integration domains. Detailed JSON schemas are archived.

---

## 2. Integration Landscape

| Domain | Business Need | Stakeholder | Key Requirements |
|--------|---------------|-------------|------------------|
| Authentication | Enterprise SSO login | Company Admin | BR-009, FR-AUTH-004/005 |
| Candidate | Apply, upload resume, track status | Candidate, Recruiter | BR-021, FR-RM-001 |
| Screening | AI score and ranking | Recruiter | BR-002, BR-003 |
| Interview | Schedule, scorecard, AI interview | Recruiter, Panel | BR-023–027 |
| Reporting | Dashboard data, exports | HR Manager, Finance | BR-031, RR-001–015 |
| Admin | Users, tenants, audit | Super Admin, Compliance | BR-010, BR-040 |

---

## 3. API Domains (Summary)

### 3.1 Authentication (12 endpoints)
- Register, login, refresh, MFA, SAML/OIDC SSO
- **BA note:** SSO required for enterprise tenants; MFA mandatory per security policy

### 3.2 Candidate (13 endpoints)
- CRUD candidates, resume upload, apply to job, merge duplicates, search
- **BA note:** Resume upload triggers parsing workflow (BR-015); duplicate merge (BR-038)

### 3.3 Interview (12 endpoints)
- Schedule, reschedule, AI interview start/responses, scorecard submit
- **BA note:** Calendar integration external dependency (Google/Outlook)

### 3.4 Reporting (10 endpoints)
- Dashboard, pipeline funnel, time-to-hire, cost-per-hire, EEOC export
- **BA note:** Maps directly to Reporting Requirements RR-001–015

### 3.5 Admin (10 endpoints)
- Tenant management, user provisioning, billing, audit log export
- **BA note:** Audit export supports compliance DSAR (BR-040)

---

## 4. External System Integrations

| External System | Integration Type | BA Requirement |
|-----------------|------------------|----------------|
| Google Calendar | OAuth + API | FR-SCH-001 — panel availability |
| Microsoft Outlook | OAuth + API | FR-SCH-001 |
| Stripe | Payment webhook | FR-BIL-002 — subscription billing |
| OpenAI | ML API | FR-AIS-001 — AI screening (vendor) |
| Workday HRIS | REST (Phase 2) | Headcount validation for approvals |

---

## 5. Data Flows (BA View)

```
Candidate Portal ──apply/resume──→ Candidate API ──→ Parsing ──→ AI Screening API
                                        │
Recruiter UI ──review/rank──────────────┘
        │
        ├──→ Interview API ──→ Calendar (external)
        ├──→ Report API ──→ Dashboard (KPIs)
        └──→ Admin API ──→ Audit Log (Compliance)
```

---

## 6. Non-Functional Integration Requirements

| ID | Requirement | Target |
|----|-------------|--------|
| API-NFR-001 | Response time | < 500ms (P95) |
| API-NFR-002 | Authentication | JWT Bearer, 15-min token |
| API-NFR-003 | Multi-tenancy | `X-Tenant-ID` header isolation |
| API-NFR-004 | Rate limiting | Tier-based (300–1200 req/min) |
| API-NFR-005 | Error format | Standard JSON envelope |

---

## 7. Interview Talking Points

- "I identified 5 integration domains and 52 endpoints to support 155 requirements."
- "Reporting APIs directly implement RR-001 through RR-006 for the executive dashboard."
- "I documented external dependencies — calendar, Stripe, HRIS — as integration risks in the business case."

---

*BA integration summary | Full REST specification in archive*
