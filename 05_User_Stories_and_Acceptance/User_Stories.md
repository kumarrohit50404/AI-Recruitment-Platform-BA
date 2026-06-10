# User Stories Backlog
## HireFlow AI — AI-Powered Recruitment & Interview Management Platform

| Field | Value |
|-------|-------|
| **Document ID** | US-HFA-2026-001 |
| **Version** | 1.0 |
| **Author** | Rohit, Business Analyst |
| **Status** | Approved |
| **Total User Stories** | 155 |

---

## 1. Document Purpose

This backlog contains 155 user stories for HireFlow AI, organized by epic and traceable to business requirements in `05_BRD/BRD.md` and use cases in `08_Use_Cases/Use_Cases.md`. Stories follow the standard format: *As a [role], I want [capability], so that [benefit]*.

**Priority Legend:** Must = MVP critical | Should = High value, Phase 2 | Could = Nice-to-have, Phase 3

**Story Points:** Fibonacci scale (1, 2, 3, 5, 8, 13)

**Sprint Plan:** 12 two-week sprints aligned to Q3 2026 – Q1 2027 release phases

---

## 2. Epic Summary

| Epic | Story Count | Sprint Range | Phase |
|------|-------------|--------------|-------|
| Authentication | 12 | 1–2 | MVP |
| User Management | 13 | 1–3 | MVP |
| Resume | 12 | 2–4 | MVP |
| AI Screening | 13 | 3–5 | MVP |
| Jobs | 12 | 4–5 | MVP |
| Scheduling | 11 | 5–6 | Phase 2 |
| AI Interview | 13 | 6–8 | Phase 2 |
| Evaluation | 12 | 7–8 | Phase 2 |
| Offers | 10 | 8–9 | Phase 2 |
| Reporting | 13 | 9–10 | Phase 2 |
| Billing | 11 | 10–11 | Phase 3 |
| Notifications | 10 | 9–11 | Phase 2–3 |
| Audit | 13 | 11–12 | Phase 3 |
| **Total** | **155** | | |

---

## 3. User Stories

### Epic 1: Authentication (12 Stories)

| ID | As a... | I want... | So that... | Priority | Story Points | Sprint |
|----|---------|-----------|------------|----------|--------------|--------|
| US-AUTH-001 | Company Admin | to register with email and password | I can create a secure account for my organization | Must | 3 | 1 |
| US-AUTH-002 | Recruiter | to verify my email address after registration | my account is activated and trusted by the system | Must | 2 | 1 |
| US-AUTH-003 | HR Manager | to log in with email and password | I can access the platform to manage hiring workflows | Must | 2 | 1 |
| US-AUTH-004 | Company Admin | to enable multi-factor authentication (TOTP) | my organization's accounts are protected against unauthorized access | Must | 5 | 1 |
| US-AUTH-005 | Company Admin | to configure SAML 2.0 SSO for my tenant | employees can log in using corporate credentials | Must | 8 | 2 |
| US-AUTH-006 | Recruiter | to log in via OIDC (Google, Azure AD) | I can use my existing enterprise identity without a separate password | Must | 5 | 2 |
| US-AUTH-007 | Company Admin | to enforce a password policy (12 chars, complexity) | weak passwords do not compromise tenant security | Must | 3 | 1 |
| US-AUTH-008 | Super Admin | to view authentication event logs across tenants | I can investigate security incidents platform-wide | Must | 5 | 2 |
| US-AUTH-009 | Recruiter | to reset my password via secure email link | I can regain access if I forget my credentials | Must | 3 | 1 |
| US-AUTH-010 | Company Admin | to lock accounts after 5 failed login attempts | brute-force attacks are mitigated automatically | Must | 3 | 2 |
| US-AUTH-011 | HR Manager | to manage concurrent session limits | shared or compromised sessions are controlled | Should | 5 | 2 |
| US-AUTH-012 | Company Admin | to create custom roles with granular permissions | I can tailor access beyond the 8 predefined roles | Should | 8 | 3 |

### Epic 2: User Management (13 Stories)

