# Conceptual Data Model
## HireFlow AI — Recruitment & Interview Management Platform

| Field | Value |
|-------|-------|
| **Document ID** | DM-HFA-2026-001 |
| **Version** | 1.0 |
| **Author** | Rohit, Business Analyst |
| **Status** | Approved |
| **Related Documents** | BRD-HFA-2026-001, ERD-HFA-2026-001, DB-SCHEMA-HFA-2026-001 |

---

## 1. Purpose

This document defines the **conceptual data model** for HireFlow AI—a multi-tenant SaaS recruitment platform. It describes business entities, attributes, relationships, and data governance rules at a logical level, independent of physical implementation. This model supports BR-001 (multi-tenancy), BR-004 (end-to-end hiring workflow), BR-008 (subscription billing), and BR-010 (immutable audit logs).

**Audience:** Business Analysts, Product Owners, Solution Architects, QA, Compliance, and interview stakeholders reviewing data design decisions.

---

## 2. Modeling Approach

| Aspect | Decision | Rationale |
|--------|----------|-----------|
| **Paradigm** | Relational (3NF) | Structured hiring data with strong referential integrity |
| **Tenancy** | Company-scoped isolation | BR-001: complete data isolation per tenant |
| **Naming** | Singular entity names | Standard ER convention (User, Job, Application) |
| **Identifiers** | Surrogate UUID keys | Globally unique, safe for distributed systems |
| **Soft Delete** | `is_active` / `status` flags | Preserve audit trail and compliance history |
| **Temporal Data** | `created_at`, `updated_at` on all entities | Traceability for SLA and compliance reporting |

---

## 3. Entity Overview

| # | Entity | Description | Primary Stakeholders |
|---|--------|-------------|------------------------|
| 1 | **Company** | Tenant organization using HireFlow AI | Super Admin, Company Admin |
| 2 | **Role** | RBAC role definition with permissions | Company Admin, Compliance |
| 3 | **User** | Internal platform user (recruiter, HR, panel, admin) | All internal roles |
| 4 | **Candidate** | External job seeker profile | Candidate, Recruiter |
| 5 | **Resume** | Uploaded/parsed resume document | Recruiter, AI Engine |
| 6 | **Job** | Job requisition / open position | Recruiter, HR Manager |
| 7 | **Application** | Candidate application to a specific job | Recruiter, Candidate |
| 8 | **Interview** | Scheduled or completed interview session | Panel, Recruiter |
| 9 | **Question** | Interview question from bank or AI-generated | Panel, Company Admin |
| 10 | **Response** | Candidate answer to an interview question | AI Engine, Panel |
| 11 | **Score** | AI screening or evaluation score record | Recruiter, Compliance |
| 12 | **Offer** | Employment offer extended to candidate | HR Manager, Finance |
| 13 | **Subscription** | SaaS subscription plan for a company | Finance, Company Admin |
| 14 | **Payment** | Billing transaction against subscription | Finance |
| 15 | **AuditLog** | Immutable record of system actions | Compliance |

**Junction Entity:** `UserRole` — assigns one or more roles to a user (M:N between User and Role).

---

## 4. Entity Definitions

### 4.1 Company

Represents a tenant organization. All operational data (users, jobs, candidates, applications) is scoped to a company.

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| Company ID | UUID | Yes | Unique tenant identifier |
| Company Name | Text | Yes | Legal or trade name |
| Domain | Text | Yes | Primary email domain (e.g., `acmecorp.com`) |
| Industry | Text | No | Industry classification (NAICS code or label) |
| Company Size | Enum | No | `STARTUP`, `SMB`, `MID_MARKET`, `ENTERPRISE` |
| Address | Text | No | Headquarters address |
| Country Code | Text | Yes | ISO 3166-1 alpha-2 (data residency) |
| Timezone | Text | Yes | Default IANA timezone |
| Logo URL | Text | No | White-label branding (BR-039) |
| Status | Enum | Yes | `ACTIVE`, `SUSPENDED`, `TRIAL`, `CHURNED` |
| Created At | Timestamp | Yes | Tenant provisioning date |
| Updated At | Timestamp | Yes | Last modification timestamp |

