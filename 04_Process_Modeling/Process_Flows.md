# Process Flow Documentation
## HireFlow AI — AI-Powered Recruitment & Interview Management Platform

| Field | Value |
|-------|-------|
| **Document ID** | PF-HFA-2026-001 |
| **Version** | 1.0 |
| **Author** | Rohit, Business Analyst |
| **Status** | Approved |
| **Related Documents** | BRD-HFA-2026-001, BC-HFA-2026-001, PRJ-HFA-2026-001 |
| **Date** | June 8, 2026 |

---

## 1. Document Purpose

This document defines the current-state (AS-IS) and future-state (TO-BE) hiring processes for HireFlow AI. It provides detailed step-by-step flows, ASCII diagrams, role assignments, SLAs, and business rules for the core workflows: Hiring, Interview, Offer, and Candidate Lifecycle.

**Audience:** Business stakeholders, product owners, developers, QA, and compliance reviewers.

**Process Requirement Traceability:** PR-001 through PR-010 (BRD Section 6).

---

## 2. Process Legend

| Symbol | Meaning |
|--------|---------|
| `[ ]` | Manual task / human action |
| `{ }` | System-automated task |
| `< >` | Decision point / gateway |
| `( )` | Start / end event |
| `>>>` | Handoff between roles or systems |
| `---` | Process boundary / stage separator |

| Role Abbreviation | Full Role |
|-------------------|-----------|
| HM | Hiring Manager |
| HR | HR Manager |
| REC | Recruiter |
| PNL | Interview Panel |
| CAN | Candidate |
| SYS | HireFlow AI System |
| FIN | Finance |
| CMP | Compliance |

---

## 3. AS-IS Process — Current Manual Hiring

### 3.1 High-Level AS-IS Overview

The current hiring process is fragmented across email, legacy ATS (Taleo), spreadsheets, SharePoint, and Zoom. Data is duplicated, decisions lack audit trails, and recruiters spend 23 hours per week on manual resume screening.

```
(AS-IS START)
    |
    v
[Hiring Manager submits requisition via email/form]
    |
    v
[HR Manager reviews & approves manually] -----> (Rejection: return to HM)
    |
    v
[Recruiter posts job to career site + job boards manually]
    |
    v
[Candidates apply via email, ATS, referrals — multiple channels]
    |
    v
[Recruiter downloads resumes to SharePoint folder]
    |
    v
[Recruiter manually reads each resume — 23 hrs/week]
    |
    v
<Qualified?> ---No---> [Send rejection email manually]
    |
   Yes
    |
    v
[Phone screen — recruiter schedules via 6+ email exchanges]
    |
    v
[Panel interviews scheduled manually — calendar conflicts common]
    |
    v
[Interviews conducted on Zoom — no structured scorecard]
    |
    v
[Panel submits feedback via email/verbal — subjective, inconsistent]
    |
    v
[HR Manager consolidates feedback in Excel]
    |
    v
<Hire decision?> ---No---> [Manual rejection — often delayed]
    |
   Yes
    |
    v
[Offer letter drafted in Word — 1.5 days avg]
    |
    v
[Multi-level approval via email chain — 3-5 days]
    |
    v
[Offer sent via email attachment]
    |
    v
<Candidate accepts?> ---No---> [Restart or close req]
    |
   Yes
    |
    v
[Manual handoff to onboarding — data re-entered in HRIS]
    |
    v
(AS-IS END)
```

### 3.2 AS-IS Process Metrics

| Stage | Avg. Duration | Primary Owner | Key Pain Point |
|-------|---------------|---------------|----------------|
| Requisition approval | 3–5 business days | HR Manager | Email-based, no SLA tracking |
| Job posting | 1–2 days | Recruiter | Duplicate entry across channels |
| Resume collection | Ongoing | Recruiter | Multiple intake channels, duplicates |
| Resume screening | 23 hrs/week/recruiter | Recruiter | 75% unqualified; fatigue & bias |
| Phone screen | 45 min/candidate | Recruiter | No standardized rubric |
| Interview scheduling | 4.5 hrs/requisition | Recruiter | 6.2 email exchanges per slot |
| Panel interview | 1.5 hrs/candidate | Panel | Inconsistent questions |
| Evaluation | 2.1 hrs/candidate | HR + Panel | 31% score variance; no audit trail |
| Offer preparation | 1.5 days | HR Manager | Manual templates |
| Offer approval | 3–5 days | HR + VP | Email chain delays |
| **Total time-to-hire** | **42 days** | — | **22% offer decline rate** |