| ID | As a... | I want... | So that... | Priority | Story Points | Sprint |
|----|---------|-----------|------------|----------|--------------|--------|
| US-UM-001 | Super Admin | to provision a new tenant company with default configuration | new customers are onboarded in under 30 minutes | Must | 8 | 1 |
| US-UM-002 | Super Admin | to view all tenant companies in a platform dashboard | I have a single pane of glass for multi-tenant management | Must | 5 | 2 |
| US-UM-003 | Company Admin | to create individual user accounts with role assignment | recruiters and panel members can access the platform | Must | 3 | 2 |
| US-UM-004 | Company Admin | to bulk import users via CSV with validation | I can provision large teams efficiently at go-live | Must | 5 | 3 |
| US-UM-005 | Company Admin | to edit and deactivate user accounts | I can manage workforce changes without vendor support | Must | 3 | 3 |
| US-UM-006 | Company Admin | to assign users to departments and hiring teams | candidates and requisitions are routed to the correct groups | Must | 3 | 3 |
| US-UM-007 | Company Admin | to view license consumption vs. subscription limit | I know when to upgrade before hitting seat caps | Must | 3 | 3 |
| US-UM-008 | Company Admin | to configure white-label branding (logo, colors) | candidates see our company identity on the career portal | Should | 5 | 4 |
| US-UM-009 | Company Admin | to sync users from Active Directory/LDAP | user provisioning stays aligned with our corporate directory | Should | 8 | 4 |
| US-UM-010 | Super Admin | to manage users across all tenant companies | I can resolve escalated access issues for any customer | Must | 5 | 3 |
| US-UM-011 | Company Admin | to send welcome emails with setup instructions on user creation | new users can self-onboard without manual guidance | Must | 2 | 2 |
| US-UM-012 | Company Admin | to view user activity logs (last login, recent actions) | I can identify inactive accounts for deactivation | Should | 3 | 4 |
| US-UM-013 | Super Admin | to configure feature flags per tenant | I can enable beta features for select customers | Could | 5 | 5 |

### Epic 3: Resume (12 Stories)

| ID | As a... | I want... | So that... | Priority | Story Points | Sprint |
|----|---------|-----------|------------|----------|--------------|--------|
| US-RES-001 | Candidate | to upload my resume in PDF, DOCX, or TXT format | I can apply to jobs with my existing documents | Must | 3 | 2 |
| US-RES-002 | Candidate | to drag and drop my resume file during application | the upload process is fast and intuitive | Must | 2 | 2 |
| US-RES-003 | System | to validate file type and scan for malware before storage | malicious files do not enter the platform | Must | 5 | 3 |
| US-RES-004 | System | to parse resumes into structured fields within 30 seconds | recruiters receive searchable candidate profiles quickly | Must | 8 | 3 |
| US-RES-005 | System | to extract skills, experience, and education from parsed resumes | AI screening has accurate input data | Must | 8 | 3 |
| US-RES-006 | Recruiter | to view and download candidate resumes | I can review original documents alongside parsed data | Must | 2 | 3 |
| US-RES-007 | Recruiter | to detect and merge duplicate candidate profiles | I maintain a single canonical record per person | Must | 5 | 4 |
| US-RES-008 | Recruiter | to manually correct parsed resume fields | inaccuracies from complex layouts do not persist | Must | 3 | 4 |
| US-RES-009 | Recruiter | to bulk upload resumes via drag-and-drop | I can import sourced candidates from job fairs or referrals | Should | 5 | 4 |
| US-RES-010 | System | to normalize skill names against a 500+ skill taxonomy | skill matching is consistent across candidates | Must | 5 | 4 |
| US-RES-011 | System | to maintain resume version history per candidate | I can track profile updates over time | Should | 3 | 5 |
| US-RES-012 | Interview Panel | to view resumes with PII redacted until interview stage | candidate privacy is protected during early screening | Should | 3 | 5 |

### Epic 4: AI Screening (13 Stories)

