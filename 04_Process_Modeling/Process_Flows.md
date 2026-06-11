# Process Flows — HireFlow AI
## AS-IS and TO-BE Hiring Process (Summary)

**Author:** Rohit Kumar | Business Analyst

---

## 1. Purpose

This document summarizes how hiring works today (AS-IS) and how it would improve with HireFlow AI (TO-BE). It supports requirements in the BRD and user stories in the portfolio.

---

## 2. AS-IS Process (Current State)

Recruiting is fragmented across email, legacy ATS, spreadsheets, and video calls.

```
Requisition (email) → HR approval (manual) → Job posted manually
    → Candidates apply via multiple channels
    → Recruiter reads every resume manually (~23 hrs/week)
    → Phone screen → Schedule interviews (email back-and-forth)
    → Panel interviews (unstructured) → Subjective feedback
    → Offer drafted in Word → Multi-level email approval
    → Manual handoff to onboarding
```

**Key problems:** duplicate data entry, slow screening, no pipeline dashboard, inconsistent evaluation, delayed offers.

---

## 3. TO-BE Process (Future State)

HireFlow AI introduces structured workflow with AI assistance and human review.

```
Requisition in system → HR approval workflow → Published to career portal
    → Candidates apply → AI ranks applicants by job match score
    → Recruiter reviews top matches (override with justification if needed)
    → Interview scheduled via calendar integration
    → Panel completes digital scorecard → Composite evaluation score
    → Offer generated from template → Candidate accepts/declines in portal
    → Hire recorded → Metrics flow to executive dashboard
```

**Human-in-the-loop:** Recruiters approve AI recommendations; compliance requires explainable scores and audit trail.

---

## 4. Hiring Funnel (Process View)

| Stage | AS-IS | TO-BE |
|-------|-------|-------|
| Applied | Manual intake | Automated capture from portal |
| Screened | Manual resume read | AI ranking + recruiter review |
| Interview | Email scheduling | Calendar integration + reminders |
| Evaluate | Verbal/email feedback | Digital scorecard |
| Offer | Word doc + email | Template + secure candidate portal |
| Hired | Spreadsheet tracking | System stage + dashboard KPIs |

---

## 5. Process Improvement Focus

1. **Screening** — Replace full manual read with AI-ranked shortlist (BR-002, BR-003)
2. **Scheduling** — Reduce email coordination with integrated availability (scheduling stories)
3. **Evaluation** — Standardize panel feedback with scorecards (Story 4)
4. **Reporting** — Replace Excel with executive hiring dashboard (BR-031, RR-001)