### 3.3 AS-IS Detailed Step Descriptions

#### Stage 1: Requisition & Approval

| Step | Actor | Action | Output | Issues |
|------|-------|--------|--------|--------|
| 1.1 | HM | Submits headcount request and job description via email or HR portal | Requisition request email | No standardized template |
| 1.2 | HR | Reviews budget, headcount, and job description completeness | Approval or rejection email | 3–5 day turnaround; no visibility |
| 1.3 | REC | Receives approved requisition; creates job posting manually | Job posting draft | Data re-entry from approval email |

#### Stage 2: Sourcing & Application

| Step | Actor | Action | Output | Issues |
|------|-------|--------|--------|--------|
| 2.1 | REC | Posts to company career page, LinkedIn, Indeed manually | Live job postings | Inconsistent formatting |
| 2.2 | CAN | Applies via email, ATS form, or referral | Resume + cover letter | Duplicate profiles across channels |
| 2.3 | REC | Downloads applications to SharePoint; no deduplication | Resume folder | Version chaos; no parsing |

#### Stage 3: Screening & Evaluation

| Step | Actor | Action | Output | Issues |
|------|-------|--------|--------|--------|
| 3.1 | REC | Reads each resume against job requirements subjectively | Shortlist spreadsheet | 23 hrs/week; inconsistent criteria |
| 3.2 | REC | Conducts phone screen; notes in email/Word | Phone screen notes | No scoring rubric |
| 3.3 | REC | Coordinates panel availability via email | Scheduled interview | 6+ emails per slot; no-shows untracked |
| 3.4 | PNL | Conducts interview on Zoom; verbal feedback | Informal feedback | No scorecard; bias risk |
| 3.5 | HR | Consolidates panel feedback in Excel | Hire/no-hire recommendation | 31% score variance |

#### Stage 4: Offer & Close

| Step | Actor | Action | Output | Issues |
|------|-------|--------|--------|--------|
| 4.1 | HR | Drafts offer letter from Word template | Offer draft | 1.5 days preparation |
| 4.2 | HR/VP | Approves offer via email chain | Approved offer | 3–5 days for offers >$150K |
| 4.3 | REC | Sends offer to candidate via email | Signed offer (maybe) | 22% decline due to slow process |
| 4.4 | HR | Manually enters hire data into Workday | Employee record | Data re-entry errors |

---

## 4. TO-BE Process — With HireFlow AI

### 4.1 High-Level TO-BE Overview

HireFlow AI automates resume parsing, AI screening, interview scheduling, structured evaluation, and offer workflows within a single multi-tenant SaaS platform with full audit trails and compliance controls.

```
(TO-BE START)
    |
    v
{HM creates requisition in HireFlow AI}
    |
    v
{SYS routes to HR Manager for approval workflow}
    |
    v
<HR approves?> ---No---> {SYS notifies HM with comments}
    |
   Yes
    |
    v
{SYS publishes job to company career portal + integrations}
    |
    v
{CAN self-registers and applies online}
    |
    v
{SYS parses resume in <30 sec; extracts skills, experience, education}
    |
    v
{SYS runs AI screening — scores 0-100 with explainable rationale}
    |
    v
<Score >= 40 & knockout pass?> ---No---> {SYS auto-rejects OR REC overrides with justification}
    |
   Yes
    |
    v
{SYS ranks candidates; REC reviews top matches}
    |
    v
{SYS sends AI interview invitation — async video}
    |
    v
{CAN completes AI interview; SYS transcribes & scores responses}
    |
    v
<AI interview pass?> ---No---> {SYS advances to rejection with notification}
    |
   Yes
    |
    v
{SYS suggests top 5 interview slots from calendar integration}
    |
    v
{CAN selects slot; SYS sends calendar invites to panel + candidate}
    |
    v
{PNL conducts interview; completes digital scorecard within 24 hrs}
    |
    v
{SYS aggregates panel scores; flags variance >1.5 points}
    |
    v
<Min 2 evaluations & composite pass?> ---No---> {REC/HR reject with audit trail}
    |
   Yes
    |
    v
{HR generates offer from template; SYS routes approval workflow}
    |
    v
<Offer approved?> ---No---> {SYS returns to HR with approver comments}
    |
   Yes
    |
    v
{SYS sends offer to candidate; tracks acceptance}
    |
    v
<Candidate accepts?> ---No---> {SYS logs decline; REC notified}
    |
   Yes
    |
    v
{SYS marks candidate Hired; triggers HRIS integration hook}
    |
    v
{SYS updates dashboards — time-to-hire, cost-per-hire, funnel KPIs}
    |
    v
(TO-BE END)
```