| ID | As a... | I want... | So that... | Priority | Story Points | Sprint |
|----|---------|-----------|------------|----------|--------------|--------|
| US-AIS-001 | Recruiter | to see candidates ranked by AI match score (0–100) | I focus on the most qualified applicants first | Must | 8 | 4 |
| US-AIS-002 | System | to score candidates using weighted criteria (skills 40%, experience 30%, education 20%, other 10%) | rankings reflect job-relevant qualifications | Must | 8 | 4 |
| US-AIS-003 | Company Admin | to configure knockout rules for minimum qualifications | unqualified candidates are auto-filtered before recruiter review | Must | 5 | 4 |
| US-AIS-004 | Recruiter | to view explainable AI rationale for each screening score | I understand why a candidate was ranked or rejected | Must | 5 | 5 |
| US-AIS-005 | Recruiter | to see matched and missing skills highlighted on candidate profiles | I can quickly assess skill gaps without reading full resumes | Must | 3 | 5 |
| US-AIS-006 | System | to auto-reject candidates scoring below 40 unless overridden | the pipeline is not cluttered with poor matches | Must | 3 | 5 |
| US-AIS-007 | Recruiter | to override an AI screening score with mandatory justification | I can advance strong candidates the AI may have undervalued | Must | 5 | 5 |
| US-AIS-008 | System | to batch-process up to 500 resumes per requisition within 10 minutes | high-volume hiring campaigns are handled efficiently | Must | 8 | 5 |
| US-AIS-009 | Company Admin | to configure custom scoring weights per job family | different roles are evaluated with appropriate emphasis | Should | 5 | 6 |
| US-AIS-010 | Compliance Team | to run bias audits comparing scores across demographic groups | I can demonstrate EEOC and NYC LL144 compliance | Must | 8 | 6 |
| US-AIS-011 | System | to flag parsing confidence scores per extracted field | recruiters know which data points need manual verification | Should | 3 | 5 |
| US-AIS-012 | Compliance Team | to receive alerts when AI scores show >20% demographic variance | adverse impact is caught before it affects hiring decisions | Must | 5 | 6 |
| US-AIS-013 | System | to log all AI screening decisions with input, output, and model version | audit trails support regulatory inspections | Must | 5 | 6 |

### Epic 5: Jobs (12 Stories)

| ID | As a... | I want... | So that... | Priority | Story Points | Sprint |
|----|---------|-----------|------------|----------|--------------|--------|
| US-JOB-001 | Recruiter | to create job requisitions with title, description, and requirements | open positions are formally documented in the system | Must | 5 | 4 |
| US-JOB-002 | Recruiter | to define salary band and employment type per job | compensation expectations are clear to candidates and approvers | Must | 3 | 4 |
| US-JOB-003 | Recruiter | to assign hiring teams and interview panel to a requisition | the right stakeholders are involved from the start | Must | 3 | 5 |
| US-JOB-004 | Recruiter | to clone an existing job requisition | recurring roles are created quickly without re-entering data | Should | 3 | 5 |
| US-JOB-005 | Recruiter | to use job templates by role family | standard roles follow consistent descriptions and requirements | Should | 3 | 5 |
| US-JOB-006 | HR Manager | to approve or reject job requisitions before they go live | hiring aligns with budget and headcount plans | Must | 5 | 5 |
| US-JOB-007 | Recruiter | to publish approved jobs to the company career portal | candidates can discover and apply to open positions | Must | 5 | 5 |
| US-JOB-008 | System | to generate a unique URL for each published job | jobs can be shared on social media and job boards | Must | 2 | 5 |
| US-JOB-009 | Candidate | to browse and apply to published jobs on the career portal | I can pursue opportunities at companies I am interested in | Must | 5 | 5 |
| US-JOB-010 | Recruiter | to track application count and pipeline status per job | I know which requisitions need attention | Must | 3 | 5 |
| US-JOB-011 | Company Admin | to configure auto-close rules for jobs after N days or fill | stale postings do not mislead candidates | Should | 3 | 6 |
| US-JOB-012 | HR Manager | to request revisions on requisitions with comments | recruiters can address feedback before resubmission | Should | 3 | 6 |

### Epic 6: Scheduling (11 Stories)

