# KPI Definitions & Measurement Framework
## HireFlow AI — Recruitment & Interview Management Platform

| Field | Value |
|-------|-------|
| **Document ID** | KPI-HFA-2026-001 |
| **Version** | 1.0 |
| **Author** | Rohit, Business Analyst |
| **Status** | Approved |
| **Related Documents** | PBI-HFA-2026-001, BC-HFA-2026-001, BRD-HFA-2026-001 |

---

## 1. Purpose

This document defines **30 Key Performance Indicators (KPIs)** for HireFlow AI across hiring efficiency, quality, financial, compliance, and platform health dimensions. Each KPI includes formula, data source, measurement frequency, target, accountable owner, and recommended visualization type.

**Governance:** KPIs are reviewed quarterly by the HR Steering Committee. Targets are calibrated against industry benchmarks (SHRM, LinkedIn Talent Solutions, iCIMS) and the organization's baseline metrics from the Business Case.

---

## 2. KPI Catalog Summary

| Category | Count | Primary Dashboard |
|----------|-------|-------------------|
| Hiring Volume & Pipeline | 6 | Executive, Recruiter |
| Efficiency & Speed | 7 | Executive, HR |
| Quality & Scoring | 5 | Recruiter, HR |
| Offer & Compensation | 5 | HR, Executive |
| Financial & Revenue | 4 | Executive, Finance |
| Compliance & Diversity | 3 | HR |

---

## 3. KPI Definitions

### 3.1 Hiring Volume & Pipeline KPIs

#### KPI-001: Total Applications

| Attribute | Value |
|-----------|-------|
| **Formula** | `COUNT(application_id)` WHERE `applied_at` IN period |
| **Data Source** | `hireflow.applications` |
| **Frequency** | Daily (aggregated weekly/monthly for reporting) |
| **Target** | ≥ 45 applications per open requisition per month |
| **Owner** | VP Talent Acquisition |
| **Visualization** | KPI card with 12-month trend line |
| **Notes** | Baseline: 38 apps/req/month (AS-IS). Target reflects improved employer branding post-launch. |

---

#### KPI-002: Active Pipeline Count

| Attribute | Value |
|-----------|-------|
| **Formula** | `COUNT(application_id)` WHERE `current_stage` NOT IN ('HIRED', 'REJECTED') |
| **Data Source** | `hireflow.applications` |
| **Frequency** | Real-time (refreshed every 4 hours) |
| **Target** | 3–5× open requisition count (healthy pipeline ratio) |
| **Owner** | Talent Acquisition Lead |
| **Visualization** | KPI card with gauge (current vs. capacity) |
| **Notes** | Below 2× indicates sourcing gap; above 8× indicates screening bottleneck. |

---

#### KPI-003: Open Requisitions

| Attribute | Value |
|-----------|-------|
| **Formula** | `COUNT(job_id)` WHERE `status = 'OPEN'` |
| **Data Source** | `hireflow.jobs` |
| **Frequency** | Daily |
| **Target** | ≤ 15% of total annual hiring plan open at any time |
| **Owner** | HR Director |
| **Visualization** | KPI card + bar chart by department |
| **Notes** | For 180 annual hires, target ≤ 27 concurrent open reqs. |

---

#### KPI-004: Hires Completed

| Attribute | Value |
|-----------|-------|
| **Formula** | `COUNT(application_id)` WHERE `current_stage = 'HIRED'` AND `updated_at` IN period |
| **Data Source** | `hireflow.applications` |
| **Frequency** | Weekly / Monthly |
| **Target** | 15 hires/month (180 annual plan ÷ 12) |
| **Owner** | VP HR |
| **Visualization** | KPI card with QTD/YTD bar chart |
| **Notes** | Primary success metric for Executive dashboard. |

---

#### KPI-005: Selection Rate (Yield Rate)

| Attribute | Value |
|-----------|-------|
| **Formula** | `Hired Applications ÷ Total Applications × 100` |
| **Data Source** | `hireflow.applications` |
| **Frequency** | Monthly |
| **Target** | 8–12% (industry benchmark for competitive roles) |
| **Owner** | Talent Acquisition Lead |
| **Visualization** | KPI card with funnel overlay |
| **Notes** | Below 5% may indicate overly broad sourcing; above 15% may indicate too-narrow funnel. |