### 4.2 TO-BE Process Metrics (Target)

| Stage | Target Duration | Automation Level | Improvement |
|-------|-----------------|------------------|-------------|
| Requisition approval | < 1 business day | 80% | Workflow routing, SLA alerts |
| Job publishing | < 1 hour | 95% | Auto-publish on approval |
| Resume parsing | < 30 seconds | 100% | NLP extraction |
| AI screening | < 10 min (500 resumes) | 85% | Batch processing |
| AI interview | 30 min (candidate self-serve) | 70% | Async video + auto-scoring |
| Interview scheduling | < 15 minutes | 90% | Calendar integration |
| Panel evaluation | < 24 hours post-interview | 60% | Digital scorecards |
| Offer approval | < 1 business day | 75% | Multi-level workflow |
| **Total time-to-hire** | **≤ 23 days** | — | **45% reduction** |

### 4.3 TO-BE Value Drivers

| Driver | AS-IS | TO-BE | Business Rule Reference |
|--------|-------|-------|-------------------------|
| Screening time | 23 hrs/week | ≤ 5 hrs/week | BR-002, BUS-003 |
| Scheduling time | 4.5 hrs/req | ≤ 0.5 hrs | BR-023, BR-025 |
| Evaluation consistency | 31% variance | Standardized rubrics | BR-027, BUS-004 |
| Compliance | 3 incidents/18 mo | Audit-ready logs | BR-010, BUS-008 |
| Offer decline rate | 22% | ≤ 12% | BO-07 |

---

## 5. Hiring Workflow

### 5.1 Hiring Workflow Diagram

```
                    HIRING WORKFLOW — REQUISITION TO PIPELINE
                    ==========================================

(HM: Create Requisition)
         |
         v
    +----+----+
    | Draft   |  HM enters: title, description, requirements,
    | Job Req |  salary band, department, knockout rules
    +----+----+
         |
         v
    {SYS: Validate completeness}
         |
         v
    <All required fields?> ---No---> [HM completes missing fields]
         |
        Yes
         |
         v
    {SYS: Route to HR Manager}
         |
         v
    +----+----+
    | Pending |  SLA: 24 hours (escalation at 48 hrs)
    | Approval|
    +----+----+
         |
         v
    <HR approves?> ---No---> {SYS: Return to HM with comments}
         |                        |
        Yes                        v
         |                   [HM revises & resubmits]
         v
    {SYS: Publish to career portal}
         |
         v
    {SYS: Notify assigned recruiter}
         |
         v
    +----+----+
    |  Open   |  Status: Accepting Applications
    |   Job   |  Auto-close: configurable days or on fill
    +----+----+
         |
         v
    {CAN: Apply online}
         |
         v
    {SYS: Parse resume + AI screen}
         |
         v
    +----+----+
    | Pipeline|  Stages: Applied → Screened → AI Interview →
    | Active  |  Panel Interview → Evaluation → Offer
    +----+----+
         |
         v
    <Req open > 45 days?> ---Yes---> {SYS: Escalation to HR + HM}
         |
        No
         |
         v
    (Continue to Interview / Offer workflows)
```

### 5.2 Hiring Workflow Step Descriptions

| Step ID | Step Name | Primary Actor | System Action | Business Rules | SLA |
|---------|-----------|---------------|---------------|----------------|-----|
| HW-01 | Create Requisition | HM | Validates required fields; saves draft | BUS-010 (knockout rules optional at draft) | — |
| HW-02 | Submit for Approval | HM | Locks requisition; routes to HR queue | BUS-001 | — |
| HW-03 | Review Requisition | HR | Displays budget, headcount, job details | — | 24 hrs |
| HW-04 | Approve / Reject | HR | Updates status; logs audit event | BR-019, FR-AUD-001 | 24 hrs |
| HW-05 | Publish Job | SYS | Generates career portal URL; activates job | BR-020, FR-JM-004 | 1 hr post-approval |
| HW-06 | Assign Recruiter | SYS / HR | Notifies recruiter; adds to dashboard | — | Immediate |
| HW-07 | Receive Applications | CAN / SYS | Creates candidate profile; triggers parsing | BR-021, FR-RM-001 | Real-time |
| HW-08 | AI Screening | SYS | Scores, ranks, applies knockout rules | BUS-003, PR-004 | < 30 sec/resume |
| HW-09 | Pipeline Management | REC | Reviews ranked list; bulk actions available | BR-037, PR-008 | Ongoing |
| HW-10 | Requisition Aging Alert | SYS | Escalates if open > 45 days | PR-005 | Day 45 |

