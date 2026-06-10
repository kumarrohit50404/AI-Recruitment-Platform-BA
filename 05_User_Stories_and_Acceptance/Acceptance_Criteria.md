# Acceptance Criteria
## HireFlow AI — AI-Powered Recruitment & Interview Management Platform

| Field | Value |
|-------|-------|
| **Document ID** | AC-HFA-2026-001 |
| **Version** | 1.0 |
| **Author** | Rohit, Business Analyst |
| **Status** | Approved |
| **Coverage** | Top 30 User Stories |

---

## 1. Document Purpose

This document provides Gherkin-style acceptance criteria (Given/When/Then) for the 30 highest-priority user stories in the HireFlow AI backlog. Criteria are testable, unambiguous, and suitable for UAT and automated BDD test scenarios.

**Format:**

```gherkin
Feature: [Feature Name]
  Scenario: [Scenario Name]
    Given [precondition]
    And [additional precondition]
    When [action]
    Then [expected outcome]
    And [additional outcome]
```

---

## 2. Acceptance Criteria by Epic

### AC-001: US-AUTH-004 — Enable Multi-Factor Authentication

**Feature:** Multi-Factor Authentication

```gherkin
Feature: Enable MFA for Tenant
  As a Company Admin
  I want to enable multi-factor authentication
  So that organizational accounts are protected against unauthorized access

  Scenario: Company Admin enables TOTP-based MFA
    Given I am logged in as a Company Admin
    And MFA is currently disabled for my tenant
    When I navigate to Security Settings and enable MFA with TOTP
    And I configure MFA as mandatory for all users
    Then MFA is enabled for the tenant
    And all users are prompted to register an authenticator app on next login
    And the configuration change is logged in the audit trail

  Scenario: User completes MFA enrollment
    Given MFA is mandatory for my tenant
    And I am a Recruiter logging in for the first time after MFA activation
    When I scan the QR code with my authenticator app
    And I enter a valid 6-digit TOTP code to confirm enrollment
    Then my MFA device is registered successfully
    And I am redirected to my role-appropriate dashboard

  Scenario: User fails MFA verification
    Given I have MFA enabled on my account
    And I have entered valid email and password credentials
    When I enter an incorrect or expired MFA code
    Then I see the error message "Invalid verification code"
    And I am allowed up to 3 retry attempts before temporary lockout
    And the failed attempt is logged in the authentication audit trail
```

---

### AC-002: US-AUTH-005 — Configure SAML 2.0 SSO

**Feature:** Enterprise SSO Configuration

```gherkin
Feature: SAML 2.0 SSO Configuration
  As a Company Admin
  I want to configure SAML 2.0 SSO for my tenant
  So that employees can log in using corporate credentials

  Scenario: Company Admin configures SAML SSO successfully
    Given I am logged in as a Company Admin
    And SSO is not yet configured for my tenant
    When I navigate to Integrations > SSO Settings
    And I upload the IdP metadata XML and configure the ACS URL
    And I map IdP groups to HireFlow AI roles
    And I click "Test Connection" and the test succeeds
    Then SSO is marked as Active for my tenant
    And users see a "Sign in with SSO" option on the login page

  Scenario: User authenticates via SAML SSO
    Given SAML SSO is active for my tenant
    And I am a Recruiter with an account in the corporate IdP
    When I click "Sign in with SSO" on the login page
    And I authenticate successfully at the IdP
    Then I am redirected to the HireFlow AI recruiter dashboard
    And my session is established without entering a local password
    And the SSO login event is recorded in the audit log

  Scenario: SSO configuration test fails
    Given I am configuring SAML SSO
    When I click "Test Connection" with an invalid or expired certificate
    Then I see the error "SSO configuration test failed"
    And SSO remains in Draft status
    And no users can authenticate via SSO until configuration is fixed
```

---

### AC-003: US-UM-001 — Provision New Tenant Company

**Feature:** Tenant Provisioning

