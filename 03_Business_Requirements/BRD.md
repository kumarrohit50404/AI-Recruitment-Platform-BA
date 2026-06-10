# Business Requirements Document (BRD)
## AI-Powered Recruitment & Interview Management Platform — HireFlow AI

| Field | Value |
|-------|-------|
| **Document ID** | BRD-HFA-2026-001 |
| **Version** | 1.0 |
| **Author** | Rohit, Business Analyst |
| **Status** | Approved |
| **Total Requirements** | 120 |

---

## 1. Document Purpose

This BRD defines business, functional, non-functional, process, and reporting requirements for HireFlow AI. Each requirement is uniquely identified, prioritized (MoSCoW), and traceable to stakeholder sources.

**Priority Legend:** M = Must Have | S = Should Have | C = Could Have | W = Won't Have (this release)

---

## 2. Business Requirements (BR)

| ID | Requirement | Priority | Source |
|----|-------------|----------|--------|
| BR-001 | The system shall support multi-tenant SaaS architecture with complete data isolation per company | M | Super Admin |
| BR-002 | The system shall reduce resume screening time by at least 80% compared to manual process | M | Recruiter |
| BR-003 | The system shall provide AI-powered candidate ranking against job requirements | M | Recruiter |
| BR-004 | The system shall support end-to-end hiring workflow from requisition to offer | M | HR Manager |
| BR-005 | The system shall comply with NYC Local Law 144 AI hiring bias regulations | M | Compliance |
| BR-006 | The system shall comply with GDPR for EU candidate data | M | Compliance |
| BR-007 | The system shall comply with EEOC adverse impact reporting requirements | M | Compliance |
| BR-008 | The system shall provide subscription-based billing with tiered plans | M | Finance |
| BR-009 | The system shall integrate with enterprise SSO (SAML 2.0, OIDC) | M | Company Admin |
| BR-010 | The system shall maintain immutable audit logs for all critical actions | M | Compliance |
| BR-011 | The system shall support 8 distinct user roles with RBAC | M | Company Admin |
| BR-012 | The system shall reduce average time-to-hire from 42 to 23 days | M | CHRO |
| BR-013 | The system shall improve candidate experience NPS from 32 to 65 | S | Candidate |
| BR-014 | The system shall support AI-conducted asynchronous video interviews | M | Recruiter |
| BR-015 | The system shall parse resumes in PDF, DOCX, and TXT formats | M | Recruiter |
| BR-016 | The system shall extract skills, experience, education from parsed resumes | M | Recruiter |
| BR-017 | The system shall score resume-to-job match with explainable AI rationale | M | Compliance |
| BR-018 | The system shall allow knockout rules based on minimum qualifications | M | HR Manager |
| BR-019 | The system shall support job requisition creation with approval workflow | M | HR Manager |
| BR-020 | The system shall publish approved jobs to company career portal | M | Recruiter |
| BR-021 | The system shall allow candidates to self-register and apply online | M | Candidate |
| BR-022 | The system shall send automated notifications at each pipeline stage | M | Candidate |
| BR-023 | The system shall support calendar integration (Google, Outlook) | M | Recruiter |
| BR-024 | The system shall enable self-service interview scheduling for candidates | S | Candidate |
| BR-025 | The system shall auto-suggest interview slots based on panel availability | M | Recruiter |
| BR-026 | The system shall send interview reminders 24 hours and 1 hour before | M | Panel |
| BR-027 | The system shall provide structured digital scorecards for interview evaluation | M | Panel |
| BR-028 | The system shall aggregate panel scores into composite candidate rating | M | HR Manager |
| BR-029 | The system shall support offer letter generation from templates | M | HR Manager |
| BR-030 | The system shall require multi-level approval for offers above threshold | M | HR Manager |
| BR-031 | The system shall provide executive dashboard with real-time hiring KPIs | M | HR Manager |
| BR-032 | The system shall provide recruiter performance analytics | S | HR Manager |
| BR-033 | The system shall track time-to-hire per requisition and department | M | HR Manager |
| BR-034 | The system shall calculate and display cost-per-hire metrics | S | Finance |
| BR-035 | The system shall standardize interview questions by role/level templates | M | Panel |
| BR-036 | The system shall detect and flag potential scoring bias across demographics | M | Compliance |
| BR-037 | The system shall support bulk candidate actions (reject, advance, email) | S | Recruiter |
| BR-038 | The system shall prevent duplicate candidate profiles across requisitions | M | Recruiter |
| BR-039 | The system shall support white-label branding per company tenant | S | Company Admin |
| BR-040 | The system shall process DSAR (data subject access requests) within 72 hours | M | Compliance |