### 5.3 Hiring Workflow Roles (RACI Summary)

| Activity | HM | HR | REC | SYS |
|----------|----|----|-----|-----|
| Create requisition | R/A | C | I | — |
| Approve requisition | I | R/A | I | C |
| Publish job | I | A | I | R |
| Manage pipeline | C | A | R | C |
| Close requisition | C | A | R | C |

*R = Responsible, A = Accountable, C = Consulted, I = Informed*

---

## 6. Interview Workflow

### 6.1 Interview Workflow Diagram

```
                 INTERVIEW WORKFLOW — AI + PANEL ROUNDS
                 ========================================

(Candidate in Screened stage — AI score >= threshold)
         |
         v
    {SYS: Generate role-specific AI interview questions}
         |
         v
    {SYS: Send AI interview invitation to candidate}
         |
         v
    +----+----+
    |  AI     |  Duration: 30 min (configurable)
    |Interview|  Practice mode available (optional)
    +----+----+
         |
         v
    {SYS: Record video; transcribe; score 1-5 per rubric}
         |
         v
    {SYS: Generate AI interview summary report}
         |
         v
    <AI score meets threshold?> ---No---> {SYS: Reject + notify CAN & REC}
         |
        Yes
         |
         v
    {SYS: Fetch panel availability (Google/Outlook)}
         |
         v
    {SYS: Suggest top 5 time slots}
         |
         v
    +----+----+
    | Slot    |  CAN selects preferred slot
    |Selection|
    +----+----+
         |
         v
    {SYS: Send calendar invites — panel + candidate}
         |
         v
    {SYS: Reminders at T-24hrs and T-1hr}
         |
         v
    +----+----+
    | Panel   |  Structured digital scorecard
    |Interview|  Weighted criteria; hire/no-hire/undecided
    +----+----+
         |
         v
    <No-show?> ---Yes---> {SYS: Flag incident; offer reschedule (max 3)}
         |
        No
         |
         v
    {PNL: Submit scorecard within 24 hours}
         |
         v
    {SYS: Calculate composite score}
         |
         v
    <Score variance > 1.5?> ---Yes---> {SYS: Flag for HR calibration}
         |
        No
         |
         v
    <Min 2 panel evaluations?> ---No---> {SYS: Hold at interview stage}
         |
        Yes
         |
         v
    <Composite passes threshold?> ---No---> {REC/HR: Reject with justification}
         |
        Yes
         |
         v
    {SYS: Advance to Evaluation → Offer stage}
         |
         v
    (Handoff to Offer Workflow)
```

### 6.2 Multi-Round Interview Support

```
Round 1: AI Async Interview
    |
    v
<Pass?> --No--> Reject
    |
   Yes
    v
Round 2: Technical Panel (parallel interviews supported)
    |
    v
<Pass?> --No--> Reject
    |
   Yes
    v
Round 3: Hiring Manager Final (optional per job family)
    |
    v
<Pass?> --No--> Reject
    |
   Yes
    v
Advance to Offer Workflow
```

**Business Rules:** PR-002 (parallel panel interviews within same stage), BUS-006 (max 3 reschedules per round), BUS-011 (scorecard within 24 hrs).

### 6.3 Interview Workflow Step Descriptions

| Step ID | Step Name | Primary Actor | System Action | Notifications |
|---------|-----------|---------------|---------------|---------------|
| IW-01 | Trigger AI Interview | SYS | Generates questions from job requirements + question bank | Email to CAN |
| IW-02 | Candidate Completes AI Interview | CAN | Records video; real-time transcription | In-app status update |
| IW-03 | AI Scoring | SYS | Scores against rubric; produces summary report | REC dashboard alert |
| IW-04 | AI Pass/Fail Decision | SYS / REC | Auto-advance or reject based on threshold | Email to CAN (pass/fail) |
| IW-05 | Slot Recommendation | SYS | Queries calendar APIs; ranks top 5 slots | — |
| IW-06 | Slot Confirmation | CAN | Confirms selection; triggers calendar invites | Calendar invite (all parties) |
| IW-07 | Interview Reminders | SYS | Sends T-24hr and T-1hr reminders | Email + SMS (optional) |
| IW-08 | Panel Scorecard | PNL | Completes weighted digital scorecard | — |
| IW-09 | Score Aggregation | SYS | Calculates composite; flags variance | HR alert if variance > 1.5 |
| IW-10 | Stage Advancement | SYS / HR | Moves candidate to Evaluation stage | Email to CAN + REC |