**Business Rules:**
- BUS-007: Seat limits enforced via linked Subscription
- BR-006: EU companies require `country_code = 'EU'` region routing

---

### 4.2 Role

Defines RBAC roles with permission sets. Eight predefined roles per FR-AUTH-007.

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| Role ID | UUID | Yes | Unique role identifier |
| Role Name | Text | Yes | e.g., `RECRUITER`, `HR_MANAGER`, `PANEL` |
| Role Code | Text | Yes | Machine-readable code |
| Description | Text | No | Human-readable role purpose |
| Permissions | JSON | Yes | Granular permission flags |
| Is System Role | Boolean | Yes | `true` for predefined roles |
| Created At | Timestamp | Yes | Role creation date |

**Predefined Roles:** Super Admin, Company Admin, Recruiter, HR Manager, Interview Panel, Candidate (portal), Finance, Compliance.

---

### 4.3 User

Internal platform user belonging to a company (except Super Admin).

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| User ID | UUID | Yes | Unique user identifier |
| Company ID | UUID | Yes* | FK to Company (*nullable for Super Admin) |
| Email | Text | Yes | Login email (unique per company) |
| Password Hash | Text | Yes | Bcrypt hashed password |
| First Name | Text | Yes | Given name |
| Last Name | Text | Yes | Family name |
| Phone | Text | No | Contact number |
| Department | Text | No | Organizational unit |
| Job Title | Text | No | e.g., "Senior Recruiter" |
| Profile Photo URL | Text | No | Avatar image |
| Timezone | Text | No | User-specific timezone override |
| MFA Enabled | Boolean | Yes | Multi-factor authentication flag |
| Is Active | Boolean | Yes | Account active status |
| Failed Login Count | Integer | Yes | For account lockout (FR-AUTH-009) |
| Last Login At | Timestamp | No | Most recent successful login |
| Created At | Timestamp | Yes | Account creation date |
| Updated At | Timestamp | Yes | Last profile update |

**Relationships:**
- User **belongs to** one Company (optional for Super Admin)
- User **has many** Roles via UserRole (M:N)

---

### 4.4 Candidate

External job seeker. Profiles are tenant-scoped after first application (BUS-013: duplicate merge).

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| Candidate ID | UUID | Yes | Unique candidate identifier |
| Company ID | UUID | Yes | Tenant scope |
| Email | Text | Yes | Primary contact email |
| First Name | Text | Yes | Given name |
| Last Name | Text | Yes | Family name |
| Phone | Text | No | Contact number |
| LinkedIn URL | Text | No | Professional profile link |
| Source | Enum | No | `CAREER_PORTAL`, `REFERRAL`, `LINKEDIN`, `INDEED`, `AGENCY`, `DIRECT` |
| Total Experience Years | Decimal | No | Calculated from resume parsing |
| Current Employer | Text | No | Most recent employer |
| Current Title | Text | No | Most recent job title |
| Location City | Text | No | City of residence |
| Location Country | Text | No | Country of residence |
| Status | Enum | Yes | `ACTIVE`, `ARCHIVED`, `BLACKLISTED` |
| GDPR Consent | Boolean | Yes | Data processing consent |
| Last Activity At | Timestamp | No | For 90-day auto-archive (BUS-005) |
| Created At | Timestamp | Yes | Profile creation date |
| Updated At | Timestamp | Yes | Last update |

---

### 4.5 Resume

Stores resume files and parsed structured data for a candidate.

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| Resume ID | UUID | Yes | Unique resume identifier |
| Candidate ID | UUID | Yes | FK to Candidate |
| File Name | Text | Yes | Original upload filename |
| File Type | Enum | Yes | `PDF`, `DOCX`, `TXT` |
| File Size Bytes | Integer | Yes | Max 10MB (FR-RM-001) |
| Storage URL | Text | Yes | Encrypted S3 path (FR-RM-003) |
| Version Number | Integer | Yes | Resume version (FR-RM-004) |
| Is Current | Boolean | Yes | Active version flag |
| Parsed Data | JSON | No | Structured extraction output |
| Skills Extracted | Text[] | No | Normalized skill array |
| Education Summary | JSON | No | Degrees, institutions, dates |
| Experience Summary | JSON | No | Work history array |
| Parsing Confidence | Decimal | No | 0.00–1.00 confidence score |
| Parsed At | Timestamp | No | Last parse completion time |
| Created At | Timestamp | Yes | Upload timestamp |

