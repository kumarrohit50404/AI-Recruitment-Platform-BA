# Reporting Requirements
## HireFlow AI — Business Analyst Deliverable

| Field | Value |
|-------|-------|
| **Document ID** | RR-HFA-2026-001 |
| **Version** | 1.0 |
| **Author** | Rohit, Business Analyst |
| **Status** | Approved |
| **Parent BRD** | [BRD.md](../04_Business_Requirements/BRD.md) §7 |

---

## 1. Purpose

This document consolidates **reporting and analytics requirements** from a Business Analyst perspective. Modern product-company BAs define **what** stakeholders need to measure, **who** consumes each report, **when** it is needed, and **how** success is judged — then trace those needs to KPIs, dashboards, data entities, and validation queries.

**Related artifacts in this section:**

| Artifact | Role |
|----------|------|
| [KPI_Definitions.md](KPI_Definitions.md) | Measurable indicators with formulas and owners |
| [Dashboard_Mockups.md](Dashboard_Mockups.md) | Layout and interaction requirements per persona |
| [PowerBI_Analytics_Package.md](PowerBI_Analytics_Package.md) | Semantic model and implementation specification |
| [Data_Model.md](Data_Model.md) / [ERD.md](ERD.md) | Data entities supporting reports |
| [SQL_Queries.md](SQL_Queries.md) | Validation and analytics query library |
| [API_Documentation.md](API_Documentation.md) | Report and export API contracts |

---

## 2. Reporting Stakeholders

| Persona | Primary Reports | Decision Supported |
|---------|-----------------|-------------------|
| CHRO / Executive | Executive hiring dashboard | Headcount velocity, cost, diversity |
| HR Manager | Pipeline, approvals, compliance | Operational oversight |
| Recruiter | Requisition pipeline, performance | Daily prioritization |
| Finance | MRR/ARR, cost-per-hire | Revenue and budget |
| Compliance | Bias audit, EEOC, audit trail | Regulatory defensibility |

---

## 3. Reporting Requirements Catalog

*Sourced from BRD RR-001 through RR-015. Each requirement traces to KPI and dashboard artifacts.*

| RR ID | Report | Audience | Frequency | KPI Link | Dashboard |
|-------|--------|----------|-----------|----------|-----------|
| RR-001 | Hiring Pipeline Funnel | HR Manager | Real-time | KPI-002, KPI-003 | Executive, HR |
| RR-002 | Time-to-Hire by Department | CHRO | Weekly | KPI-006 | Executive |
| RR-003 | Cost-per-Hire Analysis | Finance | Monthly | KPI-009 | Executive |
| RR-004 | Recruiter Performance Scorecard | HR Manager | Monthly | KPI-014 | Recruiter |
| RR-005 | AI Screening Accuracy Report | Compliance | Monthly | KPI-018 | HR (compliance tab) |
| RR-006 | Offer Acceptance Rate Trend | HR Manager | Monthly | KPI-011 | HR, Executive |
| RR-007 | Source of Hire Analysis | Recruiter Lead | Monthly | KPI-015 | Recruiter |
| RR-008 | Diversity Hiring Metrics (EEOC) | Compliance | Quarterly | KPI-028 | HR |
| RR-009 | Interview Panel Utilization | HR Manager | Monthly | KPI-016 | HR |
| RR-010 | SaaS Revenue Dashboard (MRR/ARR) | Finance | Real-time | KPI-025, KPI-026 | Executive (finance) |
| RR-011 | Candidate Experience NPS | HR Manager | Quarterly | KPI-021 | HR |
| RR-012 | Bias Audit Summary | Compliance | Monthly | KPI-029 | HR (compliance tab) |
| RR-013 | Subscription Churn Report | Finance | Monthly | KPI-027 | Executive (finance) |
| RR-014 | Open Requisition Aging Report | Recruiter | Weekly | KPI-005 | Recruiter |
| RR-015 | AI Interview Completion Rate | Recruiter | Weekly | KPI-019 | Recruiter |

---

## 4. Non-Functional Reporting Requirements

| ID | Requirement | Target |
|----|-------------|--------|
| RR-NFR-001 | Dashboard data freshness | ≤ 4 hours for operational metrics |
| RR-NFR-002 | Report export formats | PDF, CSV, Excel |
| RR-NFR-003 | Row-level security by tenant | Company-scoped data isolation |
| RR-NFR-004 | Drill-down from KPI to candidate | ≤ 3 clicks |
| RR-NFR-005 | Scheduled email delivery | Configurable per report |
| RR-NFR-006 | Mobile-responsive dashboards | Tablet minimum for HR approvals |

---

## 5. Data Dependencies

Reporting requirements depend on the following data domains (see [Data_Model.md](Data_Model.md)):

```
Applications → Pipeline funnel, time-to-hire, conversion rates
Interviews   → Panel utilization, AI completion, scores
Offers       → Acceptance rate, compensation trends
Scores       → AI accuracy, bias audit inputs
Payments     → MRR/ARR, churn (SaaS)
AuditLogs    → Compliance exports
```

**Traceability:** BR-031 through BR-034 | FR-RPT-001 through FR-RPT-010 | US-RPT-*

---

## 6. Acceptance Criteria (Reporting)

| # | Given | When | Then |
|---|-------|------|------|
| 1 | HR Manager opens Executive Dashboard | Filters to Q2 2026 | Time-to-hire, offer rate, and pipeline KPIs reflect filtered data within 4 hours freshness |
| 2 | Compliance requests EEOC report | HR exports RR-008 report | Adverse impact metrics generated with demographic breakdown per BR-007 |
| 3 | Recruiter views aging report | Requisition open > 45 days | RR-014 highlights escalation per PR-005 |
| 4 | Finance views revenue dashboard | Subscription payment recorded | MRR/ARR updates per RR-010 within one billing cycle |

---

*Document Classification: Internal — Reporting Requirements*