---

#### KPI-006: Application Source Mix

| Attribute | Value |
|-----------|-------|
| **Formula** | `COUNT(application_id) GROUP BY candidate.source` as % of total |
| **Data Source** | `hireflow.candidates`, `hireflow.applications` |
| **Frequency** | Monthly |
| **Target** | Referral ≥ 25%, LinkedIn ≥ 30%, Career Portal ≥ 20% |
| **Owner** | VP Talent Acquisition |
| **Visualization** | Donut chart with source effectiveness table |
| **Notes** | Referral-sourced candidates have 3.2× higher selection rate per Business Case. |

---

### 3.2 Efficiency & Speed KPIs

#### KPI-007: Time To Hire (TTH)

| Attribute | Value |
|-----------|-------|
| **Formula** | `AVG(hire_date - applied_at)` in days for hired applications |
| **Data Source** | `hireflow.applications` |
| **Frequency** | Weekly |
| **Target** | ≤ 28 days (down from 42-day AS-IS baseline) |
| **Owner** | HR Director |
| **Visualization** | KPI card with sparkline + department heatmap |
| **Notes** | Top Executive KPI. 33% reduction target per Business Case ROI model. |

---

#### KPI-008: Time To Fill (TTF)

| Attribute | Value |
|-----------|-------|
| **Formula** | `AVG(filled_date - posted_date)` in days per job requisition |
| **Data Source** | `hireflow.jobs` |
| **Frequency** | Monthly |
| **Target** | ≤ 35 days (down from 52-day AS-IS) |
| **Owner** | VP Talent Acquisition |
| **Visualization** | Horizontal bar chart by department |
| **Notes** | Distinct from TTH — measures requisition lifecycle, not individual candidate. |

---

#### KPI-009: Time To Interview

| Attribute | Value |
|-----------|-------|
| **Formula** | `AVG(first_interview_date - applied_at)` in days |
| **Data Source** | `hireflow.applications`, `hireflow.interviews` |
| **Frequency** | Weekly |
| **Target** | ≤ 7 days |
| **Owner** | Talent Acquisition Lead |
| **Visualization** | Line chart with recruiter comparison |
| **Notes** | AS-IS baseline: 14 days. AI screening reduces to <3 days for qualified candidates. |

---

#### KPI-010: Time To Offer

| Attribute | Value |
|-----------|-------|
| **Formula** | `AVG(offer_sent_date - final_interview_date)` in days |
| **Data Source** | `hireflow.offers`, `hireflow.interviews` |
| **Frequency** | Monthly |
| **Target** | ≤ 3 business days |
| **Owner** | HR Manager |
| **Visualization** | KPI card with pending queue table |
| **Notes** | AS-IS baseline: 5 days. Directly impacts offer acceptance rate. |

---

#### KPI-011: Recruiter Productivity

| Attribute | Value |
|-----------|-------|
| **Formula** | `Hires per Recruiter per Month` |
| **Data Source** | `hireflow.applications`, `hireflow.users` |
| **Frequency** | Monthly |
| **Target** | ≥ 3 hires/recruiter/month (36 reqs/year ÷ 5 recruiters ÷ 12 × fill rate) |
| **Owner** | Talent Acquisition Lead |
| **Visualization** | Bar chart with team benchmark line |
| **Notes** | AS-IS: 2.4 hires/recruiter/month. AI automation enables 25% productivity gain. |

---

#### KPI-012: Screening Time Saved

| Attribute | Value |
|-----------|-------|
| **Formula** | `(Manual Screening Hours - AI-Assisted Hours) per week` |
| **Data Source** | `hireflow.audit_logs` (AI_DECISION actions), timesheet integration |
| **Frequency** | Weekly |
| **Target** | ≥ 15 hours/recruiter/week saved (65% of 23-hr AS-IS) |
| **Owner** | VP Talent Acquisition |
| **Visualization** | Stacked bar (manual vs. AI-assisted hours) |
| **Notes** | Derived from Business Case: 23 hrs/week manual screening per recruiter. |

---

#### KPI-013: Pipeline Velocity