**Business Rules:**
- FR-RP-007: Re-parse on new version upload
- Only one resume per candidate marked `is_current = true`

---

### 4.6 Job

Job requisition representing an open position within a company.

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| Job ID | UUID | Yes | Unique job identifier |
| Company ID | UUID | Yes | FK to Company |
| Created By User ID | UUID | Yes | Recruiter who created requisition |
| Approved By User ID | UUID | No | HR Manager approver (BUS-001) |
| Title | Text | Yes | Job title |
| Description | Text | Yes | Full job description |
| Department | Text | Yes | Hiring department |
| Location | Text | No | Work location |
| Employment Type | Enum | Yes | `FULL_TIME`, `PART_TIME`, `CONTRACT`, `INTERN` |
| Remote Policy | Enum | No | `ONSITE`, `HYBRID`, `REMOTE` |
| Salary Min | Decimal | No | Salary band minimum |
| Salary Max | Decimal | No | Salary band maximum |
| Currency | Text | No | ISO 4217 currency code |
| Required Skills | Text[] | No | Must-have skills |
| Preferred Skills | Text[] | No | Nice-to-have skills |
| Min Experience Years | Decimal | No | Knockout threshold |
| Required Education | Text | No | Minimum education level |
| Status | Enum | Yes | `DRAFT`, `PENDING_APPROVAL`, `OPEN`, `ON_HOLD`, `CLOSED`, `FILLED` |
| Open Positions | Integer | Yes | Headcount to fill |
| Filled Positions | Integer | Yes | Positions already filled |
| Career Portal URL | Text | No | Public posting URL (FR-JM-004) |
| Published At | Timestamp | No | Go-live date |
| Closed At | Timestamp | No | Closure date |
| Created At | Timestamp | Yes | Requisition creation date |
| Updated At | Timestamp | Yes | Last modification |

**Business Rules:**
- BUS-001: Status must be `OPEN` only after HR approval
- PR-005: Escalation when open > 45 days

---

### 4.7 Application

Links a candidate to a job requisition and tracks pipeline stage.

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| Application ID | UUID | Yes | Unique application identifier |
| Job ID | UUID | Yes | FK to Job |
| Candidate ID | UUID | Yes | FK to Candidate |
| Resume ID | UUID | Yes | FK to Resume used for application |
| Assigned Recruiter ID | UUID | No | FK to User (recruiter) |
| Stage | Enum | Yes | Pipeline stage (see Section 5) |
| Stage Changed At | Timestamp | Yes | Last stage transition |
| AI Match Score | Decimal | No | 0–100 screening score (FR-AIS-001) |
| AI Rationale | Text | No | Explainable AI output (FR-AIS-004) |
| Knockout Passed | Boolean | Yes | Qualification gate result |
| Recruiter Override | Boolean | No | Override of AI rejection (FR-AIS-008) |
| Override Justification | Text | No | Required if override = true |
| Source | Enum | No | Application source channel |
| Rejection Reason | Text | No | If rejected |
| Applied At | Timestamp | Yes | Application submission date |
| Created At | Timestamp | Yes | Record creation |
| Updated At | Timestamp | Yes | Last update |

**Unique Constraint:** One active application per (Candidate, Job) pair.

**Business Rules:**
- BUS-003: AI score < 40 auto-rejects unless override
- PR-001: Sequential stage progression enforced

---

### 4.8 Interview