```gherkin
Feature: Provision New Tenant
  As a Super Admin
  I want to provision a new tenant company with default configuration
  So that new customers are onboarded in under 30 minutes

  Scenario: Super Admin creates a new tenant successfully
    Given I am logged in as a Super Admin
    And the company domain "acmecorp.com" is not already registered
    When I navigate to Tenant Management and click "Create New Tenant"
    And I enter company name "Acme Corp", domain "acmecorp.com", tier "Professional", and 25 seats
    And I enter Company Admin details: name "Jane Smith", email "jane@acmecorp.com"
    And I click "Provision Tenant"
    Then a new isolated tenant is created within 30 minutes
    And a Company Admin account is created for jane@acmecorp.com
    And a welcome email with setup instructions is sent to the Company Admin
    And the tenant appears in the platform dashboard with status "Active"

  Scenario: Duplicate domain is rejected
    Given a tenant with domain "acmecorp.com" already exists
    When I attempt to create a new tenant with domain "acmecorp.com"
    Then I see the error "Domain already in use"
    And no new tenant is created
```

---

### AC-004: US-UM-003 — Create User Accounts

**Feature:** User Account Creation

```gherkin
Feature: Create User Account
  As a Company Admin
  I want to create individual user accounts with role assignment
  So that recruiters and panel members can access the platform

  Scenario: Company Admin creates a new recruiter account
    Given I am logged in as a Company Admin
    And my subscription has available seats (current usage < seat limit)
    When I navigate to User Management and click "Add User"
    And I enter name "John Doe", email "john@acmecorp.com", role "Recruiter", department "Engineering"
    And I click "Create User"
    Then a new user account is created with status "Active"
    And a welcome email with setup instructions is sent to john@acmecorp.com
    And the license utilization dashboard reflects the new seat consumption

  Scenario: Seat limit prevents user creation
    Given my subscription has 25 seats and 25 are already in use
    When I attempt to create a new user account
    Then I see the message "Seat limit reached. Upgrade your plan to add more users."
    And no new user account is created
```

---

### AC-005: US-UM-004 — Bulk Import Users via CSV

**Feature:** Bulk User Import

```gherkin
Feature: Bulk Import Users
  As a Company Admin
  I want to bulk import users via CSV with validation
  So that I can provision large teams efficiently at go-live

  Scenario: Successful bulk import of valid users
    Given I am logged in as a Company Admin
    And I have downloaded the CSV template
    And my CSV file contains 50 valid user rows with required fields
    When I upload the CSV file to User Management > Bulk Import
    And I review the preview showing 50 valid rows
    And I click "Confirm Import"
    Then 50 user accounts are created successfully
    And an import summary shows "50 succeeded, 0 failed"
    And welcome emails are sent to all 50 imported users

  Scenario: Partial import with validation errors
    Given my CSV file contains 50 rows where 5 have invalid email formats
    When I upload the CSV and confirm import
    Then 45 user accounts are created successfully
    And the import summary shows "45 succeeded, 5 failed"
    And I can download an error report detailing the 5 failed rows with reasons
```

---

### AC-006: US-RES-001 — Upload Resume

**Feature:** Resume Upload

```gherkin
Feature: Candidate Resume Upload
  As a Candidate
  I want to upload my resume in PDF, DOCX, or TXT format
  So that I can apply to jobs with my existing documents

  Scenario: Candidate uploads a valid PDF resume
    Given I am a Candidate on the job application page
    And I have a resume file "resume.pdf" that is 2MB in size
    When I drag and drop the file into the upload zone
    Then the file upload completes successfully
    And I see a confirmation message "Resume uploaded successfully"
    And the resume is stored in encrypted storage with tenant isolation

  Scenario: Unsupported file format is rejected
    Given I am a Candidate on the job application page
    When I attempt to upload a file "resume.jpg"
    Then I see the error "Accepted formats: PDF, DOCX, TXT"
    And the file is not stored

  Scenario: Oversized file is rejected
    Given I am a Candidate on the job application page
    When I attempt to upload a file larger than 10MB
    Then I see the error "File size must not exceed 10MB"
    And the file is not stored
```

---

### AC-007: US-RES-004 — Parse Resume

**Feature:** Resume Parsing

