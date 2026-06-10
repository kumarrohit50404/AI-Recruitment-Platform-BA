# HireFlow AI — Business Analyst Portfolio Presentation

| Field | Value |
|-------|-------|
| **Document ID** | PRES-HFA-2026-002 |
| **Version** | 2.0 (Junior BA Calibrated) |
| **Author** | Rohit, Business Analyst (Portfolio Project) |
| **Format** | PowerPoint / Google Slides (16:9) |
| **Duration** | 12–15 minutes + Q&A |
| **Audience** | Junior / Associate BA hiring managers |
| **Tone** | Analytical, stakeholder-led, requirements-focused — **not** a sales or PM pitch |

**Design system:** Primary `#2563EB` | Text `#0F172A` | Background `#F8FAFC` | Font: Inter or Calibri | Max 6 bullets per slide

**How to use:** Copy each slide block into PowerPoint. Paste speaker notes into Notes pane.

---

## SLIDE 1 — Title

### Slide Title
**HireFlow AI — Requirements-Led Recruitment Transformation**

### Slide Objective
Establish credibility as a Junior/Associate Business Analyst presenting a portfolio case study — not a developer, PM, or product marketer.

### Slide Content

**Subtitle:** Business Analyst Portfolio Case Study

**Project:** AI-Powered Recruitment & Interview Management Platform

**Presented by:** Rohit | Business Analyst  
**Date:** June 2026

**Footer tagline:** From problem discovery → requirements → validation → measurable outcomes

### Visual Recommendation
- Clean title slide: left-aligned title, subtle hiring pipeline icon or abstract flow graphic on right
- No product screenshots — use a simple **BA lifecycle** ribbon: *Discover → Analyze → Specify → Validate → Measure*
- Company-neutral branding (portfolio project)

### Speaker Notes
> "Thank you for the opportunity. Today I'll walk you through HireFlow AI — a portfolio case study for an AI-assisted recruitment platform. This is not a product pitch. I'll focus on how I framed the business problem, engaged stakeholders, documented requirements, modeled processes, defined reporting needs, and traced validation through an RTM. The portfolio — BRD, user stories, process flows, wireframes, and reporting requirements — is in my GitHub repository."

---

## SLIDE 2 — Executive Summary

### Slide Title
**Executive Summary**

### Slide Objective
Give interviewers a 60-second view of the engagement scope, your role, and the business outcome — before diving into detail.

### Slide Content

**The Engagement**
- **Context:** Mid-size organization with manual hiring, legacy ATS, and limited pipeline visibility
- **My role:** Business Analyst (Portfolio Project) — elicitation through UAT support
- **Focus:** Requirements documentation, process improvement, traceability

**What I Delivered**
| Area | Deliverable |
|------|-------------|
| Discovery | Stakeholder interviews, workshop notes, stakeholder matrix |
| Requirements | BRD with business rules, user stories, acceptance criteria |
| Process | AS-IS / TO-BE hiring process flows |
| UX | Wireframes and Figma implementation plan |
| Data & Reporting | KPI definitions, reporting requirements, dashboard needs |
| Validation | RTM linking requirements to stories and UAT scenarios |

**Expected Improvements (from business case)**
- Faster time-to-hire through AI-assisted screening
- Less recruiter time on manual resume review
- Better pipeline visibility for HR leadership
- Audit-ready AI screening decisions for Compliance

### Visual Recommendation
- Three-column layout: *Context* | *BA Deliverables* | *Outcomes*
- Use icons for document types (not technology logos)
- Highlight three qualitative outcome themes (speed, visibility, compliance)

### Speaker Notes
> "At a high level, this portfolio project documents a fragmented hiring operation — too much manual screening, slow scheduling, and weak reporting. I worked across eight stakeholder groups to capture pain points and turn them into documented requirements. My deliverables are what a Junior BA would produce: BRD, user stories, process flows, wireframes, reporting requirements, and traceability through to UAT. The business case outlines expected improvements; I focused on making requirements clear and testable."

---

## SLIDE 3 — Business Problem

### Slide Title
**Business Problem — Why Change Was Required**

### Slide Objective
Demonstrate problem framing skill — quantified pain tied to business impact, not feature wish lists.

### Slide Content

**Core Problem Statement**
> Mid-to-large enterprises spend excessive time and money on manual resume screening, interview coordination, subjective evaluation, and reactive reporting — with compliance and candidate experience risk.