---

## 3. Functional Requirements (FR)

### 3.1 Authentication & Authorization (FR-AUTH)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-AUTH-001 | System shall support email/password registration with email verification | M |
| FR-AUTH-002 | System shall enforce password policy: min 12 chars, upper, lower, number, special | M |
| FR-AUTH-003 | System shall support multi-factor authentication (TOTP, SMS) | M |
| FR-AUTH-004 | System shall support SAML 2.0 SSO for enterprise tenants | M |
| FR-AUTH-005 | System shall support OIDC SSO (Google, Azure AD) | M |
| FR-AUTH-006 | System shall issue JWT tokens with 15-minute access and 7-day refresh expiry | M |
| FR-AUTH-007 | System shall implement RBAC with 8 predefined roles | M |
| FR-AUTH-008 | System shall support custom role creation with granular permissions | S |
| FR-AUTH-009 | System shall lock accounts after 5 failed login attempts for 30 minutes | M |
| FR-AUTH-010 | System shall log all authentication events to audit trail | M |
| FR-AUTH-011 | System shall support password reset via secure email link (expires 1 hour) | M |
| FR-AUTH-012 | System shall support session management with concurrent session limits | S |

### 3.2 User Management (FR-UM)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-UM-001 | Company Admin shall create, edit, deactivate user accounts | M |
| FR-UM-002 | System shall support bulk user import via CSV with validation | M |
| FR-UM-003 | System shall sync users from Active Directory/LDAP | S |
| FR-UM-004 | System shall assign users to departments and hiring teams | M |
| FR-UM-005 | System shall track user license consumption vs. subscription limit | M |
| FR-UM-006 | System shall send welcome email with setup instructions on user creation | M |
| FR-UM-007 | Super Admin shall manage users across all tenant companies | M |
| FR-UM-008 | System shall support user profile with photo, contact, timezone | S |
| FR-UM-009 | System shall enforce seat limits based on subscription tier | M |
| FR-UM-010 | System shall provide user activity log (last login, actions) | S |

### 3.3 Resume Management (FR-RM)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-RM-001 | Candidates shall upload resumes up to 10MB in PDF, DOCX, TXT format | M |
| FR-RM-002 | System shall validate file type and scan for malware before storage | M |
| FR-RM-003 | System shall store resumes in encrypted S3 with tenant isolation | M |
| FR-RM-004 | System shall maintain resume version history per candidate | S |
| FR-RM-005 | Recruiters shall view and download candidate resumes | M |
| FR-RM-006 | System shall support drag-and-drop bulk resume upload by recruiters | S |
| FR-RM-007 | System shall detect and merge duplicate candidate profiles | M |
| FR-RM-008 | System shall redact PII from resumes in panel view until interview stage | S |

### 3.4 Resume Parsing (FR-RP)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-RP-001 | System shall parse resume into structured fields within 30 seconds | M |
| FR-RP-002 | System shall extract: name, email, phone, skills, experience, education | M |
| FR-RP-003 | System shall normalize skill names against taxonomy (500+ skills) | M |
| FR-RP-004 | System shall calculate total years of experience from work history | M |
| FR-RP-005 | System shall flag parsing confidence score per field | S |
| FR-RP-006 | System shall allow manual correction of parsed fields by recruiter | M |
| FR-RP-007 | System shall re-parse resume on new version upload | M |
| FR-RP-008 | System shall support multi-column and infographic resume layouts | S |