### 6.4 Interview Workflow SLAs

| Metric | Target | Escalation |
|--------|--------|------------|
| AI interview invitation sent | Within 4 hrs of screening pass | REC notified if delayed |
| Candidate AI interview completion | Within 7 days of invitation | Auto-reminder day 3, 5 |
| Panel scorecard submission | Within 24 hrs of interview | Reminder at 12 hrs; escalate to HR |
| Reschedule requests | Max 3 per round | Block further reschedules (BUS-006) |
| No-show rate tracking | Flag repeat offenders after 2 incidents | REC review required |

---

## 7. Offer Workflow

### 7.1 Offer Workflow Diagram

```
                    OFFER WORKFLOW — GENERATION TO ACCEPTANCE
                    =========================================

(Candidate in Evaluation stage — all evaluations complete)
         |
         v
    {SYS: Validate evaluations complete}
         |
         v
    <Min 2 panel evaluations?> ---No---> {SYS: Block offer; notify HR}
         |
        Yes
         |
         v
    [HR: Initiate offer generation]
         |
         v
    {SYS: Populate offer template — role, salary, start date, benefits}
         |
         v
    [HR: Review and customize offer details]
         |
         v
    {SYS: Determine approval chain based on salary}
         |
         v
    +----+----+
    | Approval|  Standard: HR Manager
    | Routing |  >$150K: VP HR required (BUS-002)
    +----+----+
         |
         v
    <Salary > $150K?> ---Yes---> {SYS: Route to VP HR}
         |                              |
        No                               v
         |                         <VP approves?> ---No---> Return to HR
         v                              |
    <HR approves?> ---No---> Return to HR |
         |                              |
        Yes                             Yes
         |                              |
         +----------+-------------------+
                    |
                    v
            {SYS: Mark offer Approved}
                    |
                    v
            {SYS: Send offer to candidate}
                    |
                    v
            {SYS: Start acceptance countdown — configurable expiry}
                    |
                    v
            <CAN accepts within expiry?> ---No---> {SYS: Mark Expired/Declined}
                    |                                    |
                   Yes                                   v
                    |                              [REC: Pipeline review]
                    v
            {SYS: Mark candidate Hired}
                    |
                    v
            {SYS: Trigger HRIS integration webhook}
                    |
                    v
            {SYS: Close requisition (if headcount filled)}
                    |
                    v
            {SYS: Update KPIs — offer acceptance rate, time-to-hire}
                    |
                    v
            (OFFER WORKFLOW END)
```

### 7.2 Offer Workflow Step Descriptions

| Step ID | Step Name | Primary Actor | System Action | Business Rules |
|---------|-----------|---------------|---------------|----------------|
| OW-01 | Pre-Offer Validation | SYS | Verifies evaluations complete, no open compliance flags | PR-009, BUS-004 |
| OW-02 | Generate Offer | HR | Selects template; enters compensation, start date, benefits | BR-029, FR-JM-008 |
| OW-03 | HR Review | HR | Reviews accuracy; adds conditions if needed | — |
| OW-04 | Route Approval | SYS | Determines approver based on salary threshold | BUS-002, BR-030 |
| OW-05 | VP HR Approval | VP HR | Approves/rejects offers > $150K | BUS-002 |
| OW-06 | HR Manager Approval | HR | Final approval for standard offers | BR-030 |
| OW-07 | Send Offer | SYS | Delivers offer via portal + email; logs timestamp | BR-022 |
| OW-08 | Track Response | SYS | Monitors accept/decline/expire; sends reminders | — |
| OW-09 | Record Hire | SYS | Updates status to Hired; triggers integrations | BR-004 |
| OW-10 | Close Requisition | SYS | Auto-closes job if headcount met | FR-JM-007 |

### 7.3 Offer Approval Matrix