```gherkin
Feature: Resume Parsing
  As the System
  I want to parse resumes into structured fields within 30 seconds
  So that recruiters receive searchable candidate profiles quickly

  Scenario: Successful resume parsing
    Given a Candidate has uploaded a valid PDF resume
    When the parsing engine processes the resume
    Then structured fields are extracted within 30 seconds
    And the profile displays name, email, phone, skills, work history, and education
    And skills are normalized against the skill taxonomy
    And total years of experience is calculated from work history

  Scenario: Low-confidence parsing flags fields for review
    Given a Candidate has uploaded a complex infographic resume
    When the parsing engine processes the resume with low confidence on the "skills" field
    Then the skills field is flagged with a low-confidence indicator
    And the recruiter can manually correct the parsed value
```

---

### AC-008: US-RES-007 — Merge Duplicate Profiles

**Feature:** Duplicate Candidate Merge

```gherkin
Feature: Merge Duplicate Candidate Profiles
  As a Recruiter
  I want to detect and merge duplicate candidate profiles
  So that I maintain a single canonical record per person

  Scenario: Recruiter merges confirmed duplicates
    Given the system has flagged two candidate profiles with matching email "jane@email.com"
    And I am a Recruiter with candidate management permissions
    When I open the duplicate review screen
    And I select the primary profile to retain
    And I confirm the merge
    Then the profiles are consolidated into a single record
    And application history from both profiles is preserved
    And the application with the highest AI score is retained per BUS-013
    And the merge action is logged in the audit trail

  Scenario: Recruiter dismisses false duplicate flag
    Given the system has flagged two profiles as potential duplicates
    When I review the profiles and click "Not a Duplicate"
    Then the duplicate flag is dismissed
    And the system suppresses re-flagging for 90 days
```

---

### AC-009: US-AIS-001 — AI Candidate Ranking

**Feature:** AI Candidate Ranking

```gherkin
Feature: AI Candidate Ranking
  As a Recruiter
  I want to see candidates ranked by AI match score (0–100)
  So that I focus on the most qualified applicants first

  Scenario: Candidates are ranked after AI screening
    Given a published job requisition with defined requirements
    And knockout rules are configured for the requisition
    And 25 candidates have applied with parsed resumes
    When AI screening completes for the requisition
    Then each candidate receives a match score between 0 and 100
    And candidates are displayed in descending order by match score
    And candidates scoring below 40 are auto-rejected unless overridden
    And the ranked list is visible on the recruiter pipeline view

  Scenario: Batch screening completes within SLA
    Given a requisition has 500 candidate applications
    When AI screening is triggered
    Then all 500 resumes are processed within 10 minutes
    And the recruiter receives a notification when screening is complete
```

---

### AC-010: US-AIS-003 — Configure Knockout Rules

**Feature:** Knockout Rules Configuration

```gherkin
Feature: Configure Knockout Rules
  As a Company Admin
  I want to configure knockout rules for minimum qualifications
  So that unqualified candidates are auto-filtered before recruiter review

  Scenario: Company Admin creates knockout rules for a job family
    Given I am logged in as a Company Admin
    When I navigate to Hiring Policies > Knockout Rules
    And I select job family "Software Engineering"
    And I define rules: minimum 3 years experience, required skill "Python", Bachelor's degree
    And I save the configuration
    Then knockout rules are associated with the Software Engineering job family
    And rules are enforced during the next AI screening run for matching requisitions
    And the configuration change is logged in the audit trail

  Scenario: Screening blocked without knockout rules
    Given a requisition has no knockout rules defined
    When a Recruiter attempts to run AI screening
    Then screening is blocked
    And the message "Configure knockout rules before screening" is displayed
```

---

### AC-011: US-AIS-004 — Explainable AI Rationale

**Feature:** Explainable AI Screening

```gherkin
Feature: Explainable AI Rationale
  As a Recruiter
  I want to view explainable AI rationale for each screening score
  So that I understand why a candidate was ranked or rejected

  Scenario: Recruiter views AI scoring rationale
    Given AI screening has completed for a candidate with score 78
    When I open the candidate profile and view the AI Screening tab
    Then I see the overall match score of 78
    And I see a breakdown by criteria: skills, experience, education, other
    And I see a list of matched skills highlighted in green
    And I see a list of missing skills highlighted in red
    And I see a natural-language explanation of the score

  Scenario: Compliance officer reviews AI explainability data
    Given AI screening has been performed on a candidate
    When a Compliance Team member searches audit logs for the screening decision
    Then the log includes input data, output score, model version, and rationale
```

---

### AC-012: US-AIS-007 — Override AI Score

