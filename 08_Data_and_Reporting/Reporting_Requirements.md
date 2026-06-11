# Reporting Requirements
## HireFlow AI — Portfolio Case Study

**Author:** Rohit Kumar | Business Analyst

**Parent BRD:** [BRD.md](../03_Business_Requirements/BRD.md)

---

## 1. Purpose

This document defines **what** stakeholders need to measure, **who** consumes each report, and **when** it is needed — from a Business Analyst perspective.

**Related artifacts:**

| Artifact | Role |
|----------|------|
| [KPI_Definitions.md](KPI_Definitions.md) | Core KPI formulas and sample values |
| [Dashboard_Overview.md](Dashboard_Overview.md) | Executive dashboard layout and metrics |
| [Business_SQL_Examples.md](Business_SQL_Examples.md) | Sample validation queries |
| [API_Analysis.md](API_Analysis.md) | Integration points for reporting data |

---

## 2. Reporting Stakeholders

| Persona | Primary Reports | Decision Supported |
|---------|-----------------|-------------------|
| HR Manager | Pipeline funnel, recruiter performance | Operational oversight |
| Recruiter | Requisition pipeline | Daily prioritization |
| Compliance | Bias audit summary, audit trail export | Regulatory defensibility |

---

## 3. Core Reporting Requirements

| RR ID | Report | Audience | Frequency | KPI link |
|-------|--------|----------|-----------|----------|
| RR-001 | Hiring Pipeline Funnel | HR Manager | Real-time | KPI 1–4 |
| RR-004 | Recruiter Performance Scorecard | HR Manager | Monthly | KPI 2, 3, 6 |
| RR-006 | Offer Acceptance Rate Trend | HR Manager | Monthly | KPI 5 |
| RR-005 | AI Screening Summary | Compliance | Monthly | Explainability metrics |

---

## 4. Non-Functional Reporting Requirements

| Requirement | Target |
|-------------|--------|
| Dashboard data freshness | Within same business day for operational metrics |
| Report export formats | PDF and CSV |
| Drill-down from KPI to candidate | Up to 3 navigation steps |

---

## 5. Sample Acceptance Criteria

| Given | When | Then |
|-------|------|------|
| HR Manager opens Executive Dashboard | Filters to last quarter | Funnel and time-to-hire reflect filtered period |
| Recruiter views pipeline report | New applications arrive | Applied count updates on dashboard |
| Compliance requests screening summary | HR exports report | AI scores include rationale fields per BR-017 |