### 3.5 AI Screening (FR-AIS)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-AIS-001 | System shall score candidate-job match on 0-100 scale | M |
| FR-AIS-002 | System shall rank candidates per requisition by match score | M |
| FR-AIS-003 | System shall apply knockout rules and auto-reject non-qualifying candidates | M |
| FR-AIS-004 | System shall provide explainable AI rationale for each score | M |
| FR-AIS-005 | System shall weight scoring criteria: skills 40%, experience 30%, education 20%, other 10% | M |
| FR-AIS-006 | Company Admin shall configure custom scoring weights per job family | S |
| FR-AIS-007 | System shall run bias audit comparing scores across demographic groups | M |
| FR-AIS-008 | System shall allow recruiter override of AI score with justification | M |
| FR-AIS-009 | System shall batch-process up to 500 resumes per requisition within 10 minutes | M |
| FR-AIS-010 | System shall highlight matched and missing skills in candidate profile | M |

### 3.6 Job Management (FR-JM)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-JM-001 | Recruiters shall create job requisitions with title, description, requirements | M |
| FR-JM-002 | System shall require HR Manager approval before job goes live | M |
| FR-JM-003 | System shall support job templates by role family | S |
| FR-JM-004 | System shall publish jobs to company career portal with unique URL | M |
| FR-JM-005 | System shall track application count and pipeline per job | M |
| FR-JM-006 | System shall support job cloning from existing requisitions | S |
| FR-JM-007 | System shall auto-close jobs after configurable days or fill | S |
| FR-JM-008 | System shall define salary band and employment type per job | M |

### 3.7 Interview Scheduling (FR-IS)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-IS-001 | System shall display panel member availability from calendar integration | M |
| FR-IS-002 | System shall suggest top 5 interview time slots ranked by availability | M |
| FR-IS-003 | Candidates shall select preferred slot from available options | M |
| FR-IS-004 | System shall send calendar invites to panel and candidate on confirmation | M |
| FR-IS-005 | System shall support rescheduling with automatic notification to all parties | M |
| FR-IS-006 | System shall track no-show incidents and flag repeat offenders | S |
| FR-IS-007 | System shall support multi-round interview scheduling (sequential stages) | M |
| FR-IS-008 | System shall enforce buffer time (15 min) between consecutive interviews | S |

### 3.8 AI Interview (FR-AII)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-AII-001 | System shall generate role-specific interview questions using AI | M |
| FR-AII-002 | System shall conduct asynchronous video interviews with recording | M |
| FR-AII-003 | System shall transcribe candidate responses in real-time | M |
| FR-AII-004 | System shall score responses against rubric criteria (1-5 scale) | M |
| FR-AII-005 | System shall allow recruiter review of AI interview recordings | M |
| FR-AII-006 | System shall limit AI interview to configurable duration (default 30 min) | M |
| FR-AII-007 | System shall provide practice mode for candidates before live AI interview | S |
| FR-AII-008 | System shall detect and flag inappropriate candidate behavior | S |
| FR-AII-009 | System shall support question bank management by Company Admin | M |
| FR-AII-010 | System shall generate AI interview summary report per candidate | M |

### 3.9 Candidate Evaluation (FR-CE)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-CE-001 | Panel shall complete digital scorecard with weighted criteria | M |
| FR-CE-002 | System shall calculate composite score from all panel evaluations | M |
| FR-CE-003 | System shall require minimum 2 panel evaluations before advancement | M |
| FR-CE-004 | System shall flag score variance >1.5 points between panelists | M |
| FR-CE-005 | System shall support hire/no-hire/undecided recommendation per panelist | M |
| FR-CE-006 | HR Manager shall view evaluation summary with all panel feedback | M |
| FR-CE-007 | System shall enforce scorecard completion within 24 hours of interview | S |
| FR-CE-008 | System shall support debrief notes shared among panel members | S |
| FR-CE-009 | System shall maintain evaluation history across requisitions for returning candidates | M |
| FR-CE-010 | System shall anonymize evaluations during calibration sessions | S |

### 3.10 Reporting (FR-RPT)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-RPT-001 | System shall provide executive dashboard with 10 core KPIs | M |
| FR-RPT-002 | System shall show real-time hiring pipeline funnel visualization | M |
| FR-RPT-003 | System shall generate recruiter performance comparison reports | S |
| FR-RPT-004 | System shall export reports in PDF, CSV, and Excel formats | M |
| FR-RPT-005 | System shall support scheduled report delivery via email | S |
| FR-RPT-006 | System shall calculate time-to-hire, cost-per-hire, offer acceptance rate | M |
| FR-RPT-007 | System shall provide department-wise hiring breakdown | M |
| FR-RPT-008 | System shall show monthly hiring trend with YoY comparison | M |
| FR-RPT-009 | System shall generate EEOC adverse impact analysis report | M |
| FR-RPT-010 | System shall provide source-of-hire analytics | S |