**Quantified Pain**
| Metric | Current State | Business Impact |
|--------|---------------|-----------------|
| Time-to-hire | 42 days avg | Candidates accept competing offers |
| Cost-per-hire | $4,700 | Above industry benchmark |
| Resume screening | 23 hrs/week/recruiter | 75% of resumes unqualified |
| Offer decline rate | 22% | Revenue loss on filled reqs |
| Recruiter turnover | 34% annually | Knowledge loss, retraining cost |
| Compliance incidents | 3 in 18 months | EEOC audit exposure |

**Root Cause (Analysis)**
- Point solutions (ATS, email, Excel, Zoom) operate in silos
- No standardized evaluation or AI-assisted screening
- HR leadership lacks real-time pipeline visibility

### Visual Recommendation
- Problem statement in a highlighted quote box at top
- Red/amber metric callouts for "current state" column
- Simple "silo diagram": 5 disconnected tools with broken arrows between them

### Speaker Notes
> "I didn't start with 'we need AI.' I started with stakeholder interviews and job shadowing. Recruiters told me they spend more than half their week screening resumes that don't qualify. HR couldn't tell you time-to-hire by department without a week of Excel work. Compliance failed an audit because screening decisions weren't documented. I framed the problem as operational inefficiency plus regulatory risk — that justified the business case."

---

## SLIDE 4 — Existing AS-IS Process

### Slide Title
**AS-IS Process — How Hiring Works Today**

### Slide Objective
Show process analysis capability — current-state mapping before proposing any solution.

### Slide Content

**AS-IS Hiring Lifecycle**
```
Requisition (email) → Manual job posting → Resume flood (multi-channel)
    → Manual screening (23 hrs/wk) → Phone screen → Schedule (6+ emails)
    → Panel interview → Subjective feedback → Offer (3–5 day approval)
    → Spreadsheet reporting
```

**Process Characteristics**
| Step | Owner | Tools | Avg. Duration |
|------|-------|-------|---------------|
| Resume screening | Recruiter | Email, ATS, Excel | 23 hrs/week |
| Interview scheduling | Recruiter | Outlook, phone | 4.5 hrs/requisition |
| Evaluation | Panel | Notes, memory | 2.1 hrs/candidate |
| Reporting | HR Manager | Excel | 8 hrs/month |

**Technology Landscape**
- Legacy ATS (Taleo 2018) — no AI, poor UX
- No integrated calendar, scoring, or analytics

### Visual Recommendation
- Horizontal **swimlane flowchart** with 4 lanes: Recruiter | HR Manager | Panel | Candidate
- Use gray/desaturated palette to convey "manual / broken"
- Annotate bottlenecks with clock icons at screening and scheduling steps

### Speaker Notes
> "I mapped the AS-IS process in workshops with five recruiters and two HR managers. The key insight: the process isn't linear — it's a loop of rework. Scheduling alone averages six email exchanges per candidate. Evaluation happens in unstructured notes, so when Compliance asks 'why was this candidate rejected?' there's no defensible record. This AS-IS map became the baseline for every TO-BE improvement metric."

---

## SLIDE 5 — Pain Points

### Slide Title
**Stakeholder Pain Points**

### Slide Objective
Connect empathy and elicitation output to requirements — prove you listen before you specify.

### Slide Content

| Stakeholder | Top Pain Points | Impact |
|-------------|-----------------|--------|
| **Recruiter** | 23+ hrs/week manual screening; 6+ tools; scheduling friction | Burnout, 34% turnover |
| **HR Manager** | No real-time pipeline view; 3–5 day offer approvals | Delayed fills, budget overruns |
| **Interview Panel** | No standard scorecard; 38% late feedback | Inconsistent hiring decisions |
| **Candidate** | Application "black hole"; slow scheduling | 22% offer decline to competitors |
| **Compliance** | No AI decision audit trail; manual DSAR (15+ days) | Regulatory incidents |
| **Finance** | No cost-per-hire visibility; manual invoicing | Limited hiring spend insight |

**Elicitation Methods Used**
- Stakeholder interviews | Workshops | Job shadowing notes | Candidate feedback survey

### Visual Recommendation
- **Stakeholder pain matrix**: Stakeholders on Y-axis, Pain severity (H/M/L) on X-axis
- Pull one verbatim quote per role in speech bubbles (e.g., Recruiter: *"I review 200+ resumes per req"*)
- Color-code by severity

### Speaker Notes
> "Each pain point in this table traces directly to requirements in my BRD. For example, recruiter screening fatigue became BR-002 and BR-003 — AI ranking with 80% screening reduction. Compliance's audit failure became BR-010 — immutable audit logs — and BR-040 — 72-hour DSAR processing. This is how I work: pain point → requirement ID → test case → UAT scenario."

---

## SLIDE 6 — Stakeholder Analysis

### Slide Title
**Stakeholder Analysis**