**Feature:** AI Score Override

```gherkin
Feature: Override AI Screening Score
  As a Recruiter
  I want to override an AI screening score with mandatory justification
  So that I can advance strong candidates the AI may have undervalued

  Scenario: Recruiter overrides auto-rejection with justification
    Given a candidate was auto-rejected with AI score 35
    And I am a Recruiter with override permissions
    When I select the candidate and click "Override AI Score"
    And I change the status to "Advance" and enter justification of at least 50 characters
    And I confirm the override
    Then the candidate status is updated to "Screened – Advanced"
    And the override is logged with my user ID, original score, new status, and justification

  Scenario: Override blocked without justification
    Given a candidate has an AI score I want to override
    When I attempt to save the override without entering a justification
    Then the save is prevented
    And the justification field is highlighted as required
```

---

### AC-013: US-JOB-006 — Approve Job Requisition

**Feature:** Job Requisition Approval

```gherkin
Feature: Approve Job Requisition
  As an HR Manager
  I want to approve or reject job requisitions before they go live
  So that hiring aligns with budget and headcount plans

  Scenario: HR Manager approves a requisition
    Given a Recruiter has submitted a job requisition with status "Pending Approval"
    And I am an HR Manager with approval permissions
    When I open the requisition and review title, description, salary band, and hiring team
    And I click "Approve"
    Then the requisition status changes to "Approved"
    And the assigned Recruiter is notified of the approval
    And the approval event is logged in the audit trail

  Scenario: HR Manager rejects a requisition with reason
    Given a job requisition is in "Pending Approval" status
    When I click "Reject" and enter reason "Salary band exceeds department budget"
    Then the requisition status changes to "Rejected"
    And the Recruiter is notified with the rejection reason
    And the requisition returns to the Recruiter for revision
```

---

### AC-014: US-JOB-007 — Publish Job to Career Portal

**Feature:** Job Publication

```gherkin
Feature: Publish Job to Career Portal
  As a Recruiter
  I want to publish approved jobs to the company career portal
  So that candidates can discover and apply to open positions

  Scenario: Recruiter publishes an approved job
    Given a job requisition has status "Approved"
    And the company career portal is configured
    When I click "Publish to Career Portal"
    Then the requisition status changes to "Published / Open"
    And a unique career portal URL is generated for the job
    And the job appears on the company career portal job listings
    And I receive a confirmation with the shareable job URL

  Scenario: Publication blocked for unapproved requisition
    Given a job requisition has status "Draft" or "Pending Approval"
    When I attempt to publish the job
    Then publication is blocked
    And I see the message "Job must be approved by HR Manager before publishing"
```

---

### AC-015: US-JOB-009 — Candidate Self-Apply

**Feature:** Candidate Job Application

```gherkin
Feature: Candidate Self-Apply
  As a Candidate
  I want to browse and apply to published jobs on the career portal
  So that I can pursue opportunities at companies I am interested in

  Scenario: Candidate completes a job application
    Given a job is published and accepting applications on the career portal
    And I am a Candidate with a valid PDF resume
    When I select the job and click "Apply Now"
    And I create an account or log in to my existing profile
    And I upload my resume and complete application questions
    And I submit the application
    Then an application record is created in "Applied" stage
    And AI screening is queued automatically
    And I receive a confirmation email with an application tracking link

  Scenario: Duplicate application is prevented
    Given I have already applied to job requisition JOB-1234
    When I attempt to apply to the same job again
    Then I see the message "You have already applied to this position"
    And no duplicate application is created
```

---

### AC-016: US-SCH-001 — Calendar Integration for Scheduling

**Feature:** Calendar Integration

```gherkin
Feature: Calendar Integration for Interview Scheduling
  As a Recruiter
  I want to view panel member availability from calendar integration
  So that I schedule interviews without manual availability checks

  Scenario: Recruiter views panel availability from integrated calendars
    Given Interview Panel members have connected Google or Outlook calendars
    And a candidate is in the interview stage
    When I navigate to Schedule Interview and select panel members
    Then the system displays each panel member's available time slots for the next 14 days
    And busy times from their calendars are excluded
    And the top 5 slots ranked by combined panel availability are suggested

  Scenario: Panel member without calendar integration
    Given a panel member has not connected their calendar
    When I attempt to schedule an interview including that panel member
    Then I see a warning "Calendar not connected for [Panel Member Name]"
    And I can manually enter availability for that panel member
```