### 3.11 Billing & Subscription (FR-BIL)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-BIL-001 | System shall offer 3 subscription tiers: Starter, Professional, Enterprise | M |
| FR-BIL-002 | System shall process payments via Stripe payment gateway | M |
| FR-BIL-003 | System shall support monthly and annual billing cycles | M |
| FR-BIL-004 | System shall auto-generate invoices on billing cycle date | M |
| FR-BIL-005 | System shall handle failed payment retry with 3-attempt dunning | M |
| FR-BIL-006 | System shall prorate charges on mid-cycle plan upgrades | M |
| FR-BIL-007 | System shall enforce feature limits per subscription tier | M |
| FR-BIL-008 | Finance shall access MRR/ARR revenue dashboard | M |
| FR-BIL-009 | System shall support 14-day free trial with auto-conversion | S |
| FR-BIL-010 | System shall send renewal reminder 30 days before contract expiry | M |

### 3.12 Notifications (FR-NOT)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-NOT-001 | System shall send email notifications for 15 defined event types | M |
| FR-NOT-002 | System shall send SMS notifications for interview reminders | S |
| FR-NOT-003 | System shall provide in-app notification center with read/unread status | M |
| FR-NOT-004 | Users shall configure notification preferences per event type | S |
| FR-NOT-005 | System shall support customizable email templates per tenant | M |
| FR-NOT-006 | System shall batch non-urgent notifications into daily digest | S |

### 3.13 Audit Logs (FR-AUD)

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-AUD-001 | System shall log all CRUD operations with user, timestamp, IP, action | M |
| FR-AUD-002 | Audit logs shall be immutable and tamper-evident | M |
| FR-AUD-003 | Compliance shall search and filter audit logs by date, user, action, entity | M |
| FR-AUD-004 | System shall retain audit logs for minimum 7 years | M |
| FR-AUD-005 | System shall log AI screening decisions with input, output, model version | M |
| FR-AUD-006 | System shall export audit logs in CSV and JSON formats | M |

---

## 4. Non-Functional Requirements (NFR)

| ID | Category | Requirement | Target |
|----|----------|-------------|--------|
| NFR-001 | Performance | Page load time | < 2 seconds (P95) |
| NFR-002 | Performance | API response time | < 500ms (P95) |
| NFR-003 | Performance | Resume parsing throughput | 500 resumes in 10 min |
| NFR-004 | Scalability | Concurrent users | 500 per tenant |
| NFR-005 | Scalability | Total platform users | 50,000 |
| NFR-006 | Availability | Uptime SLA | 99.9% |
| NFR-007 | Security | Data encryption at rest | AES-256 |
| NFR-008 | Security | Data encryption in transit | TLS 1.3 |
| NFR-009 | Security | Penetration testing | Annual, zero critical |
| NFR-010 | Security | SOC 2 Type II certification | Before enterprise GA |
| NFR-011 | Usability | New recruiter onboarding | < 2 hours to proficiency |
| NFR-012 | Usability | WCAG 2.1 AA accessibility compliance | Full compliance |
| NFR-013 | Compatibility | Browser support | Chrome, Firefox, Safari, Edge (latest 2 versions) |
| NFR-014 | Compatibility | Mobile responsive | 320px to 2560px viewports |
| NFR-015 | Data | Backup frequency | Daily automated, 35-day retention |
| NFR-016 | Data | RPO (Recovery Point Objective) | 1 hour |
| NFR-017 | Data | RTO (Recovery Time Objective) | 4 hours |
| NFR-018 | Localization | Language support (MVP) | English (US) |
| NFR-019 | Compliance | GDPR right to erasure | 72-hour fulfillment |
| NFR-020 | Compliance | Data residency | EU data in eu-west-1 |

---

## 5. Business Rules (BUS)