### Slide Objective
Demonstrate stakeholder management — roles, influence, goals, and how you engaged each group.

### Slide Content

**8 Stakeholder Groups**

| Stakeholder | Interest | Influence | Engagement |
|-------------|----------|-----------|------------|
| Super Admin | Platform governance | High | Weekly steering |
| Company Admin | Tenant setup, SSO | High | Bi-weekly workshops |
| Recruiter | Daily hiring workflow | Medium | UAT participant |
| HR Manager | Approvals, reporting | High | Sprint reviews |
| Interview Panel | Evaluation | Medium | Training sessions |
| Candidate | Application experience | High | Usability testing |
| Finance | Billing, cost visibility | Medium | Monthly reviews |
| Compliance | Audit, GDPR, LL144 | High | Compliance gates |

**Power-Interest Strategy**
- **Manage closely:** Recruiter, HR Manager, Candidate, Company Admin
- **Keep satisfied:** Compliance, Super Admin
- **Monitor:** Finance, Interview Panel

### Visual Recommendation
- Standard **Power/Interest 2×2 grid** with stakeholder names plotted
- Small avatar icons per role
- Bottom strip: "Requirements derived from 8 stakeholder groups → documented in BRD"

### Speaker Notes
> "I used a power-interest grid to plan engagement, not just list names. Recruiters and HR Managers were manage-closely — they owned UAT. Compliance had high influence but participated at gate reviews, not daily standups. This prevented scope churn: when Finance asked for ERP integration in sprint 3, I could point to the charter out-of-scope list and route it to Phase 3."

---

## SLIDE 7 — Business Objectives

### Slide Title
**Business Objectives & Success Metrics**

### Slide Objective
Show you define measurable success criteria upfront — the BA accountability for outcomes.

### Slide Content

| ID | Objective | Baseline | Target | Timeline |
|----|-----------|----------|--------|----------|
| BO-01 | Reduce time-to-hire | 42 days | ≤ 23 days | 12 months |
| BO-02 | Lower cost-per-hire | $4,700 | ≤ $3,055 | 12 months |
| BO-03 | Increase recruiter productivity | 36 reqs/yr | 50+ reqs/yr | 6 months |
| BO-04 | Improve candidate NPS | 32 | ≥ 65 | 9 months |
| BO-05 | Compliance audit pass rate | — | ≥ 95% | Ongoing |
| BO-06 | AI screening accuracy | — | ≥ 92% | MVP launch |
| BO-07 | Reduce offer decline rate | 22% | ≤ 12% | 12 months |

**Success Definition**
- Objectives are **SMART** and traceable to KPIs (KPI-006, KPI-009, KPI-011, KPI-021)
- UAT sign-off tied to BO-01 and BO-05 achievement

### Visual Recommendation
- **Scorecard table** with baseline → target arrows (green for improvement direction)
- Right sidebar: "Every objective maps to ≥1 KPI and ≥1 UAT scenario"
- Avoid vanity metrics — emphasize operational and compliance measures

### Speaker Notes
> "As BA, I co-authored these objectives with the VP of Talent Acquisition and CHRO sponsor. Notice they're measurable — not 'improve hiring.' Time-to-hire has a number. Compliance has a pass rate. I linked each objective to KPIs in my reporting framework so HR could track progress without asking IT for a custom report every month."

---

## SLIDE 8 — Scope

### Slide Title
**Project Scope — In & Out**

### Slide Objective
Prove scope management discipline — what you included, excluded, and phased.

### Slide Content

**In Scope (MVP — Q3 2026)**
- Authentication & RBAC (8 roles, SSO, MFA)
- Resume upload, parsing, AI screening & ranking
- Job requisition workflow with HR approval
- Interview scheduling with calendar integration
- Recruiter dashboard & core reporting

**Phase 2 (Q4 2026)**
- AI asynchronous interviews | Panel scorecards | Offer management | HR executive dashboard

**Phase 3 (Q1 2027)**
- Billing/subscription | Advanced analytics | Compliance automation | API marketplace

**Out of Scope**
| Item | Rationale |
|------|-----------|
| Post-hire onboarding | Separate HRIS initiative |
| Native mobile apps | Responsive web in Phase 1 |
| On-premise deployment | Cloud SaaS model only |
| Background check execution | Third-party integration hook only |

**Constraints:** MVP timeline | NYC LL144, GDPR, EEOC compliance | Phased delivery

### Visual Recommendation
- **Three-phase roadmap strip** (MVP → Phase 2 → Phase 3) with feature chips
- Red "Out of Scope" box below — shows boundary control
- MoSCoW legend: Must / Should / Could priorities on user stories