| Offer Value | Approver 1 | Approver 2 | SLA |
|-------------|------------|------------|-----|
| ≤ $150,000 | HR Manager | — | 1 business day |
| > $150,000 | HR Manager | VP HR | 2 business days |
| Executive (C-suite) | HR Manager | VP HR + CHRO | 3 business days |

### 7.4 Offer Outcome Handling

| Outcome | System Action | Next Steps |
|---------|---------------|------------|
| Accepted | Status → Hired; HRIS webhook; close req if filled | Onboarding handoff |
| Declined | Status → Offer Declined; notify REC + HM | Review compensation or pipeline |
| Expired | Status → Offer Expired; notify REC | Extend or regenerate offer |
| Negotiation | Status → Offer Pending; HR updates terms | Re-enter approval if material change |

---

## 8. Candidate Lifecycle

### 8.1 Candidate Lifecycle State Diagram

```
                        CANDIDATE LIFECYCLE — STATE TRANSITIONS
                        ========================================

                              (New Application)
                                     |
                                     v
                              +-------------+
                              |   APPLIED   |  Resume uploaded; parsing queued
                              +------+------+
                                     |
                                     v
                              {Resume parsed}
                                     |
                                     v
                              +-------------+
                              |  SCREENING  |  AI score calculated; knockout check
                              +------+------+
                                     |
                        +------------+------------+
                        |                         |
                   Score < 40                  Score >= 40
                   (no override)                  |
                        |                         v
                        v                  +-------------+
                 +-------------+           |  SCREENED   |  Ranked in pipeline
                 |  REJECTED   |           +------+------+
                 +-------------+                  |
                        ^                         v
                        |                  +-------------+
                        |                  | AI INTERVIEW|  Async video interview
                        |                  +------+------+
                        |                         |
                        |              +----------+----------+
                        |              |                     |
                        |         AI fail               AI pass
                        |              |                     |
                        +--------------+                     v
                                               +-------------+
                                               |   PANEL     |  Live interview scheduled
                                               |  INTERVIEW  |
                                               +------+------+
                                                      |
                                           +----------+----------+
                                           |                     |
                                      Panel fail              Panel pass
                                           |                     |
                                           v                     v
                                    +-------------+      +-------------+
                                    |  REJECTED   |      | EVALUATION  |  Score aggregation
                                    +-------------+      +------+------+
                                                              |
                                                              v
                                                       +-------------+
                                                       |    OFFER    |  Offer generated & sent
                                                       +------+------+
                                                              |
                                           +------------------+------------------+
                                           |                  |                  |
                                      Declined            Expired            Accepted
                                           |                  |                  |
                                           v                  v                  v
                                    +-------------+   +-------------+   +-------------+
                                    |  REJECTED   |   |  WITHDRAWN  |   |   HIRED     |
                                    +-------------+   +-------------+   +-------------+
                                                                           |
                                                                           v
                                                                    (Lifecycle Complete)

                              +-------------+
                              |  ARCHIVED   |  Auto-archive after 90 days inactive (BUS-005)
                              +-------------+
```

### 8.2 Candidate Lifecycle Stages — Detailed Descriptions

| Stage | Entry Criteria | Exit Criteria | Owner | Automated Actions |
|-------|----------------|---------------|-------|-------------------|
| **Applied** | Candidate submits application for open requisition | Resume parsed successfully | SYS | Parse resume; deduplicate profile (BUS-013) |
| **Screening** | Resume parsed; AI screening queued | AI score generated | SYS | Apply knockout rules; bias audit log (FR-AIS-007) |
| **Screened** | AI score ≥ 40 (or recruiter override) | AI interview invitation sent | REC / SYS | Rank in pipeline; highlight matched/missing skills |
| **AI Interview** | Invitation accepted | AI interview completed and scored | CAN / SYS | Transcribe, score, generate summary report |
| **Panel Interview** | AI interview passed | All scheduled panel interviews complete | PNL / SYS | Calendar management; scorecard enforcement |
| **Evaluation** | Min 2 panel scorecards submitted | Composite score calculated; hire decision made | HR | Flag score variance; compliance review if needed |
| **Offer** | Hire decision = Yes; evaluations complete | Offer accepted, declined, or expired | HR | Approval routing; acceptance tracking |
| **Hired** | Offer accepted | HRIS integration complete | HR / SYS | Close requisition; update KPIs |
| **Rejected** | Failed any stage or manual rejection | — | REC / HR | Send rejection notification; retain audit trail |
| **Archived** | 90 days inactive (BUS-005) | DSAR or reactivation | SYS | Data retention per GDPR policy |