| Attribute | Value |
|-----------|-------|
| **Formula** | `Stage Transitions per Week ÷ Active Applications` |
| **Data Source** | `hireflow.applications` (stage change audit trail) |
| **Frequency** | Weekly |
| **Target** | ≥ 0.35 transitions/application/week |
| **Owner** | Talent Acquisition Lead |
| **Visualization** | Line chart with stage breakdown |
| **Notes** | Low velocity (<0.15) triggers stalled pipeline alerts. |

---

### 3.3 Quality & Scoring KPIs

#### KPI-014: Average AI Screening Score

| Attribute | Value |
|-----------|-------|
| **Formula** | `AVG(score_value)` WHERE `score_type = 'AI_SCREENING'` |
| **Data Source** | `hireflow.scores` |
| **Frequency** | Weekly |
| **Target** | ≥ 62 (calibrated to org's competency model) |
| **Owner** | Talent Acquisition Lead |
| **Visualization** | Histogram distribution + KPI card |
| **Notes** | Threshold for auto-advance to interview: ≥ 60. |

---

#### KPI-015: Average Interview Score

| Attribute | Value |
|-----------|-------|
| **Formula** | `AVG(COALESCE(panel_score, ai_interview_score))` |
| **Data Source** | `hireflow.scores`, `hireflow.interviews` |
| **Frequency** | Monthly |
| **Target** | ≥ 72 |
| **Owner** | HR Manager |
| **Visualization** | Box plot by department + trend line |
| **Notes** | Composite of AI and panel scores for standardization. |

---

#### KPI-016: Strong Hire Rate

| Attribute | Value |
|-----------|-------|
| **Formula** | `COUNT(recommendation = 'STRONG_HIRE') ÷ Total Evaluated × 100` |
| **Data Source** | `hireflow.scores` |
| **Frequency** | Monthly |
| **Target** | 20–30% of evaluated candidates |
| **Owner** | HR Manager |
| **Visualization** | Donut chart with recommendation breakdown |
| **Notes** | Too high (>40%) may indicate lenient scoring; too low (<10%) indicates quality gap. |

---

#### KPI-017: Interview No-Show Rate

| Attribute | Value |
|-----------|-------|
| **Formula** | `COUNT(status = 'NO_SHOW') ÷ Total Scheduled Interviews × 100` |
| **Data Source** | `hireflow.interviews` |
| **Frequency** | Weekly |
| **Target** | ≤ 8% (down from 14% AS-IS) |
| **Owner** | Talent Acquisition Lead |
| **Visualization** | KPI card with automated reminder effectiveness chart |
| **Notes** | Automated reminders and calendar integration target 40% reduction. |

---

#### KPI-018: 90-Day New Hire Retention Proxy

| Attribute | Value |
|-----------|-------|
| **Formula** | `Hires with Composite Score ≥ 75 ÷ Total Hires × 100` (leading indicator) |
| **Data Source** | `hireflow.scores`, `hireflow.applications` |
| **Frequency** | Quarterly |
| **Target** | ≥ 85% of hires above quality threshold |
| **Owner** | HR Director |
| **Visualization** | Gauge chart with score band breakdown |
| **Notes** | Lagging 90-day retention tracked via HRIS integration (Phase 2). Score proxy validated at r=0.72 correlation. |

---

### 3.4 Offer & Compensation KPIs

#### KPI-019: Offer Acceptance Rate

| Attribute | Value |
|-----------|-------|
| **Formula** | `Accepted Offers ÷ (Accepted + Declined + Expired) × 100` |
| **Data Source** | `hireflow.offers` |
| **Frequency** | Monthly |
| **Target** | ≥ 78% (up from 68% AS-IS) |
| **Owner** | HR Manager |
| **Visualization** | KPI card with trend + offer pipeline funnel |
| **Notes** | Primary driver: reduce time-to-offer (KPI-010). 22% decline rate attributed to slow process. |

---

#### KPI-020: Offer Decline Rate

| Attribute | Value |
|-----------|-------|
| **Formula** | `Declined Offers ÷ (Accepted + Declined) × 100` |
| **Data Source** | `hireflow.offers` |
| **Frequency** | Monthly |
| **Target** | ≤ 22% |
| **Owner** | HR Manager |
| **Visualization** | Bar chart with decline reason breakdown |
| **Notes** | Top decline reasons: competing offer (45%), compensation (30%), role fit (15%). |

---

#### KPI-021: Average Offer Compensation

| Attribute | Value |
|-----------|-------|
| **Formula** | `AVG(total_compensation)` WHERE `status = 'ACCEPTED'` |
| **Data Source** | `hireflow.offers` |
| **Frequency** | Monthly |
| **Target** | Within ±5% of approved salary band midpoint |
| **Owner** | HR Director / Finance |
| **Visualization** | Scatter plot (offer vs. budget) with band overlay |
| **Notes** | Finance approval required for offers >110% of band midpoint. |

---

#### KPI-022: Offer Response Time

| Attribute | Value |
|-----------|-------|
| **Formula** | `AVG(responded_at - sent_at)` in days |
| **Data Source** | `hireflow.offers` |
| **Frequency** | Monthly |
| **Target** | ≤ 4 days average candidate response |
| **Owner** | HR Manager |
| **Visualization** | Distribution histogram with fast/slow bands |
| **Notes** | Offers with >7-day response have 2.1× higher decline rate. |

---

#### KPI-023: Offers Pending Approval

| Attribute | Value |
|-----------|-------|
| **Formula** | `COUNT(offer_id)` WHERE `status = 'PENDING_APPROVAL'` |
| **Data Source** | `hireflow.offers` |
| **Frequency** | Real-time |
| **Target** | ≤ 5 pending at any time; none >48 hours |
| **Owner** | HR Manager |
| **Visualization** | Table with aging highlight + KPI card |
| **Notes** | Power Automate alert triggered at 48-hour threshold. |

---

### 3.5 Financial & Revenue KPIs

#### KPI-024: Cost Per Hire

| Attribute | Value |
|-----------|-------|
| **Formula** | `(Recruiter Labor + Platform Cost + Agency Fees) ÷ Total Hires` |
| **Data Source** | Finance ERP + `hireflow.applications` + `hireflow.payments` |
| **Frequency** | Quarterly |
| **Target** | ≤ $4,200 (down from $6,800 AS-IS) |
| **Owner** | VP HR / Finance |
| **Visualization** | Waterfall chart (cost components) + KPI card |
| **Notes** | 38% reduction target per Business Case. Excludes compensation costs. |

---

#### KPI-025: Monthly Recurring Revenue (MRR)

| Attribute | Value |
|-----------|-------|
| **Formula** | `SUM(monthly_subscription_amount)` for active subscriptions |
| **Data Source** | `hireflow.subscriptions`, `hireflow.payments` |
| **Frequency** | Monthly |
| **Target** | $200K MRR by Month 12 ($2.4M ARR) |
| **Owner** | VP Product / Finance |
| **Visualization** | Line chart with plan tier breakdown |
| **Notes** | SaaS revenue metric for multi-tenant platform business. |

---

#### KPI-026: Customer Churn Rate

| Attribute | Value |
|-----------|-------|
| **Formula** | `Churned Companies in Month ÷ Total Active Companies at Start × 100` |
| **Data Source** | `hireflow.companies`, `hireflow.subscriptions` |
| **Frequency** | Monthly |
| **Target** | ≤ 3% monthly churn |
| **Owner** | VP Product |
| **Visualization** | KPI card with cohort retention curve |
| **Notes** | Enterprise tier target: ≤ 1.5% monthly churn. |

---

#### KPI-027: Platform ARPU (Average Revenue Per User)

| Attribute | Value |
|-----------|-------|
| **Formula** | `MRR ÷ Total Active Recruiter Seats` |
| **Data Source** | `hireflow.subscriptions`, `hireflow.users` |
| **Frequency** | Monthly |
| **Target** | ≥ $350/seat/month (Professional tier) |
| **Owner** | VP Product |
| **Visualization** | Bar chart by plan tier |
| **Notes** | Pricing: Starter $199, Professional $349, Enterprise $599 per seat. |

---

### 3.6 Compliance & Diversity KPIs

#### KPI-028: Compliance Documentation Score

| Attribute | Value |
|-----------|-------|
| **Formula** | `Applications with Complete Evaluation Records ÷ Total Evaluated × 100` |
| **Data Source** | `hireflow.scores`, `hireflow.audit_logs` |
| **Frequency** | Monthly |
| **Target** | ≥ 98% |
| **Owner** | Compliance Officer |
| **Visualization** | Gauge chart with exception table |
| **Notes** | Addresses 3 compliance incidents in past 18 months (Business Case). Complete = score + recommendation + panel notes. |

---

#### KPI-029: Interview Score Variance (Bias Indicator)

| Attribute | Value |
|-----------|-------|
| **Formula** | `STDDEV(panel_score)` grouped by panel member; flag if >15 pts from team mean |
| **Data Source** | `hireflow.scores`, `hireflow.interviews` |
| **Frequency** | Quarterly |
| **Target** | ≤ 10% of panel members flagged per quarter |
| **Owner** | Compliance Officer / HR Director |
| **Visualization** | Box plot by panel member with mean line |
| **Notes** | Leading indicator for evaluation bias. Triggers calibration training. |

---

#### KPI-030: Diversity Pipeline Ratio

| Attribute | Value |
|-----------|-------|
| **Formula** | `% of applications/interviews/offers` across gender, ethnicity categories at each funnel stage |
| **Data Source** | `hireflow.candidates` (voluntary EEO data), `hireflow.applications` |
| **Frequency** | Quarterly |
| **Target** | Pipeline ratios within ±5% at each stage (no significant drop-off) |
| **Owner** | HR Director |
| **Visualization** | 100% stacked bar (funnel stage × demographic) |
| **Notes** | EEOC reporting aligned. Voluntary self-identification; minimum 50 responses for statistical validity. |

---

## 4. KPI Hierarchy & Relationships

```
                    ┌─────────────────────┐
                    │   EXECUTIVE TIER    │
                    │  KPI-004 Hires      │
                    │  KPI-007 Time To Hire│
                    │  KPI-019 Offer Accept│
                    │  KPI-024 Cost Per Hire│
                    │  KPI-025 MRR         │
                    └──────────┬──────────┘
                               │
              ┌────────────────┼────────────────┐
              ▼                ▼                ▼
    ┌─────────────────┐ ┌──────────────┐ ┌─────────────────┐
    │ OPERATIONAL TIER│ │ QUALITY TIER │ │ COMPLIANCE TIER │
    │ KPI-001 Apps    │ │ KPI-014 AI   │ │ KPI-028 Docs    │
    │ KPI-009 TTI     │ │ KPI-015 Intv │ │ KPI-029 Bias    │
    │ KPI-011 Prod    │ │ KPI-016 Strong│ │ KPI-030 Diversity│
    │ KPI-013 Velocity│ │ KPI-017 NoShow│ │                 │
    └─────────────────┘ └──────────────┘ └─────────────────┘
```

---

## 5. Target Setting Methodology

| Method | KPIs Applied | Description |
|--------|-------------|-------------|
| **Baseline Improvement** | KPI-007, 008, 009, 012, 017, 019, 024 | AS-IS metric × improvement factor from Business Case |
| **Industry Benchmark** | KPI-005, 014, 016, 026 | SHRM/iCIMS published benchmarks |
| **Internal SLA** | KPI-010, 022, 023, 028 | Stakeholder-defined service levels from BRD |
| **Revenue Model** | KPI-025, 027 | Financial projections from Business Case |
| **Regulatory** | KPI-028, 029, 030 | EEOC, GDPR, organizational policy requirements |

---

## 6. Reporting Cadence

| Report | Audience | KPIs Included | Frequency | Format |
|--------|----------|---------------|-----------|--------|
| Executive Hiring Scorecard | CEO, VP HR | KPI-004, 007, 019, 024 | Monthly | Power BI + PDF email |
| Recruiter Performance Review | TA Lead, Recruiters | KPI-001, 009, 011, 014, 017 | Weekly | Power BI dashboard |
| HR Operations Report | HR Manager | KPI-019–023, 028 | Bi-weekly | Power BI + approval queue |
| Compliance Dashboard | Compliance Officer | KPI-028, 029, 030 | Monthly | Power BI (restricted) |
| SaaS Revenue Report | Finance, VP Product | KPI-025, 026, 027 | Monthly | Power BI + ERP export |
| Quarterly Business Review | Steering Committee | All 30 KPIs | Quarterly | PPT + live dashboard |

---

## 7. KPI Change Log

| Version | Date | Change | Author |
|---------|------|--------|--------|
| 1.0 | June 2026 | Initial 30 KPI definitions | Rohit |

---

**Author:** Rohit | Business Analyst Portfolio  
**Classification:** Portfolio / Educational  
**Next Review:** September 2026