---

### AC-017: US-SCH-004 — Candidate Self-Schedule

**Feature:** Candidate Self-Scheduling

```gherkin
Feature: Candidate Self-Schedule Interview
  As a Candidate
  I want to select my preferred interview slot from available options
  So that I can schedule without back-and-forth emails

  Scenario: Candidate selects and confirms an interview slot
    Given a Recruiter has sent me a self-scheduling link with available slots
    And I am in the interview stage for the application
    When I click the scheduling link and view available time slots
    And I select a slot on Tuesday at 2:00 PM EST
    And I click "Confirm"
    Then the interview is booked for Tuesday at 2:00 PM EST
    And calendar invites are sent to all panel members and me
    And the Recruiter is notified of the confirmed interview
    And reminder notifications are scheduled for 24 hours and 1 hour before

  Scenario: Selected slot is no longer available
    Given I am viewing available interview slots
    When I select a slot that was just booked by another candidate
    Then I see the message "This slot is no longer available"
    And the slot list refreshes with current availability
```

---

### AC-018: US-AII-002 — Asynchronous AI Video Interview

**Feature:** AI Video Interview

```gherkin
Feature: Asynchronous AI Video Interview
  As a Candidate
  I want to complete an asynchronous video interview
  So that I can interview on my own schedule without live coordination

  Scenario: Candidate completes a full AI video interview
    Given I have been advanced to the AI Interview stage
    And I have received an AI interview invitation with a valid link
    When I click the interview link and grant camera/microphone permissions
    And I view each AI-generated question and record my video response
    And I complete all questions within the 30-minute time limit
    Then all video responses are recorded and stored
    And responses are transcribed in real-time
    And each response is scored on a 1–5 rubric scale
    And an AI interview summary report is generated
    And the Recruiter is notified of my completed interview

  Scenario: Candidate uses practice mode before live interview
    Given I have not yet started the live AI interview
    When I click "Practice Mode" on the interview landing page
    Then I can experience sample questions without recording being saved
    And I receive tips for optimal video interview performance
```

---

### AC-019: US-AII-005 — Review AI Interview Recording

**Feature:** AI Interview Review

```gherkin
Feature: Review AI Interview Recording
  As a Recruiter
  I want to review AI interview recordings and transcripts
  So that I can make informed advancement decisions

  Scenario: Recruiter reviews completed AI interview
    Given a Candidate has completed an AI video interview
    And the AI summary report has been generated
    When I navigate to the candidate profile > AI Interview tab
    Then I see the overall AI interview score and per-question breakdown
    And I can play video recordings for each question
    And I can read transcripts alongside each recording
    And I can view AI scoring rationale per rubric criterion
    And I can add review notes and select Advance, Reject, or Hold

  Scenario: Recording unavailable due to retention policy
    Given an AI interview recording is older than 12 months
    When I attempt to play the recording
    Then I see the message "Recording no longer available per retention policy"
    And the transcript and scores remain accessible
```

---

### AC-020: US-EVL-001 — Digital Scorecard

**Feature:** Panel Evaluation Scorecard

```gherkin
Feature: Digital Scorecard Submission
  As an Interview Panel member
  I want to complete a digital scorecard with weighted criteria
  So that my evaluation is structured and comparable across candidates

  Scenario: Panel member submits a complete scorecard
    Given I have conducted an interview for a candidate
    And a scorecard template is assigned for the role/level
    When I open the digital scorecard from my post-interview notification
    And I rate each criterion on the 1–5 scale with behavioral anchor guidance
    And I select recommendation "Hire" and enter written feedback of at least 100 characters
    And I click "Submit Scorecard"
    Then the scorecard is saved successfully
    And the composite score is updated if minimum evaluations are met
    And the HR Manager is notified when all panel evaluations are complete

  Scenario: Incomplete scorecard is rejected
    Given I am completing a scorecard
    When I attempt to submit without rating all required criteria
    Then submission is prevented
    And missing required fields are highlighted
```

---

### AC-021: US-EVL-004 — Minimum Panel Evaluations

**Feature:** Minimum Evaluation Requirement