### Speaker Notes
> "Scope management was important for this case study. I documented what belongs in MVP versus later phases — screening and scheduling first, then AI interviews and offers. Explicit out-of-scope items like onboarding and payroll kept the requirements focused. Each exclusion has a documented rationale, which is how I'd support change control on a real project."

---

## SLIDE 9 — Solution Overview

### Slide Title
**Solution Overview — What the Platform Delivers**

### Slide Objective
Describe the solution at a **requirements level** — capabilities and workflows, not a product demo.

### Slide Content

**HireFlow AI — Capability Map (BA View)**

| Capability | Solves (Pain Point) | Key Requirement |
|------------|---------------------|-----------------|
| AI Resume Screening | 23 hrs/week manual review | BR-002, BR-003 |
| Explainable Ranking | Compliance audit gap | BR-017, BR-036 |
| Interview Scheduling | 6+ email exchanges | BR-023, BR-025 |
| Digital Scorecards | 38% late panel feedback | BR-027, BR-028 |
| Executive Dashboards | 8 hrs/month Excel reporting | BR-031, BR-033 |
| Audit & DSAR | 3 compliance incidents | BR-010, BR-040 |

**End-to-End Workflow (Capability Chain)**
```
Apply → Parse → AI Screen → AI Interview → Schedule Panel → Evaluate → Offer → Hire
         ↑__________________ Notifications & Audit at every stage __________________↑
```

**Multi-Tenant SaaS:** Isolated company environments | Subscription tiers | RBAC for 8 roles

### Visual Recommendation
- **Capability matrix** (table above) — not a system architecture diagram
- Simple linear workflow across the slide bottom with capability labels under each stage
- Neutral blue icons per capability — avoid "salesy" product mockups

### Speaker Notes
> "I'm describing capabilities, not selling features. Each row ties a business pain to a requirement ID in the BRD. The platform is multi-tenant SaaS — that shaped data isolation and reporting needs. I stay at the 'what the system must do' level here; the BRD and user stories carry the behavioral detail, and the data section documents entity and reporting requirements."

---

## SLIDE 10 — TO-BE Process

### Slide Title
**TO-BE Process — Transformed Hiring Workflow**

### Slide Objective
Show process improvement thinking — contrast AS-IS with automation, standardization, and visibility.

### Slide Content

**TO-BE Hiring Lifecycle**
```
Requisition (system) → Auto-publish → AI parse & rank → Recruiter reviews Top-10
    → AI pre-screen interview → Self-service scheduling → Digital scorecards
    → Composite score → Offer workflow → Real-time dashboards
```

**Process Improvements**

| Step | AS-IS | TO-BE | Improvement |
|------|-------|-------|-------------|
| Screening | 23 hrs/week manual | AI-ranked shortlist in <10 min | **−80%** effort |
| Scheduling | 6+ emails | Calendar-suggested slots | **−90%** coordination |
| Evaluation | Subjective notes | Rubric scorecards | Standardized |
| Reporting | Monthly Excel | Real-time KPI dashboards | Continuous |
| Compliance | Undocumented | Immutable audit + bias reports | Audit-ready |

**Target:** 42-day time-to-hire → **23 days**

### Visual Recommendation
- Side-by-side **AS-IS (gray) vs TO-BE (blue)** swimlane — same format as Slide 4 for direct comparison
- Green improvement badges on TO-BE lane (−80%, −90%)
- Animate left-to-right if presenting live (optional)

### Speaker Notes
> "The TO-BE process isn't 'add AI everywhere.' It's targeted automation: AI handles volume screening; humans handle judgment calls. Recruiters still override AI scores — but with documented justification per BR-017. Scheduling moves to self-service for candidates. Every state change triggers a notification and an audit log entry. This process model was validated in BPMN walkthroughs with process owners."

---

## SLIDE 11 — BRD Highlights

### Slide Title
**BRD Highlights — Requirements at a Glance**

### Slide Objective
Demonstrate requirements structure and prioritization — show depth without reading the full BRD aloud.

### Slide Content

**BRD Structure (BRD-HFA-2026-001)**

| Category | Purpose | Example IDs |
|----------|---------|-------------|
| Business Requirements (BR) | What the business needs | BR-001 to BR-040 |
| Functional Requirements (FR) | System behavior | FR-AUTH, FR-AIS, FR-RPT… |
| Non-Functional (NFR) | Performance, security, compliance | NFR-001… |
| Business Rules (BUS) | Policy encoded in requirements | BUS-001: HR approval before publish |
| Process Requirements (PR) | Workflow rules | Sequential hiring stages |
| Reporting Requirements (RR) | Stakeholder reports | RR-001: Pipeline funnel |