Represents a scheduled or completed interview session for an application.

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| Interview ID | UUID | Yes | Unique interview identifier |
| Application ID | UUID | Yes | FK to Application |
| Interview Type | Enum | Yes | `AI_ASYNC`, `AI_LIVE`, `PANEL`, `PHONE`, `TECHNICAL` |
| Round Number | Integer | Yes | Multi-round sequence (FR-IS-007) |
| Scheduled At | Timestamp | No | Planned start time |
| Duration Minutes | Integer | No | Scheduled duration |
| Actual Start At | Timestamp | No | Actual start |
| Actual End At | Timestamp | No | Actual end |
| Status | Enum | Yes | `SCHEDULED`, `IN_PROGRESS`, `COMPLETED`, `CANCELLED`, `NO_SHOW` |
| Location / Meeting URL | Text | No | Physical room or video link |
| Recording URL | Text | No | AI interview recording (FR-AII-002) |
| Reschedule Count | Integer | Yes | Max 3 per round (BUS-006) |
| AI Summary | Text | No | AI-generated interview summary |
| Created By User ID | UUID | No | Scheduler |
| Created At | Timestamp | Yes | Creation date |
| Updated At | Timestamp | Yes | Last update |

**Relationships:**
- Interview **has many** panelists via InterviewPanelist (User FK)
- Interview **has many** Responses

---

### 4.9 Question

Interview question from company question bank or AI-generated set.

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| Question ID | UUID | Yes | Unique question identifier |
| Company ID | UUID | Yes | FK to Company (tenant question bank) |
| Job ID | UUID | No | FK to Job (job-specific questions) |
| Created By User ID | UUID | No | Author |
| Question Text | Text | Yes | Full question content |
| Question Type | Enum | Yes | `BEHAVIORAL`, `TECHNICAL`, `SITUATIONAL`, `CULTURE_FIT`, `AI_GENERATED` |
| Difficulty Level | Enum | No | `JUNIOR`, `MID`, `SENIOR`, `EXECUTIVE` |
| Skill Tags | Text[] | No | Associated skills |
| Rubric Criteria | JSON | No | Scoring rubric definition |
| Expected Duration Sec | Integer | No | Suggested answer time |
| Is Active | Boolean | Yes | Available in question bank |
| Created At | Timestamp | Yes | Creation date |
| Updated At | Timestamp | Yes | Last update |

---

### 4.10 Response

Candidate's answer to a specific question during an interview.

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| Response ID | UUID | Yes | Unique response identifier |
| Interview ID | UUID | Yes | FK to Interview |
| Question ID | UUID | Yes | FK to Question |
| Response Text | Text | No | Transcribed or typed answer |
| Response Audio URL | Text | No | Audio recording path |
| Response Video URL | Text | No | Video recording path |
| Transcript Confidence | Decimal | No | Speech-to-text confidence |
| AI Response Score | Decimal | No | 1–5 rubric score (FR-AII-004) |
| AI Feedback | Text | No | AI evaluation notes |
| Duration Seconds | Integer | No | Answer duration |
| Submitted At | Timestamp | Yes | Response timestamp |
| Created At | Timestamp | Yes | Record creation |

---

### 4.11 Score

Consolidated scoring record for AI screening or panel evaluation.

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| Score ID | UUID | Yes | Unique score identifier |
| Application ID | UUID | Yes | FK to Application |
| Interview ID | UUID | No | FK to Interview (null for screening scores) |
| Scored By User ID | UUID | No | Panel evaluator (null for AI) |
| Score Type | Enum | Yes | `AI_SCREENING`, `AI_INTERVIEW`, `PANEL_EVALUATION`, `COMPOSITE` |
| Overall Score | Decimal | Yes | Weighted composite (0–100 or 1–5 scaled) |
| Skills Score | Decimal | No | Skills dimension (40% weight) |
| Experience Score | Decimal | No | Experience dimension (30% weight) |
| Education Score | Decimal | No | Education dimension (20% weight) |
| Other Score | Decimal | No | Other dimension (10% weight) |
| Recommendation | Enum | No | `STRONG_HIRE`, `HIRE`, `NO_HIRE`, `UNDECIDED` |
| Comments | Text | No | Evaluator feedback |
| Model Version | Text | No | AI model version (FR-AUD-005) |
| Is Final | Boolean | Yes | Finalized score flag |
| Scored At | Timestamp | Yes | Evaluation timestamp |
| Created At | Timestamp | Yes | Record creation |