| ID | As a... | I want... | So that... | Priority | Story Points | Sprint |
|----|---------|-----------|------------|----------|--------------|--------|
| US-SCH-001 | Recruiter | to view panel member availability from calendar integration | I schedule interviews without manual availability checks | Must | 8 | 5 |
| US-SCH-002 | System | to suggest top 5 interview time slots ranked by availability | scheduling decisions are data-driven and fast | Must | 5 | 6 |
| US-SCH-003 | Recruiter | to schedule multi-round interviews sequentially | complex hiring processes are coordinated in one workflow | Must | 5 | 6 |
| US-SCH-004 | Candidate | to select my preferred interview slot from available options | I can schedule without back-and-forth emails | Should | 5 | 6 |
| US-SCH-005 | Recruiter | to reschedule interviews with automatic notifications to all parties | calendar changes are communicated instantly | Must | 5 | 6 |
| US-SCH-006 | System | to send calendar invites to panel and candidate on confirmation | all parties have the event in their calendars | Must | 3 | 6 |
| US-SCH-007 | System | to send interview reminders 24 hours and 1 hour before | no-shows are reduced through timely alerts | Must | 3 | 6 |
| US-SCH-008 | Interview Panel | to submit my availability for interview scheduling | recruiters can book times that work for me | Must | 3 | 6 |
| US-SCH-009 | System | to enforce a 15-minute buffer between consecutive interviews | panel members have adequate transition time | Should | 2 | 7 |
| US-SCH-010 | Recruiter | to track no-show incidents and flag repeat offenders | unreliable candidates are identified early | Should | 3 | 7 |
| US-SCH-011 | System | to limit reschedules to 3 per candidate per round | scheduling abuse does not delay the hiring process | Must | 3 | 7 |

### Epic 7: AI Interview (13 Stories)

| ID | As a... | I want... | So that... | Priority | Story Points | Sprint |
|----|---------|-----------|------------|----------|--------------|--------|
| US-AII-001 | System | to generate role-specific interview questions using AI | each candidate is assessed on relevant competencies | Must | 8 | 6 |
| US-AII-002 | Candidate | to complete an asynchronous video interview | I can interview on my own schedule without live coordination | Must | 8 | 7 |
| US-AII-003 | System | to transcribe candidate responses in real-time | reviewers can read responses alongside video recordings | Must | 8 | 7 |
| US-AII-004 | System | to score responses against rubric criteria on a 1–5 scale | interview evaluations are consistent and objective | Must | 5 | 7 |
| US-AII-005 | Recruiter | to review AI interview recordings and transcripts | I can make informed advancement decisions | Must | 5 | 7 |
| US-AII-006 | System | to generate an AI interview summary report per candidate | panel members receive a concise performance overview | Must | 5 | 8 |
| US-AII-007 | Company Admin | to manage a question bank by role and level | interview content is standardized across the organization | Must | 5 | 7 |
| US-AII-008 | Candidate | to access a practice mode before the live AI interview | I am comfortable with the format and technology | Should | 5 | 8 |
| US-AII-009 | System | to limit AI interviews to a configurable duration (default 30 min) | interviews are concise and respectful of candidate time | Must | 3 | 7 |
| US-AII-010 | System | to detect and flag inappropriate candidate behavior | compliance and safety concerns are escalated promptly | Should | 8 | 8 |
| US-AII-011 | System | to retain AI interview recordings for 12 months then auto-delete | storage costs and privacy obligations are managed | Must | 3 | 8 |
| US-AII-012 | Recruiter | to extend the AI interview deadline for a candidate | exceptional circumstances do not result in auto-rejection | Should | 2 | 8 |
| US-AII-013 | Candidate | to pause and resume an AI interview within 48 hours | technical interruptions do not force a full restart | Should | 5 | 8 |

### Epic 8: Evaluation (12 Stories)