*All categories MoSCoW prioritized*

**Sample Business Requirements**
- **BR-002:** Reduce screening time ≥ 80% *(Recruiter)*
- **BR-005:** NYC Local Law 144 AI bias compliance *(Compliance)*
- **BR-012:** Time-to-hire 42 → 23 days *(CHRO)*
- **BR-017:** Explainable AI rationale for every score *(Compliance)*
- **BR-031:** Executive dashboard with real-time KPIs *(HR Manager)*

### Visual Recommendation
- Donut chart: requirement category breakdown (BR | FR | NFR | BUS | PR | RR)
- Highlight box with 5 sample BRs — each tagged with stakeholder source
- Footer: "Full BRD in portfolio → `03_Business_Requirements/BRD.md`"

### Speaker Notes
> "The BRD is my single source of truth for what the business needs. Each requirement has MoSCoW priority and a stakeholder source. In an interview I show structure and depth, then deep-dive one area. If you ask about compliance, I'll walk BR-005 through BR-007 and BR-040 and show traceability to UAT scenarios in the RTM."

---

## SLIDE 12 — Solution Areas (from BRD)

### Slide Title
**Solution Areas — From Business Needs to Capabilities**

### Slide Objective
Show how you grouped business needs into solution areas — BA decomposition, not technical architecture.

### Slide Content

**BRD Solution Areas**

| Area | Business Need | Sample Requirements |
|------|---------------|---------------------|
| Screening & Ranking | Reduce manual resume review | BR-002, BR-003, BR-017 |
| Interview Scheduling | Cut email back-and-forth | BR-023, BR-025 |
| Candidate Evaluation | Standardize panel feedback | BR-027, BR-028 |
| Reporting & Dashboards | Real-time pipeline visibility | BR-031, BR-033 |
| Compliance & Audit | Defensible AI decisions | BR-005, BR-010, BR-040 |
| User Access | Role-based hiring workflows | BR-001, BR-008 |

**Business Rule Example (BUS-003)**
> AI score below 40 auto-rejects unless recruiter overrides with documented justification.

### Visual Recommendation
- **Solution area cards** (2×3 grid) with business need + requirement IDs
- Highlight Screening & Ranking — your deep-dive area
- Small "Must / Phase 2" badges where phased

### Speaker Notes
> "I grouped the BRD into solution areas so stakeholders could discuss hiring capabilities, not technical modules. AI Screening, for example, isn't just 'rank candidates' — it includes explainable scores and audit logging for Compliance. Business rule BUS-003 shows how I encode policy directly in requirements. In a real project, a senior BA or architect might write detailed functional specs; my portfolio stays at the business-requirements level."

---

## SLIDE 13 — User Stories

### Slide Title
**User Stories — Agile Requirements Backlog**

### Slide Objective
Prove agile BA competency — stories with priorities, points, and traceability to business needs.

### Slide Content

**Epic Summary (by hiring workflow)**

| Epic | Phase | Focus |
|------|-------|-------|
| Authentication | MVP | Login, roles, tenant access |
| AI Screening | MVP | Resume ranking, explainable scores |
| Jobs & Requisitions | MVP | Posting, approval workflow |
| Interview Scheduling | Phase 2 | Calendar integration, self-service |
| AI Interview | Phase 2 | Async video, rubric scoring |
| Reporting | Phase 2 | Executive and recruiter dashboards |
| Audit & Compliance | Phase 3 | Bias reports, DSAR fulfillment |

**Sample User Stories**

| ID | Story (abbreviated) | Priority | Points |
|----|---------------------|----------|--------|
| US-AIS-001 | As a Recruiter, I want AI-ranked candidates so I focus on top matches | Must | 5 |
| US-AIS-004 | As Compliance, I want explainable AI rationale for audit defense | Must | 8 |
| US-SCH-004 | As a Candidate, I want self-scheduling to reduce email delays | Should | 5 |
| US-RPT-001 | As HR Manager, I want executive dashboard for real-time KPIs | Must | 8 |

**Acceptance Criteria:** Gherkin format (Given/When/Then) for priority stories

### Visual Recommendation
- **Epic burndown-style bar chart** showing story count per epic (not a sales roadmap)
- 2×2 card layout for sample stories with Priority and Points badges
- Link icon: "Each story traces to BRD requirement via RTM"

### Speaker Notes
> "I translate BRD requirements into user stories the agile team can work from. US-AIS-004 is a good example of compliance driving story creation — explainable AI rationale isn't a nice-to-have, it's a Must because Compliance needs audit defense. Each priority story has Gherkin acceptance criteria that double as UAT conditions. I linked stories back to BRD requirements through the RTM."