**Business Rules:**
- BUS-004: Minimum 2 panel evaluations before offer
- FR-CE-004: Flag variance > 1.5 between panelists

---

### 4.12 Offer

Employment offer extended to a candidate for a job.

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| Offer ID | UUID | Yes | Unique offer identifier |
| Application ID | UUID | Yes | FK to Application |
| Created By User ID | UUID | Yes | HR user who generated offer |
| Approved By User ID | UUID | No | VP HR for offers > $150K (BUS-002) |
| Job Title | Text | Yes | Offered title |
| Base Salary | Decimal | Yes | Annual base compensation |
| Bonus Amount | Decimal | No | Signing or annual bonus |
| Equity Units | Decimal | No | Stock/equity grant |
| Currency | Text | Yes | ISO 4217 |
| Start Date | Date | Yes | Proposed start date |
| Expiry Date | Date | Yes | Offer acceptance deadline |
| Offer Letter URL | Text | No | Generated PDF path |
| Status | Enum | Yes | `DRAFT`, `PENDING_APPROVAL`, `SENT`, `ACCEPTED`, `DECLINED`, `EXPIRED`, `WITHDRAWN` |
| Decline Reason | Text | No | Candidate decline reason |
| Sent At | Timestamp | No | Offer delivery date |
| Responded At | Timestamp | No | Candidate response date |
| Created At | Timestamp | Yes | Offer creation |
| Updated At | Timestamp | Yes | Last update |

---

### 4.13 Subscription

SaaS subscription plan assigned to a company.

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| Subscription ID | UUID | Yes | Unique subscription identifier |
| Company ID | UUID | Yes | FK to Company |
| Plan Tier | Enum | Yes | `STARTER`, `PROFESSIONAL`, `ENTERPRISE` |
| Billing Cycle | Enum | Yes | `MONTHLY`, `ANNUAL` |
| Seat Limit | Integer | Yes | Licensed user seats (BUS-007) |
| Seats Used | Integer | Yes | Current active users |
| Price Per Seat | Decimal | Yes | Unit price |
| Total Amount | Decimal | Yes | Recurring charge |
| Currency | Text | Yes | ISO 4217 |
| Status | Enum | Yes | `TRIAL`, `ACTIVE`, `PAST_DUE`, `CANCELLED`, `EXPIRED` |
| Trial Ends At | Timestamp | No | 14-day trial end (BUS-012) |
| Current Period Start | Date | Yes | Billing period start |
| Current Period End | Date | Yes | Billing period end |
| Auto Renew | Boolean | Yes | Renewal flag |
| Stripe Subscription ID | Text | No | External payment provider ref |
| Created At | Timestamp | Yes | Subscription start |
| Updated At | Timestamp | Yes | Last modification |

---

### 4.14 Payment

Financial transaction against a subscription.

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| Payment ID | UUID | Yes | Unique payment identifier |
| Subscription ID | UUID | Yes | FK to Subscription |
| Company ID | UUID | Yes | FK to Company |
| Amount | Decimal | Yes | Transaction amount |
| Currency | Text | Yes | ISO 4217 |
| Payment Method | Enum | Yes | `CREDIT_CARD`, `ACH`, `WIRE`, `INVOICE` |
| Status | Enum | Yes | `PENDING`, `COMPLETED`, `FAILED`, `REFUNDED`, `DISPUTED` |
| Stripe Payment ID | Text | No | External transaction reference |
| Invoice Number | Text | No | Generated invoice ID |
| Failure Reason | Text | No | Decline/error message |
| Retry Count | Integer | Yes | Dunning retry attempts (FR-BIL-005) |
| Paid At | Timestamp | No | Successful payment date |
| Created At | Timestamp | Yes | Transaction initiation |

---

### 4.15 AuditLog