```gherkin
Feature: Minimum Panel Evaluations
  As the System
  I want to require minimum 2 panel evaluations before advancement
  So that decisions are not made on a single interviewer's opinion

  Scenario: Candidate blocked from offer stage with only 1 evaluation
    Given a candidate has completed panel interviews
    And only 1 of 2 assigned panel members has submitted a scorecard
    When an HR Manager attempts to advance the candidate to the Offer stage
    Then advancement is blocked
    And the message "Minimum 2 panel evaluations required" is displayed
    And the system shows which panel members have not yet submitted

  Scenario: Candidate advances after 2 evaluations submitted
    Given a candidate has 2 panel evaluations submitted
    And both evaluations include Hire recommendations
    When the HR Manager views the evaluation summary
    Then the composite score is calculated from both evaluations
    And the candidate is eligible for offer generation
```

---

### AC-022: US-OFR-001 — Generate Offer Letter

**Feature:** Offer Letter Generation

```gherkin
Feature: Generate Offer Letter
  As an HR Manager
  I want to generate offer letters from configurable templates
  So that offers are professional and consistent across the organization

  Scenario: HR Manager generates an offer letter
    Given a candidate has ≥2 panel evaluations with Hire recommendations
    And all evaluations are complete
    When I navigate to the candidate profile > Offer tab
    And I select an offer template and enter salary, start date, and benefits
    And I click "Preview Offer"
    Then a PDF offer letter is generated with candidate and job details populated
    And I can review the PDF before sending
    And the offer is saved in Draft status pending approval

  Scenario: Offer generation blocked for incomplete evaluations
    Given a candidate has only 1 panel evaluation submitted
    When I attempt to generate an offer letter
    Then offer generation is blocked
    And I see details of missing evaluations
```

---

### AC-023: US-OFR-003 — VP HR Approval for High-Value Offers

**Feature:** Multi-Level Offer Approval

```gherkin
Feature: VP HR Approval for High-Value Offers
  As an HR Manager
  I want to route offers above $150K to VP HR for additional approval
  So that high-value offers receive executive oversight

  Scenario: High-value offer routed to VP HR
    Given I have generated an offer with salary $175,000
    When I submit the offer for approval
    Then the offer is routed to VP HR for additional approval per BUS-002
    And the VP HR receives a notification with offer details
    And the offer status is "Pending VP Approval"
    And the offer cannot be sent to the candidate until VP HR approves

  Scenario: Standard offer requires only HR Manager approval
    Given I have generated an offer with salary $120,000
    When I submit the offer for approval
    Then VP HR approval is not required
    And I can approve and send the offer directly
```

---

### AC-024: US-OFR-006 — Candidate Accept/Decline Offer

**Feature:** Offer Response

```gherkin
Feature: Candidate Offer Response
  As a Candidate
  I want to accept or decline an offer through the secure portal
  So that my decision is captured without email ambiguity

  Scenario: Candidate accepts an offer
    Given I have received an offer email with a secure acceptance link
    And the offer has not expired
    When I click the link and review the offer details
    And I click "Accept Offer"
    Then my offer status is updated to "Accepted"
    And the HR Manager and Recruiter are notified immediately
    And the acceptance timestamp is recorded in the audit trail

  Scenario: Candidate declines an offer with reason
    Given I have received a valid offer
    When I click "Decline Offer" and select reason "Accepted another offer"
    Then my offer status is updated to "Declined"
    And the decline reason is captured for analytics
    And the HR Manager and Recruiter are notified
```

---

### AC-025: US-RPT-001 — Executive Hiring Dashboard

**Feature:** Executive Dashboard

```gherkin
Feature: Executive Hiring Dashboard
  As an HR Manager
  I want to view an executive dashboard with 10 core hiring KPIs
  So that I have real-time visibility into hiring performance

  Scenario: HR Manager views executive dashboard with live data
    Given I am logged in as an HR Manager
    And active requisitions and candidate data exist in the system
    When I navigate to Analytics > Executive Dashboard
    Then I see 10 core KPIs: open requisitions, time-to-hire, cost-per-hire, offer acceptance rate, pipeline conversion, AI screening volume, interview completion rate, diversity metrics, recruiter productivity, and requisition aging
    And I see a real-time hiring pipeline funnel visualization
    And I see a department-wise hiring breakdown
    And each KPI displays a "Last updated" timestamp

  Scenario: HR Manager drills down from KPI to detail
    Given I am viewing the Executive Dashboard
    When I click the "Time-to-Hire" KPI tile
    Then I see a detailed breakdown by department and requisition
    And I can navigate to individual candidate records from the detail view
```