---

## SLIDE 14 — Process Modeling

### Slide Title
**Process Modeling — BPMN & Workflow Analysis**

### Slide Objective
Demonstrate formal process documentation — flows and BPMN as BA deliverables.

### Slide Content

**Process Artifacts Delivered**

| Artifact | Coverage |
|----------|----------|
| AS-IS / TO-BE narrative flows | Full hiring lifecycle |
| Hiring, Interview, Offer workflows | Step-level detail |
| Candidate lifecycle states | Applied → Screened → Interview → Offer |
| Process flow diagrams | Screening, Scheduling, Offer Approval |

**BPMN: Resume Screening (Simplified)**
```
[Start] → Upload Resume → Parse → AI Score → <Knockout?> 
    → Yes → Auto-Reject → [End]
    → No → Rank → Recruiter Review → <Override?> → Advance/Reject → [End]
         ↑ Bias Audit Gate (Compliance lane) runs parallel
```

**Key Process Rules (PR)**
- PR-001: Sequential stages: Applied → Screened → Interview → Evaluation → Offer
- PR-005: Escalation when requisition open > 45 days
- PR-010: Compliance review if AI score variance > 20% across demographics

### Visual Recommendation
- Embed **one BPMN diagram** (Resume Screening) — use swimlanes: Candidate | System | Recruiter | Compliance
- Thumbnail grid of process flow diagram names with checkmarks
- Keep diagram readable — max 8–10 nodes on slide

### Speaker Notes
> "Process modeling was how I got recruiter and compliance alignment. The screening flow has a compliance checkpoint for bias audit — that came directly from workshop input. Process requirements PR-001 through PR-010 document workflow rules the system must support. In an interview I'd walk through AS-IS versus TO-BE and show where time is saved and where human review stays."

---

## SLIDE 15 — Data & Reporting Requirements

### Slide Title
**Data & Reporting Requirements**

### Slide Objective
Show modern product-company BA skill — data entities, integration needs, and reporting specifications.

### Slide Content

**Data & Integration (BA scope)**
| Artifact | Purpose |
|----------|---------|
| Conceptual Data Model | Business entities (Job, Candidate, Application, Interview) |
| KPI Definitions | Formulas, owners, refresh frequency |
| Reporting Requirements | What HR and recruiters need to see |
| Dashboard Overview | Persona-based dashboard needs (Executive, Recruiter, HR) |
| Business SQL Examples | Sample queries to validate reporting logic |
| API Analysis | How modules exchange data (integration requirements) |

**Reporting Requirements (RR-001 – RR-015)**
| Report | Audience | Frequency |
|--------|----------|-----------|
| Hiring Pipeline Funnel | HR Manager | Real-time |
| Time-to-Hire by Department | CHRO | Weekly |
| EEOC Adverse Impact | Compliance | Quarterly |
| Recruiter Performance | HR Manager | Monthly |
| MRR/ARR Revenue | Finance | Real-time |

**Data Governance**
- Multi-tenant isolation (`company_id` on all operational tables)
- 7-year audit log retention | GDPR 72-hour DSAR fulfillment

### Visual Recommendation
- **BA data stack**: Entities → KPIs → Reports → Dashboards → Validation
- Right panel: mini reporting requirements table (5 rows)
- Simple entity relationship sketch (Companies, Jobs, Applications, Candidates)

### Speaker Notes
> "As a BA I defined what data we need to capture, what stakeholders need to report on, and how to sanity-check the logic. For example, time-to-hire reporting requires tracking stage transitions on applications — I documented that in the data model and KPI definitions. Sample SQL queries let me verify the formula makes sense. The API analysis summarizes integration needs between modules — I didn't build APIs, I documented what data must flow where."

---

## SLIDE 16 — KPI Framework

### Slide Title
**KPI Framework — Measuring Success**

### Slide Objective
Prove measurement design — KPIs tied to business objectives with formulas and owners.

### Slide Content

**KPI Framework (sample)**

| Category | KPI Examples | Target | Owner |
|----------|--------------|--------|-------|
| Efficiency | Time-to-Hire (KPI-006) | ≤ 23 days | VP Talent Acquisition |
| Efficiency | Screening Hours (KPI-007) | ≤ 5 hrs/week | Recruiter Lead |
| Quality | Offer Acceptance Rate (KPI-011) | ≥ 88% | HR Manager |
| Quality | AI Screening Accuracy (KPI-018) | ≥ 92% | Compliance |
| Financial | Cost-per-Hire (KPI-009) | ≤ $3,055 | Finance |
| Compliance | Bias Audit Pass Rate (KPI-029) | 100% | Compliance |

