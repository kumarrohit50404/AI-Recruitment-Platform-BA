# User Stories — Sample Set
## HireFlow AI | Portfolio Case Study

**Author:** Rohit Kumar | Business Analyst

This document shows **eight representative user stories** from the HireFlow AI case study. Each story includes business value and testable acceptance criteria.

---

## Story 1 — User Login

**User Story**  
As an **HR Manager**, I want secure login with role-based access, so that I only see the hiring features relevant to my role.

**Business Value**  
Supports access control requirement BR-009.

**Acceptance Criteria**

```gherkin
Given I am on the login page
When I enter valid credentials
Then I reach the dashboard matching my role and permissions

Given my login fails
When I return to the login page
Then I see a clear error message
```

**Related requirement:** BR-009

---

## Story 2 — Candidate Search (AI-Ranked List)

**User Story**  
As a **Recruiter**, I want to see candidates ranked by AI match score for a job requisition, so that I focus on the most qualified applicants first.

**Business Value**  
Addresses manual screening fatigue and supports BR-002 (reduce screening time).

**Acceptance Criteria**

```gherkin
Given a job requisition has 25 applications with parsed resumes
When AI screening completes
Then each candidate displays a match score from 0 to 100
And the list is sorted by score descending
And I can open a candidate profile from the list

Given a candidate scored below the knockout threshold
When I view the pipeline
Then the candidate is flagged as auto-filtered unless I override with justification
```

**Related requirements:** BR-002, BR-003, BR-017

---

## Story 3 — Interview Scheduling

**User Story**  
As a **Recruiter**, I want to view panel member availability from calendar integration, so that I schedule interviews without manual availability checks.

**Business Value**  
Reduces scheduling delays and email back-and-forth (AS-IS pain point).

**Acceptance Criteria**

```gherkin
Given panel members have connected their calendars
When I open Schedule Interview for a candidate
Then I see available time slots for the next 14 days
And busy times are excluded
And the top 5 slots by combined availability are suggested

When I confirm a slot
Then calendar invites are sent to the panel and candidate
And reminder notifications are scheduled 24 hours and 1 hour before
```

**Related requirement:** BR-023

---

## Story 4 — Candidate Evaluation

**User Story**  
As an **Interview Panel member**, I want to complete a digital scorecard with weighted criteria, so that my evaluation is structured and comparable across candidates.

**Business Value**  
Replaces subjective email feedback with consistent, auditable evaluation.

**Acceptance Criteria**

```gherkin
Given I completed an interview for a candidate
When I open the evaluation scorecard
Then I rate each criterion on the defined scale
And I must submit within 24 hours of the interview

When all required panel evaluations are submitted
Then HR sees a composite score on the candidate profile
And the candidate cannot advance to offer until minimum evaluations are complete
```

**Related requirement:** BR-027 (structured evaluation)

---

## Story 5 — Hiring Dashboard (Executive View)

**User Story**  
As an **HR Manager**, I want to view an executive hiring dashboard with core KPIs and a funnel chart, so that I can monitor hiring health and identify bottlenecks.

**Business Value**  
Gives leadership pipeline visibility (BR-031, BR-033).

**Acceptance Criteria**

```gherkin
Given I am logged in as HR Manager
When I open the Executive Hiring Dashboard
Then I see KPI cards: Total Candidates, Screened, Interviews Completed,
  Offers Released, Offer Acceptance Rate, and Time to Hire
And I see a hiring funnel from Applied through Hired
And I can filter by date range, department, and recruiter

When I review the recruiter performance table
Then I see screened count, interviews, offers, hires, and time-to-hire per recruiter
```

**Related requirements:** BR-031, BR-033, RR-001, RR-004

---

## Story 6 — Offer Tracking

**User Story**  
As an **HR Manager**, I want to send approved offers through a secure link and track acceptance status, so that offer decisions are captured without email ambiguity.

**Business Value**  
Supports faster offer cycle and measurable offer acceptance rate (KPI).

**Acceptance Criteria**

```gherkin
Given a candidate has completed evaluation and approval to offer
When I generate and send an offer via secure link
Then the candidate can accept or decline in the portal
And the offer status updates to Accepted or Declined
And acceptance rate metrics update on the executive dashboard

Given a candidate declines
When they select a decline reason
Then HR and the recruiter are notified
And the reason is stored for reporting
```

**Related requirements:** BR-004, BR-029

---

## Story 7 — Explainable AI Score (Compliance)

**User Story**  
As a **Recruiter**, I want to view an explainable rationale for each AI screening score, so that I understand why a candidate was ranked and can defend the decision to compliance stakeholders.

**Business Value**  
Supports explainable AI and audit requirements (BR-017, BR-010).

**Acceptance Criteria**

```gherkin
Given a candidate has an AI match score
When I open the candidate details screen
Then I see matched and missing skills
And I see a plain-language rationale for the score
When I override the score
Then I must enter a justification
And the override is logged in the audit trail
```

---

## Story 8 — Job Requisition Submission

**User Story**  
As a **Recruiter**, I want to create a job requisition with required skills and knockout rules, so that open roles are documented before candidates apply.

**Business Value**  
Formalizes hiring intake and enables AI screening against defined requirements (BR-018, BR-019).

**Acceptance Criteria**

```gherkin
Given I am creating a new requisition
When I enter title, department, skills, and knockout rules
And I click Submit
Then the requisition routes to HR for approval
And it is not published until approved
```