### 8.3 Candidate Lifecycle Transitions & Rules

| Transition | Trigger | Authorized Roles | Audit Required |
|------------|---------|------------------|----------------|
| Applied → Screening | Auto on application submit | SYS | Yes — parsing log |
| Screening → Screened | AI score ≥ 40 | SYS | Yes — AI decision log (FR-AUD-005) |
| Screening → Rejected | AI score < 40, no override | SYS | Yes |
| Screened → AI Interview | Recruiter advance or auto-threshold | REC, SYS | Yes |
| AI Interview → Panel Interview | AI pass threshold met | SYS, REC | Yes |
| Panel Interview → Evaluation | All scorecards submitted | SYS | Yes |
| Evaluation → Offer | Hire decision approved | HR | Yes |
| Offer → Hired | Candidate accepts | CAN, SYS | Yes |
| Any → Rejected | Manual or automated rejection | REC, HR | Yes — justification required for override |
| Any → Archived | 90-day inactivity | SYS | Yes — BUS-005 |
| Rejected → Screened | Stage rollback (exception) | HR only | Yes — PR-003, justification mandatory |

### 8.4 Candidate Lifecycle Notifications

| Stage Transition | Recipient | Channel | Template |
|------------------|-----------|---------|----------|
| Applied → Screening | CAN | Email | Application received |
| Screened → AI Interview | CAN | Email + In-app | AI interview invitation |
| AI Interview → Panel Interview | CAN, PNL | Email + Calendar | Interview scheduled |
| Panel Interview → Evaluation | REC | In-app | Scorecards submitted |
| Evaluation → Offer | CAN | Email | Offer extended |
| Offer → Hired | CAN, HR, REC | Email | Welcome / hire confirmation |
| Any → Rejected | CAN | Email | Respectful rejection (BR-022) |

### 8.5 Candidate Data Retention

| Data Type | Retention Period | Policy Reference |
|-----------|------------------|------------------|
| Application & resume | 24 months post-rejection; duration of employment if hired | GDPR, BR-006 |
| AI interview recording | 12 months then auto-delete | BUS-009 |
| Audit logs | 7 years minimum | FR-AUD-004 |
| Archived candidate profiles | 90 days inactive → archive; 24 months → purge (unless hired) | BUS-005, BR-040 |

---

## 9. Cross-Workflow Integration Map

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│ Hiring Workflow │────>│Interview Workflow│────>│ Offer Workflow  │
│  (Requisition)  │     │  (AI + Panel)   │     │  (Approval)     │
└────────┬────────┘     └────────┬────────┘     └────────┬────────┘
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 v
                    ┌────────────────────────┐
                    │  Candidate Lifecycle   │
                    │  (State Management)    │
                    └────────────┬───────────┘
                                 v
                    ┌────────────────────────┐
                    │ Reporting & Analytics  │
                    │ (KPIs, Funnel, SLAs)   │
                    └────────────────────────┘
```

---

## 10. Exception & Escalation Paths

| Exception | Detection | Escalation Path | Resolution |
|-----------|-----------|-----------------|------------|
| AI bias variance > 20% | Monthly bias audit (BUS-015) | Compliance team review | Pause auto-reject; manual review |
| Requisition open > 45 days | SYS timer (PR-005) | HR Manager + HM | Revise req or close |
| Panel score variance > 1.5 | SYS calculation | HR calibration session | Debrief; consensus decision |
| Offer approval delayed > SLA | SYS workflow timer | Escalate to next approver | CHRO override (executive offers) |
| Duplicate candidate detected | SYS deduplication (BR-038) | REC review | Merge profiles; keep highest score (BUS-013) |
| GDPR deletion request | Compliance portal | 72-hour SLA (BR-040) | Purge PII; retain anonymized audit |

---

## 11. Document Approval

| Role | Name | Date | Signature |
|------|------|------|-----------|
| VP Talent Acquisition | _________________ | ___/___/2026 | _________ |
| HR Manager Lead | _________________ | ___/___/2026 | _________ |
| Business Analyst | Rohit | 06/08/2026 | _________ |
| Compliance Officer | _________________ | ___/___/2026 | _________ |

---

## 12. Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 06/08/2026 | Rohit | Initial release — AS-IS, TO-BE, and core workflows |

---

*Document Classification: Internal — Process Documentation*