**Sample KPI Definition — Time-to-Hire**
```
Formula:   AVG(offer_accepted_date − requisition_approved_date)
Source:    hireflow.applications + hireflow.offers
Frequency: Weekly (executive), daily (recruiter)
Dashboard: Executive + HR Manager
```

**Traceability:** BO-01 → KPI-006 → RR-002 → US-RPT-003 → UAT-032

### Visual Recommendation
- **KPI scorecard mockup** with 4 large metric tiles (Time-to-Hire, Cost-per-Hire, Offer Rate, Pipeline Count)
- Formula shown in monospace box for one KPI
- Traceability chain as a horizontal arrow diagram at bottom

### Speaker Notes
> "KPIs aren't dashboard decorations — they're requirements. Each has a formula, data source, owner, and refresh frequency. Time-to-Hire traces back to business objective BO-01, reporting requirement RR-002, and a UAT scenario where HR validates the metric. I documented dashboard needs by persona in the reporting section — the BI team would build from those requirements."

---

## SLIDE 17 — UAT & Validation

### Slide Title
**UAT & Validation — Proving Requirements Were Met**

### Slide Objective
Demonstrate quality assurance from a BA lens — traceability, test coverage, stakeholder sign-off.

### Slide Content

**Validation Framework**

| Layer | Artifact | Purpose |
|-------|----------|---------|
| Traceability | RTM | Req → Story → UAT scenario |
| Acceptance Criteria | Gherkin AC | Testable conditions on priority stories |
| Business Acceptance | UAT Scenarios | Stakeholder sign-off in plain language |
| Validation support | Sample scenarios | Recruiter and HR walkthroughs |

**Sample UAT Scenarios**
| UAT ID | Scenario | Stakeholder |
|--------|----------|-------------|
| UAT-002 | Recruiter completes AI screening 80% faster | Recruiter |
| UAT-014 | Bias audit report generated for Compliance | Compliance |
| UAT-001 | End-to-end company onboarding and first hire | Company Admin |
| UAT-050 | Go-live readiness — all P1 scenarios pass | All |

**Sign-Off Criteria:** All P1 UAT pass | Zero open Critical defects | BO-01 and BO-05 validated

### Visual Recommendation
- **Traceability pyramid**: BRD (base) → User Stories → Test Cases → UAT (apex)
- Green checkmarks on 4 sample UAT scenarios
- RTM snippet screenshot or table (4 rows) showing Req → Story → TC → UAT chain

### Speaker Notes
> "Validation is where requirements prove their value. My RTM maps requirements to user stories to UAT scenarios. UAT-002 validates BR-002 directly: recruiter completes screening faster than the manual baseline. I wrote UAT scenarios in business language so recruiters could walk through them without QA jargon. On a real project, QA would own detailed test cases; my role was traceability and UAT support."

---

## SLIDE 18 — Expected Process Improvements

### Slide Title
**Expected Process Improvements**

### Slide Objective
Close the loop from problem to value — qualitative outcomes a Junior BA can explain.

### Slide Content

**Process Improvements (TO-BE vs AS-IS)**

| Area | AS-IS Pain | Expected Improvement |
|------|------------|----------------------|
| Resume screening | Hours of manual review per week | AI-ranked shortlist; recruiter reviews top matches |
| Interview scheduling | Multiple email exchanges | Self-service slots with calendar integration |
| Panel evaluation | Unstructured notes, late feedback | Digital scorecards with defined criteria |
| HR reporting | Monthly Excel pulls | Dashboard with pipeline and time-to-hire KPIs |
| Compliance | Undocumented screening decisions | Explainable AI scores and audit logging |

**How Success Would Be Measured**
- Time-to-hire tracked via KPI definitions
- Recruiter screening effort compared to baseline
- UAT scenarios confirm workflows work for business users
- Compliance reviews bias audit and DSAR outputs

### Visual Recommendation
- **Before/after comparison table** (AS-IS gray | TO-BE blue)
- Simple icons per improvement area — no financial waterfall
- Footer: "Detailed targets in Business Case and KPI Definitions"

### Speaker Notes
> "I close with expected improvements, not a financial model I'd struggle to defend in an interview. The business case outlines why change matters; my BA work defines what to build and how to validate it. Recruiters should spend less time on unqualified resumes. HR should see pipeline status without Excel. Compliance should have audit trails on AI decisions. UAT and KPIs are how we'd confirm those improvements after launch."

---

## SLIDE 19 — BA Contributions

### Slide Title
**My BA Contributions — What I Owned**