Immutable, tamper-evident log of critical system actions.

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| Audit Log ID | UUID | Yes | Unique log entry identifier |
| Company ID | UUID | No | Tenant scope (null for platform-level) |
| User ID | UUID | No | Acting user |
| Entity Type | Text | Yes | e.g., `Application`, `Offer`, `Score` |
| Entity ID | UUID | No | Affected record ID |
| Action | Enum | Yes | `CREATE`, `READ`, `UPDATE`, `DELETE`, `LOGIN`, `LOGOUT`, `EXPORT`, `AI_DECISION` |
| Old Values | JSON | No | Pre-change state |
| New Values | JSON | No | Post-change state |
| IP Address | Text | No | Client IP (FR-AUD-001) |
| User Agent | Text | No | Browser/client identifier |
| AI Model Version | Text | No | For AI decision logs |
| Description | Text | No | Human-readable summary |
| Created At | Timestamp | Yes | Immutable timestamp |

**Business Rules:**
- BUS-008: Audit logs cannot be modified or deleted
- FR-AUD-004: 7-year retention minimum

---

## 5. Domain Enumerations

### 5.1 Application Pipeline Stages (PR-001)

```
APPLIED → SCREENED → AI_INTERVIEW → PANEL_INTERVIEW → EVALUATION → OFFER → HIRED | REJECTED
```

| Stage | Description | Entry Trigger |
|-------|-------------|---------------|
| APPLIED | Candidate submitted application | Application created |
| SCREENED | AI resume screening completed | Parsing + scoring complete |
| AI_INTERVIEW | Async/live AI interview stage | Passed screening threshold |
| PANEL_INTERVIEW | Human panel interview scheduled | AI interview passed |
| EVALUATION | Panel scorecards under review | Interviews completed |
| OFFER | Offer letter generated | Composite score approved |
| HIRED | Offer accepted | Candidate accepts offer |
| REJECTED | Removed from pipeline | Knockout, rejection, or withdrawal |

### 5.2 Subscription Plan Limits

| Tier | Seats | Jobs/Month | AI Interviews/Month | Price/Seat/Mo |
|------|-------|------------|---------------------|---------------|
| Starter | 5 | 10 | 50 | $49 |
| Professional | 25 | 50 | 500 | $89 |
| Enterprise | Unlimited | Unlimited | Unlimited | Custom |

---

## 6. Entity Relationship Summary

```
Company 1 ──── M User
Company 1 ──── M Candidate
Company 1 ──── M Job
Company 1 ──── M Question
Company 1 ──── 1 Subscription
Company 1 ──── M Payment
Company 1 ──── M AuditLog

User M ──── M Role (via UserRole)

Candidate 1 ──── M Resume
Candidate 1 ──── M Application

Job 1 ──── M Application
Job 1 ──── M Question (optional)

Application 1 ──── M Interview
Application 1 ──── M Score
Application 1 ──── 0..1 Offer

Interview 1 ──── M Response
Interview M ──── M User (panelists)

Question 1 ──── M Response

Subscription 1 ──── M Payment

User 1 ──── M AuditLog (actor)
```

---

## 7. Cardinality Matrix

| From Entity | Relationship | To Entity | Cardinality | Optionality |
|-------------|--------------|-----------|-------------|-------------|
| Company | employs | User | 1:M | Mandatory on User side |
| Company | owns | Candidate | 1:M | Mandatory |
| Company | posts | Job | 1:M | Mandatory |
| Company | maintains | Question | 1:M | Mandatory |
| Company | has | Subscription | 1:1 | Mandatory (active tenant) |
| Company | generates | Payment | 1:M | Mandatory |
| Company | scopes | AuditLog | 1:M | Optional (platform logs unscoped) |
| User | assigned | Role | M:M | At least one role required |
| User | creates | Job | 1:M | Optional |
| User | manages | Application | 1:M | Optional (assigned recruiter) |
| User | evaluates | Score | 1:M | Optional (AI scores have no user) |
| User | schedules | Interview | 1:M | Optional |
| Candidate | uploads | Resume | 1:M | At least one for application |
| Candidate | submits | Application | 1:M | Optional |
| Job | receives | Application | 1:M | Optional |
| Application | uses | Resume | M:1 | Mandatory |
| Application | includes | Interview | 1:M | Optional |
| Application | has | Score | 1:M | Optional |
| Application | results in | Offer | 1:0..1 | Optional |
| Interview | contains | Response | 1:M | Optional |
| Interview | references | Question | M:M | Via Response |
| Question | answered in | Response | 1:M | Optional |
| Subscription | billed via | Payment | 1:M | Optional |
| User | performs | AuditLog action | 1:M | Optional |