| ID | Rule | Module |
|----|------|--------|
| BUS-001 | A job requisition must be approved by HR Manager before publishing | Job Management |
| BUS-002 | Offers above $150K salary require VP HR approval | Offer Management |
| BUS-003 | AI screening score below 40 auto-rejects unless recruiter overrides | AI Screening |
| BUS-004 | Minimum 2 panel evaluations required before offer stage | Evaluation |
| BUS-005 | Candidates inactive for 90 days are auto-archived | Candidate Lifecycle |
| BUS-006 | Maximum 3 interview reschedules per candidate per round | Scheduling |
| BUS-007 | Subscription seat limit cannot be exceeded without upgrade | Billing |
| BUS-008 | Audit logs cannot be modified or deleted by any user | Audit |
| BUS-009 | AI interview recordings retained for 12 months then auto-deleted | AI Interview |
| BUS-010 | Knockout rules must be defined before AI screening can run | AI Screening |
| BUS-011 | Panel scorecards must be submitted within 24 hours of interview | Evaluation |
| BUS-012 | Free trial converts to paid plan automatically on day 15 unless cancelled | Billing |
| BUS-013 | Duplicate candidates merged keeping highest AI score application | Resume |
| BUS-014 | GDPR deletion requests processed within 72 hours | Compliance |
| BUS-015 | Bias audit must run monthly with results accessible to Compliance | AI Screening |

---

## 6. Process Requirements (PR)

| ID | Requirement |
|----|-------------|
| PR-001 | System shall enforce sequential hiring stages: Applied → Screened → AI Interview → Panel Interview → Evaluation → Offer → Hired/Rejected |
| PR-002 | System shall support parallel panel interviews within the same stage |
| PR-003 | System shall allow stage rollback by HR Manager with audit justification |
| PR-004 | System shall auto-advance candidates meeting configurable score thresholds |
| PR-005 | System shall trigger escalation when requisition open > 45 days |
| PR-006 | System shall support requisition cloning for recurring role types |
| PR-007 | System shall track SLA compliance per hiring stage |
| PR-008 | System shall support bulk stage transition for multiple candidates |
| PR-009 | System shall prevent offer generation for candidates with incomplete evaluations |
| PR-010 | System shall trigger compliance review for AI scores with >20% demographic variance |

---

## 7. Reporting Requirements (RR)

| ID | Report | Audience | Frequency |
|----|--------|----------|-----------|
| RR-001 | Hiring Pipeline Funnel | HR Manager | Real-time |
| RR-002 | Time-to-Hire by Department | CHRO | Weekly |
| RR-003 | Cost-per-Hire Analysis | Finance | Monthly |
| RR-004 | Recruiter Performance Scorecard | HR Manager | Monthly |
| RR-005 | AI Screening Accuracy Report | Compliance | Monthly |
| RR-006 | Offer Acceptance Rate Trend | HR Manager | Monthly |
| RR-007 | Source of Hire Analysis | Recruiter Lead | Monthly |
| RR-008 | Diversity Hiring Metrics (EEOC) | Compliance | Quarterly |
| RR-009 | Interview Panel Utilization | HR Manager | Monthly |
| RR-010 | SaaS Revenue Dashboard (MRR/ARR) | Finance | Real-time |
| RR-011 | Candidate Experience NPS | HR Manager | Quarterly |
| RR-012 | Bias Audit Summary | Compliance | Monthly |
| RR-013 | Subscription Churn Report | Finance | Monthly |
| RR-014 | Open Requisition Aging Report | Recruiter | Weekly |
| RR-015 | AI Interview Completion Rate | Recruiter | Weekly |

---

## 8. Requirement Summary

| Category | Count |
|----------|-------|
| Business Requirements (BR) | 40 |
| Functional Requirements (FR) | 55 |
| Non-Functional Requirements (NFR) | 20 |
| Business Rules (BUS) | 15 |
| Process Requirements (PR) | 10 |
| Reporting Requirements (RR) | 15 |
| **Total** | **155** |

---

## 9. Approval

| Role | Name | Date | Signature |
|------|------|------|-----------|
| Business Owner | VP Talent Acquisition | ___/___/2026 | _________ |
| Business Analyst | Rohit | 06/08/2026 | _________ |
| Technical Lead | _________________ | ___/___/2026 | _________ |
| QA Lead | _________________ | ___/___/2026 | _________ |

---

*Document Classification: Internal — Requirements*