---

### AC-026: US-RPT-008 — EEOC Adverse Impact Report

**Feature:** EEOC Compliance Reporting

```gherkin
Feature: EEOC Adverse Impact Report
  As a Compliance Team member
  I want to generate EEOC adverse impact analysis reports
  So that regulatory filings are supported with accurate data

  Scenario: Compliance Team generates adverse impact report
    Given sufficient hiring data exists across demographic groups
    And I am logged in as a Compliance Team member
    When I navigate to Compliance > EEOC Reports
    And I select date range "Q1 2026" and click "Generate Report"
    Then the report displays selection rates by demographic group
    And the report calculates adverse impact ratios using the four-fifths rule
    And groups with ratios below 0.80 are flagged for review
    And the report is exportable in PDF and CSV formats

  Scenario: Insufficient data for statistical analysis
    Given a demographic group has fewer than 30 records in the selected period
    When I generate the adverse impact report
    Then that group is noted as "Insufficient sample size"
    And the report includes a data completeness disclaimer
```

---

### AC-027: US-BIL-001 — Subscription Tier Selection

**Feature:** Subscription Management

```gherkin
Feature: Subscription Tier Selection
  As a Company Admin
  I want to select from Starter, Professional, and Enterprise subscription tiers
  So that I choose a plan that matches my organization's needs

  Scenario: Company Admin selects and activates a subscription plan
    Given I am logged in as a Company Admin
    And my tenant is on a 14-day free trial
    When I navigate to Settings > Subscription & Billing
    And I compare Starter, Professional, and Enterprise tier features and pricing
    And I select "Professional" plan with 25 seats and annual billing
    And I enter valid payment details via Stripe
    And I click "Subscribe"
    Then my subscription is activated on the Professional tier
    And feature limits are updated to Professional tier entitlements
    And an invoice is generated and emailed to me

  Scenario: Feature access restricted by tier
    Given I am on the Starter subscription tier
    When I attempt to access AI Interview features (Enterprise/Professional only)
    Then access is restricted
    And I see an upgrade prompt with tier comparison details
```

---

### AC-028: US-BIL-004 — Failed Payment Dunning

**Feature:** Payment Dunning

```gherkin
Feature: Failed Payment Dunning
  As the System
  I want to retry failed payments with a 3-attempt dunning process
  So that involuntary churn from transient payment issues is minimized

  Scenario: System retries failed payment automatically
    Given a Company Admin's subscription payment fails on the billing date
    When the dunning process initiates
    Then the system retries payment after 3 days (attempt 2)
    And the system retries payment after 7 days (attempt 3)
    And the Company Admin receives email notification after each failed attempt
    And if payment succeeds on any retry, the subscription remains active

  Scenario: Subscription suspended after 3 failed attempts
    Given all 3 payment retry attempts have failed
    When the dunning process completes
    Then the subscription status changes to "Suspended"
    And the Company Admin receives a final notice with payment update instructions
    And users can view data but cannot create new requisitions or process candidates
```

---

### AC-029: US-NOT-001 — Pipeline Stage Notifications

**Feature:** Candidate Pipeline Notifications

```gherkin
Feature: Pipeline Stage Notifications
  As a Candidate
  I want to receive email notifications at each pipeline stage
  So that I always know the status of my application

  Scenario: Candidate receives notification on stage advancement
    Given I have applied to a job and my application is in "Applied" stage
    When AI screening completes and I am advanced to "AI Interview" stage
    Then I receive an email notification within 5 minutes
    And the email includes my current stage, next steps, and a link to my application dashboard
    And the notification uses the tenant's customized email template

  Scenario: All 15 defined event types trigger notifications
    Given notification templates are configured for all 15 event types
    When any defined event occurs (application received, screening complete, interview scheduled, offer sent, etc.)
    Then the appropriate stakeholder receives the configured notification
    And the notification is logged with delivery status
```

---

### AC-030: US-AUD-005 — DSAR Processing