---

## 8. Data Volume Estimates (Year 1 — Enterprise Tenant)

| Entity | Estimated Records/Tenant/Year | Growth Rate |
|--------|-------------------------------|-------------|
| Users | 50–200 | Linear with hiring team size |
| Candidates | 5,000–25,000 | Seasonal (Q1, Q3 peaks) |
| Resumes | 6,000–30,000 | 1.2× candidates (re-uploads) |
| Jobs | 200–500 | Stable |
| Applications | 8,000–40,000 | 1.5× candidates (multi-apply) |
| Interviews | 3,000–15,000 | 0.4× applications |
| Responses | 15,000–75,000 | 5× interviews (avg questions) |
| Scores | 12,000–50,000 | Screening + panel + composite |
| Offers | 200–500 | ~1× filled positions |
| Payments | 12–24 | Monthly/annual billing |
| AuditLogs | 500,000–2M | High-volume (all CRUD) |

---

## 9. Data Governance & Compliance

| Requirement | Implementation | Entity Impact |
|-------------|----------------|---------------|
| GDPR Right to Erasure (BR-040) | Anonymize PII, retain audit metadata | Candidate, User, Resume |
| EEOC Adverse Impact (BR-007) | Demographic fields in reporting views | Candidate (optional EEO fields) |
| NYC Local Law 144 (BR-005) | Bias audit on AI scores | Score, AuditLog |
| Data Residency (NFR-020) | Region tag on Company | Company |
| Immutable Audit (BUS-008) | Append-only AuditLog table | AuditLog |
| 7-Year Retention (FR-AUD-004) | Partitioned archive strategy | AuditLog, Payment |
| PII Encryption (NFR-007) | AES-256 at rest | Resume, Candidate |

---

## 10. Traceability to Requirements

| Entity | Key BRD Requirements |
|--------|---------------------|
| Company | BR-001, BR-039 |
| Role / User | BR-011, FR-AUTH-007 |
| Candidate / Resume | BR-015, BR-016, BR-038, FR-RM-001 |
| Job | BR-019, BR-020, FR-JM-001 |
| Application | BR-003, BR-004, FR-AIS-001 |
| Interview | BR-014, FR-IS-001, FR-AII-001 |
| Question / Response | FR-AII-001, FR-AII-004, FR-AII-009 |
| Score | BR-017, FR-CE-002, FR-AIS-005 |
| Offer | BR-029, BR-030, BUS-002 |
| Subscription / Payment | BR-008, FR-BIL-001 |
| AuditLog | BR-010, FR-AUD-001, FR-AUD-005 |

---

## 11. Glossary

| Term | Definition |
|------|------------|
| **Tenant** | A Company organization with isolated data |
| **Requisition** | Synonym for Job in hiring context |
| **Pipeline Stage** | Current position of Application in hiring workflow |
| **Knockout Rule** | Automatic disqualification criteria (BUS-010) |
| **Composite Score** | Weighted aggregation of panel evaluations |
| **MRR/ARR** | Monthly/Annual Recurring Revenue from Subscriptions |

---

## 12. Approval

| Role | Name | Date | Signature |
|------|------|------|-----------|
| Business Analyst | Rohit | 06/08/2026 | _________ |
| Solution Architect | _________________ | ___/___/2026 | _________ |
| Data Architect | _________________ | ___/___/2026 | _________ |
| Compliance Lead | _________________ | ___/___/2026 | _________ |

---

*Document Classification: Internal — Data Architecture*
*Next Document: [15_ERD/ERD.md](../15_ERD/ERD.md)*