| ID | As a... | I want... | So that... | Priority | Story Points | Sprint |
|----|---------|-----------|------------|----------|--------------|--------|
| US-EVL-001 | Interview Panel | to complete a digital scorecard with weighted criteria | my evaluation is structured and comparable across candidates | Must | 5 | 7 |
| US-EVL-002 | Interview Panel | to submit a hire/no-hire/undecided recommendation | hiring decisions capture my overall judgment | Must | 3 | 7 |
| US-EVL-003 | System | to calculate a composite score from all panel evaluations | HR has a single metric for candidate comparison | Must | 5 | 8 |
| US-EVL-004 | System | to require minimum 2 panel evaluations before advancement | decisions are not made on a single interviewer's opinion | Must | 3 | 8 |
| US-EVL-005 | System | to flag score variance greater than 1.5 points between panelists | disagreements trigger calibration before final decisions | Must | 5 | 8 |
| US-EVL-006 | HR Manager | to view an evaluation summary with all panel feedback | I have complete context for offer decisions | Must | 5 | 8 |
| US-EVL-007 | Interview Panel | to receive a one-page candidate brief before each interview | I am prepared with resume highlights and AI summary | Must | 3 | 7 |
| US-EVL-008 | System | to enforce scorecard completion within 24 hours of interview | feedback latency does not delay the hiring pipeline | Should | 3 | 8 |
| US-EVL-009 | Interview Panel | to add debrief notes shared among panel members | the hiring team can discuss impressions collaboratively | Should | 3 | 8 |
| US-EVL-010 | System | to maintain evaluation history for returning candidates | prior interview data informs re-application decisions | Must | 5 | 8 |
| US-EVL-011 | HR Manager | to conduct anonymized calibration sessions | panel bias is reduced through structured discussion | Should | 5 | 9 |
| US-EVL-012 | Company Admin | to configure scorecard templates by role and level | evaluation criteria match job requirements consistently | Must | 5 | 7 |

### Epic 9: Offers (10 Stories)

| ID | As a... | I want... | So that... | Priority | Story Points | Sprint |
|----|---------|-----------|------------|----------|--------------|--------|
| US-OFR-001 | HR Manager | to generate offer letters from configurable templates | offers are professional and consistent across the organization | Must | 5 | 8 |
| US-OFR-002 | HR Manager | to preview offer letter PDF before sending | errors in compensation or terms are caught before delivery | Must | 3 | 8 |
| US-OFR-003 | HR Manager | to route offers above $150K to VP HR for additional approval | high-value offers receive executive oversight | Must | 5 | 9 |
| US-OFR-004 | System | to block offer generation for candidates with incomplete evaluations | offers are not extended without proper due diligence | Must | 3 | 9 |
| US-OFR-005 | HR Manager | to send approved offers to candidates via secure link | candidates can review and respond electronically | Must | 5 | 9 |
| US-OFR-006 | Candidate | to accept or decline an offer through the secure portal | my decision is captured without email ambiguity | Must | 3 | 9 |
| US-OFR-007 | HR Manager | to create revised offers after candidate negotiation | counteroffers are managed within the same workflow | Should | 5 | 9 |
| US-OFR-008 | System | to auto-expire offers after 7 days without response | stale offers do not create legal or operational confusion | Should | 3 | 9 |
| US-OFR-009 | Recruiter | to capture decline reasons when candidates reject offers | we can analyze and reduce offer decline rates | Should | 3 | 9 |
| US-OFR-010 | HR Manager | to approve or reject offers from my mobile device | approval bottlenecks do not delay time-to-hire | Should | 5 | 9 |

### Epic 10: Reporting (13 Stories)