### Slide Objective
Make your personal role unmistakable — this is a portfolio presentation about **your** work.

### Slide Content

**My BA Contributions (Portfolio Project)**

| Phase | My Contribution |
|-------|-----------------|
| **Discover** | Stakeholder interviews, stakeholder matrix, AS-IS process mapping |
| **Analyze** | Business case summary, pain point analysis, scope definition |
| **Specify** | BRD, user stories, acceptance criteria |
| **Model** | AS-IS/TO-BE process flows, wireframes, Figma implementation plan |
| **Data & Report** | Conceptual data model, KPI definitions, reporting requirements, dashboard needs |
| **Validate** | RTM, UAT scenario support, Gherkin acceptance criteria |
| **Communicate** | This presentation and interview walkthrough |

**Tools & Techniques**
- Elicitation: Interviews, workshops, job shadowing notes, surveys
- Modeling: Process flows, user stories, wireframes
- Analysis: MoSCoW prioritization, power-interest grid, traceability matrix
- Validation: Sample SQL for reporting logic, API integration analysis

**Portfolio:** Nine primary folders on GitHub — focused BA artifacts

### Visual Recommendation
- **BA lifecycle wheel** with your name at center and phases around the rim
- Checklist aesthetic — completed items with green ticks
- Avoid team photos — this is individual contribution

### Speaker Notes
> "I want to be clear about my role. This is a portfolio case study — I documented requirements from discovery through UAT support. I didn't write production code, build databases, or create BI dashboards. I defined what stakeholders need, wrote user stories and acceptance criteria, modeled processes, and traced validation through an RTM. You can review any folder in the GitHub portfolio after this session."

---

## SLIDE 20 — Conclusion

### Slide Title
**Conclusion — Key Takeaways**

### Slide Objective
Leave a crisp, memorable close — three takeaways and an invitation to deep-dive.

### Slide Content

**Three Key Takeaways**

1. **Problem-first approach** — Stakeholder pain points documented before specifying any solution
2. **Requirements discipline** — Traceability from business needs → user stories → UAT scenarios
3. **Junior BA breadth** — Elicitation, process modeling, agile specs, reporting requirements, and validation support

**What This Project Demonstrates**
- Core BA skills: stakeholder analysis, BRD, user stories, RTM, UAT support
- Process improvement thinking (AS-IS → TO-BE)
- Reporting and KPI requirements without claiming BI or engineering ownership

**Thank You**
- Portfolio: GitHub → `AI-Recruitment-Platform`
- Deep-dive available: BRD, RTM, Process Models, Data & Reporting section
- **Questions?**

### Visual Recommendation
- Three icon columns for takeaways (magnifying glass | chain link | chart)
- QR code or short URL to GitHub repo (bottom right)
- Clean, minimal — maximum whitespace

### Speaker Notes
> "To summarize: I started with a real hiring problem, engaged eight stakeholder groups, and documented requirements with process flows, user stories, reporting needs, and traceability to UAT. This is how I'd present myself as a Junior or Associate BA — analytical, stakeholder-aware, and honest about scope. I'm happy to deep-dive into the BRD, a process flow, or one RTM chain. What would you like to explore?"

---

## APPENDIX — Presentation Delivery Guide

| Attribute | Recommendation |
|-----------|----------------|
| **Total slides** | 20 |
| **Duration** | 12–15 minutes (≈40 sec/slide; extend Slides 11, 13, 15, 17 if asked) |
| **Deep-dive slides** | 11 (BRD), 13 (Stories), 15 (Reporting), 17 (UAT) — spend 2 min each if asked |
| **Skip if short on time** | Slides 8 (Scope), 14 (Process) — summarize in 30 seconds |
| **Anticipated questions** | "How did you handle AI bias?" → BR-005, US-AIS-004, UAT-014. "How do you prioritize?" → MoSCoW. "Conflicting stakeholders?" → Power-interest grid. "Did you build the database?" → "I documented data and reporting requirements; engineering builds the schema." |

### Slide Build Checklist (PowerPoint)
- [ ] Apply 16:9 widescreen
- [ ] Master slide: logo area blank, footer with slide number
- [ ] Copy speaker notes to Notes pane for each slide
- [ ] Build AS-IS/TO-BE diagrams in Slides 4 and 10 (reuse same template)
- [ ] Add simple entity sketch for Slide 15 from `08_Data_and_Reporting/Data_Model.md`
- [ ] Practice transition: Problem (3–5) → Solution (9–12) → Proof (15–17) → Impact (18–20)

---

*Document Classification: Portfolio — Interview Presentation*  
*Import into PowerPoint: One slide per "SLIDE N" section above*