**Feature:** Data Subject Access Request

```gherkin
Feature: DSAR Processing
  As a Compliance Team member
  I want to process DSAR requests within 72 hours
  So that GDPR data subject rights are fulfilled on time

  Scenario: Compliance Team fulfills a data access request
    Given a Candidate has submitted a DSAR access request via the privacy portal
    And the request has been assigned reference number DSAR-2026-0042
    When I open the DSAR queue and verify the candidate's identity
    And I click "Generate Data Export"
    Then the system compiles all candidate data within 72 hours of request submission
    And the export is delivered in machine-readable JSON format via secure download link
    And the DSAR status is updated to "Completed"
    And all actions are logged in the audit trail

  Scenario: Compliance Team fulfills a data deletion request
    Given a Candidate has submitted a DSAR deletion request
    And the candidate's identity has been verified
    And no active legal hold applies to the candidate's data
    When I process the deletion request
    Then all candidate PII is anonymized or deleted per retention policies
    And the DSAR is completed within 72 hours
    And a completion confirmation is sent to the candidate

  Scenario: DSAR SLA escalation alert
    Given a DSAR request has been open for 60 hours without completion
    When the SLA monitoring job runs
    Then an escalation alert is sent to the Compliance Team lead and DPO
    And the DSAR ticket is flagged as "At Risk" in the queue
```

---

## 3. Traceability Matrix

| AC ID | User Story | Epic | Related Use Case | Test Priority |
|-------|------------|------|------------------|---------------|
| AC-001 | US-AUTH-004 | Authentication | UC-001 | P1 |
| AC-002 | US-AUTH-005 | Authentication | UC-002 | P1 |
| AC-003 | US-UM-001 | User Management | UC-003 | P1 |
| AC-004 | US-UM-003 | User Management | UC-004 | P1 |
| AC-005 | US-UM-004 | User Management | UC-005 | P2 |
| AC-006 | US-RES-001 | Resume | UC-006 | P1 |
| AC-007 | US-RES-004 | Resume | UC-006 | P1 |
| AC-008 | US-RES-007 | Resume | UC-007 | P2 |
| AC-009 | US-AIS-001 | AI Screening | UC-008 | P1 |
| AC-010 | US-AIS-003 | AI Screening | UC-009 | P1 |
| AC-011 | US-AIS-004 | AI Screening | UC-008 | P1 |
| AC-012 | US-AIS-007 | AI Screening | UC-010 | P2 |
| AC-013 | US-JOB-006 | Jobs | UC-012 | P1 |
| AC-014 | US-JOB-007 | Jobs | UC-012 | P1 |
| AC-015 | US-JOB-009 | Jobs | UC-013 | P1 |
| AC-016 | US-SCH-001 | Scheduling | UC-014 | P1 |
| AC-017 | US-SCH-004 | Scheduling | UC-015 | P2 |
| AC-018 | US-AII-002 | AI Interview | UC-017 | P1 |
| AC-019 | US-AII-005 | AI Interview | UC-018 | P1 |
| AC-020 | US-EVL-001 | Evaluation | UC-019 | P1 |
| AC-021 | US-EVL-004 | Evaluation | UC-019 | P1 |
| AC-022 | US-OFR-001 | Offers | UC-020 | P1 |
| AC-023 | US-OFR-003 | Offers | UC-020 | P2 |
| AC-024 | US-OFR-006 | Offers | UC-020 | P1 |
| AC-025 | US-RPT-001 | Reporting | UC-021 | P1 |
| AC-026 | US-RPT-008 | Reporting | UC-024 | P2 |
| AC-027 | US-BIL-001 | Billing | UC-022 | P2 |
| AC-028 | US-BIL-004 | Billing | UC-022 | P2 |
| AC-029 | US-NOT-001 | Notifications | UC-013 | P1 |
| AC-030 | US-AUD-005 | Audit | UC-023 | P1 |

---

## 4. Approval

| Role | Name | Date | Signature |
|------|------|------|-----------|
| Product Owner | VP Talent Acquisition | ___/___/2026 | _________ |
| Business Analyst | Rohit | 06/08/2026 | _________ |
| QA Lead | _________________ | ___/___/2026 | _________ |

---

*Document Classification: Internal — Test Requirements*