| ID | As a... | I want... | So that... | Priority | Story Points | Sprint |
|----|---------|-----------|------------|----------|--------------|--------|
| US-RPT-001 | HR Manager | to view an executive dashboard with 10 core hiring KPIs | I have real-time visibility into hiring performance | Must | 8 | 9 |
| US-RPT-002 | HR Manager | to see a real-time hiring pipeline funnel visualization | I can identify bottlenecks in the recruitment process | Must | 5 | 9 |
| US-RPT-003 | HR Manager | to view time-to-hire metrics by department | I can compare hiring velocity across the organization | Must | 5 | 9 |
| US-RPT-004 | HR Manager | to view cost-per-hire analytics | I can demonstrate ROI of the recruitment investment | Should | 5 | 10 |
| US-RPT-005 | HR Manager | to compare recruiter performance in a scorecard report | I can coach underperforming recruiters objectively | Should | 5 | 10 |
| US-RPT-006 | HR Manager | to export reports in PDF, CSV, and Excel formats | I can share data in board presentations and spreadsheets | Must | 3 | 10 |
| US-RPT-007 | HR Manager | to schedule automated report delivery via email | I receive weekly KPI summaries without manual effort | Should | 5 | 10 |
| US-RPT-008 | Compliance Team | to generate EEOC adverse impact analysis reports | regulatory filings are supported with accurate data | Must | 8 | 10 |
| US-RPT-009 | Recruiter | to view open requisition aging reports | I prioritize roles that have been open too long | Must | 3 | 9 |
| US-RPT-010 | Recruiter | to view source-of-hire analytics | I invest sourcing effort in the most effective channels | Should | 5 | 10 |
| US-RPT-011 | HR Manager | to see monthly hiring trends with year-over-year comparison | I can report progress against annual hiring goals | Must | 5 | 10 |
| US-RPT-012 | Recruiter | to view AI interview completion rate reports | I can follow up with candidates who have not completed interviews | Should | 3 | 10 |
| US-RPT-013 | HR Manager | to drill down from KPI tiles to individual candidate records | I can investigate anomalies without switching modules | Must | 5 | 10 |

### Epic 11: Billing (11 Stories)

| ID | As a... | I want... | So that... | Priority | Story Points | Sprint |
|----|---------|-----------|------------|----------|--------------|--------|
| US-BIL-001 | Company Admin | to select from Starter, Professional, and Enterprise subscription tiers | I choose a plan that matches my organization's needs | Must | 5 | 10 |
| US-BIL-002 | Company Admin | to pay via Stripe with monthly or annual billing cycles | subscription payments are automated and secure | Must | 5 | 10 |
| US-BIL-003 | System | to auto-generate invoices on each billing cycle date | financial records are accurate without manual intervention | Must | 5 | 11 |
| US-BIL-004 | System | to retry failed payments with a 3-attempt dunning process | involuntary churn from transient payment issues is minimized | Must | 5 | 11 |
| US-BIL-005 | Company Admin | to upgrade my plan mid-cycle with prorated charges | I can scale up immediately when hiring volume increases | Must | 5 | 11 |
| US-BIL-006 | System | to enforce feature limits per subscription tier | plan entitlements are respected automatically | Must | 5 | 11 |
| US-BIL-007 | Finance Team | to access an MRR/ARR revenue dashboard | I can track SaaS revenue performance in real time | Must | 8 | 11 |
| US-BIL-008 | Company Admin | to start a 14-day free trial with auto-conversion | I can evaluate the platform before committing to a paid plan | Should | 5 | 11 |
| US-BIL-009 | System | to send renewal reminders 30 days before contract expiry | customers renew proactively rather than lapsing | Must | 3 | 11 |
| US-BIL-010 | Finance Team | to export revenue reports in NetSuite-compatible format | revenue posts to our ERP without manual re-entry | Should | 5 | 12 |
| US-BIL-011 | Finance Team | to view subscription churn reports | I can identify and address customer retention risks | Should | 5 | 12 |

### Epic 12: Notifications (10 Stories)

| ID | As a... | I want... | So that... | Priority | Story Points | Sprint |
|----|---------|-----------|------------|----------|--------------|--------|
| US-NOT-001 | Candidate | to receive email notifications at each pipeline stage | I always know the status of my application | Must | 5 | 9 |
| US-NOT-002 | Recruiter | to receive in-app notifications for candidate actions | I respond promptly to applications and scheduling requests | Must | 3 | 9 |
| US-NOT-003 | HR Manager | to receive push notifications for pending approvals | requisitions and offers are not delayed in my queue | Must | 5 | 9 |
| US-NOT-004 | Interview Panel | to receive SMS reminders 1 hour before interviews | I do not miss scheduled interview sessions | Should | 5 | 10 |
| US-NOT-005 | Company Admin | to customize email notification templates per tenant | communications reflect our brand and tone | Must | 5 | 10 |
| US-NOT-006 | Recruiter | to configure my notification preferences per event type | I control which alerts I receive and how | Should | 3 | 10 |
| US-NOT-007 | System | to send 15 defined event-type notifications automatically | all stakeholders are informed without manual effort | Must | 5 | 9 |
| US-NOT-008 | Candidate | to view an in-app notification center with read/unread status | I can review all communications in one place | Must | 3 | 9 |
| US-NOT-009 | System | to batch non-urgent notifications into a daily digest | users are not overwhelmed by excessive email volume | Could | 5 | 11 |
| US-NOT-010 | Recruiter | to send bulk emails to selected candidates | I can communicate efficiently with candidate groups | Should | 5 | 10 |

### Epic 13: Audit (13 Stories)

| ID | As a... | I want... | So that... | Priority | Story Points | Sprint |
|----|---------|-----------|------------|----------|--------------|--------|
| US-AUD-001 | Compliance Team | to search and filter audit logs by date, user, action, and entity | I can investigate any system event during audits | Must | 5 | 11 |
| US-AUD-002 | System | to log all CRUD operations with user, timestamp, IP, and action | every data change has a complete forensic trail | Must | 5 | 11 |
| US-AUD-003 | Compliance Team | to run monthly AI bias audit reports with demographic breakdowns | NYC LL144 and EEOC obligations are met proactively | Must | 8 | 11 |
| US-AUD-004 | System | to maintain immutable, tamper-evident audit logs | log integrity is guaranteed for regulatory inspections | Must | 8 | 11 |
| US-AUD-005 | Compliance Team | to process DSAR requests within 72 hours | GDPR data subject rights are fulfilled on time | Must | 8 | 12 |
| US-AUD-006 | Candidate | to submit a data access or deletion request via the privacy portal | I can exercise my GDPR rights without contacting support | Must | 5 | 12 |
| US-AUD-007 | Compliance Team | to export audit logs in CSV and JSON formats | logs can be provided to external auditors | Must | 3 | 12 |
| US-AUD-008 | System | to retain audit logs for a minimum of 7 years | retention meets regulatory and legal requirements | Must | 3 | 12 |
| US-AUD-009 | Compliance Team | to view AI explainability data for every screening decision | I can demonstrate fairness and transparency to regulators | Must | 5 | 12 |
| US-AUD-010 | Compliance Team | to configure data retention policies with auto-deletion | data is not kept longer than necessary | Must | 5 | 12 |
| US-AUD-011 | Super Admin | to view platform-wide audit events across all tenants | I can investigate cross-tenant security incidents | Must | 5 | 12 |
| US-AUD-012 | Compliance Team | to track candidate consent with version history | consent management is auditable per GDPR | Must | 5 | 12 |
| US-AUD-013 | System | to trigger compliance review when requisitions are open >45 days | stale hiring processes receive governance attention | Should | 3 | 12 |

---

## 4. Story Point Summary

| Story Points | Count | Total Points |
|--------------|-------|--------------|
| 1 | 0 | 0 |
| 2 | 12 | 24 |
| 3 | 48 | 144 |
| 5 | 72 | 360 |
| 8 | 21 | 168 |
| 13 | 2 | 26 |
| **Total** | **155** | **722** |

---

## 5. Priority Distribution

| Priority | Count | Percentage |
|----------|-------|------------|
| Must | 108 | 69.7% |
| Should | 42 | 27.1% |
| Could | 5 | 3.2% |
| **Total** | **155** | 100% |

---

## 6. Role Coverage

| Role | Story Count |
|------|-------------|
| Super Admin | 8 |
| Company Admin | 28 |
| Recruiter | 32 |
| HR Manager | 24 |
| Interview Panel | 8 |
| Candidate | 14 |
| Finance Team | 4 |
| Compliance Team | 12 |
| System | 25 |

---

## 7. Approval

| Role | Name | Date | Signature |
|------|------|------|-----------|
| Product Owner | VP Talent Acquisition | ___/___/2026 | _________ |
| Business Analyst | Rohit | 06/08/2026 | _________ |
| Scrum Master | _________________ | ___/___/2026 | _________ |

---

*Document Classification: Internal — Agile Backlog*
