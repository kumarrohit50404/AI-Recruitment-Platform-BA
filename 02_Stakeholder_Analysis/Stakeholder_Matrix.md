# Stakeholder Analysis Matrix
## AI-Powered Recruitment & Interview Management Platform

| Document ID | SA-HFA-2026-001 |
|-------------|-----------------|
| Version | 1.0 |
| Author | Rohit, Business Analyst |

---

## 1. Stakeholder Overview

| # | Stakeholder | Type | Influence | Interest | Engagement Strategy |
|---|-------------|------|-----------|----------|---------------------|
| 1 | Super Admin | Internal/Platform | High | High | Weekly steering committee |
| 2 | Company Admin | Internal/Customer | High | High | Bi-weekly workshops |
| 3 | Recruiter | Internal/End User | Medium | High | Daily standups, UAT |
| 4 | HR Manager | Internal/End User | High | High | Sprint reviews, UAT |
| 5 | Interview Panel | Internal/End User | Medium | Medium | Training sessions, feedback |
| 6 | Candidate | External/End User | Low | High | Usability testing, surveys |
| 7 | Finance Team | Internal/Support | Medium | Medium | Monthly billing reviews |
| 8 | Compliance Team | Internal/Governance | High | High | Compliance checkpoints |

---

## 2. Detailed Stakeholder Profiles

### 2.1 Super Admin

| Attribute | Detail |
|-----------|--------|
| **Role** | Platform owner; manages all tenant companies |
| **Primary Users** | HireFlow AI operations team (3-5 staff) |

**Responsibilities:**
- Provision and deprovision company tenants
- Configure global platform settings and feature flags
- Monitor system health, uptime, and performance
- Manage subscription tiers and pricing
- Handle escalated support tickets across tenants
- Oversee AI model configuration and bias audit schedules

**Pain Points:**
- No unified view across tenant environments
- Manual tenant onboarding takes 2-3 days
- Difficult to diagnose cross-tenant performance issues
- Revenue leakage from unmanaged trial accounts
- Lack of platform-wide analytics

**Goals:**
- Single pane of glass for all tenant management
- Automated tenant provisioning (<30 minutes)
- 99.9% platform uptime
- Reduce support ticket resolution time by 50%
- Maximize SaaS revenue and minimize churn

**Expectations:**
- Real-time platform dashboard with tenant health metrics
- One-click tenant creation with default configurations
- Granular feature flag controls per tenant
- Automated billing reconciliation
- Comprehensive audit trail for all admin actions

---

### 2.2 Company Admin

| Attribute | Detail |
|-----------|--------|
| **Role** | Organization-level administrator |
| **Primary Users** | IT/HR ops managers at customer companies |

**Responsibilities:**
- Configure company profile, branding, and departments
- Manage user accounts (recruiters, HR, panel members)
- Set hiring policies, approval chains, and knockout rules
- Configure integrations (SSO, HRIS, calendar)
- Manage subscription and billing for their organization
- Define role permissions and data access policies

**Pain Points:**
- Complex user provisioning across departments
- No self-service for policy configuration
- Difficulty tracking license utilization
- Integration setup requires vendor support tickets
- Inconsistent permissions leading to data exposure risks

**Goals:**
- Self-service admin portal for all company settings
- Bulk user import from Active Directory/HRIS
- Clear license usage dashboard
- Plug-and-play SSO configuration
- Department-level hiring policy templates

**Expectations:**
- Intuitive admin console with guided setup wizard
- Role-based permission matrix with templates
- Usage reports showing active vs. licensed users
- SSO setup completed in <1 hour without vendor help
- White-label branding options (logo, colors, email templates)

---

### 2.3 Recruiter

| Attribute | Detail |
|-----------|--------|
| **Role** | Primary day-to-day platform user |
| **Primary Users** | Talent acquisition specialists (5-50 per company) |

**Responsibilities:**
- Create and publish job requisitions
- Review AI-screened candidate rankings
- Schedule and conduct interviews
- Communicate with candidates throughout the pipeline
- Provide feedback and move candidates through stages
- Generate requisition-level reports

**Pain Points:**
- Spending 23+ hours/week on manual resume screening
- Juggling 6+ tools (email, ATS, calendar, spreadsheets)
- No visibility into candidate pipeline health
- Scheduling interviews requires excessive back-and-forth
- Duplicate candidates across requisitions
- Slow system response times frustrate daily workflow

**Goals:**
- AI-ranked candidate shortlists delivered instantly
- One-click interview scheduling with calendar sync
- Unified inbox for all candidate communications
- Pipeline kanban view with drag-and-drop stage changes
- Mobile-friendly access for on-the-go updates

**Expectations:**
- Top-10 candidate list within 5 minutes of job posting
- 90% reduction in scheduling email exchanges
- Real-time notifications for candidate actions
- Bulk actions (reject, advance, email) on candidate lists
- Integration with LinkedIn and job boards for sourcing

---

### 2.4 HR Manager

| Attribute | Detail |
|-----------|--------|
| **Role** | Hiring oversight, approvals, and strategic reporting |
| **Primary Users** | HR directors, talent acquisition managers |

**Responsibilities:**
- Approve job requisitions and salary bands
- Review final candidate recommendations
- Approve/reject offer letters
- Monitor hiring metrics and department fill rates
- Ensure compliance with hiring policies and regulations
- Manage headcount planning alignment

**Pain Points:**
- No real-time visibility into hiring pipeline
- Approval bottlenecks delay offers by 3-5 days
- Reports require manual Excel compilation monthly
- Cannot compare recruiter performance objectively
- Compliance documentation scattered across systems
- Budget vs. actual hiring cost tracking is manual

**Goals:**
- Executive dashboard with live hiring KPIs
- Mobile approval workflows for requisitions and offers
- Automated compliance reports for audits
- Department-level hiring velocity tracking
- Predictive analytics for time-to-fill forecasting

**Expectations:**
- One-page executive summary updated in real-time
- Push notifications for pending approvals
- Drill-down from KPI to individual candidate level
- Export-ready reports for board presentations
- EEOC/diversity metrics automatically calculated

---

### 2.5 Interview Panel

| Attribute | Detail |
|-----------|--------|
| **Role** | Subject matter experts conducting/evaluating interviews |
| **Primary Users** | Hiring managers, technical leads, team members |

**Responsibilities:**
- Conduct scheduled interviews (live or review AI recordings)
- Complete structured evaluation scorecards
- Provide written feedback and hiring recommendations
- Participate in debrief sessions
- Submit availability for interview scheduling

**Pain Points:**
- No standardized evaluation criteria across interviewers
- Interview feedback submitted late or not at all (38% non-compliance)
- Unprepared for interviews due to missing candidate context
- Calendar conflicts cause rescheduling delays
- Subjective scoring leads to hiring disagreements

**Goals:**
- Pre-populated candidate brief before each interview
- Standardized digital scorecards with rubric guidance
- 5-minute feedback submission post-interview
- Calendar integration showing only available slots
- Historical comparison of candidate responses

**Expectations:**
- One-page candidate summary with resume highlights
- Guided scorecard with behavioral anchors
- Reminder notifications 1 hour before interview
- Ability to review AI interview recordings before live session
- Anonymous calibration reports to reduce bias

---

### 2.6 Candidate

| Attribute | Detail |
|-----------|--------|
| **Role** | External user applying and interviewing for positions |
| **Primary Users** | Job seekers across all levels |

**Responsibilities:**
- Create profile and upload resume
- Apply to published job openings
- Complete AI pre-screen interviews
- Attend scheduled live interviews
- Respond to offer communications
- Provide interview feedback (post-process survey)

**Pain Points:**
- Repetitive data entry across multiple applications
- No visibility into application status ("black hole" effect)
- Confusing interview scheduling process
- AI interviews feel impersonal and unclear
- Long gaps between stages without communication
- Mobile experience is poor on current systems

**Goals:**
- Single profile applicable to multiple jobs
- Transparent application status tracking
- Self-service interview scheduling from available slots
- Clear instructions for AI interview process
- Timely notifications at every pipeline stage

**Expectations:**
- Application completion in <10 minutes
- Status dashboard showing current stage and next steps
- 3-click interview scheduling
- Professional, branded experience reflecting employer
- Feedback survey and response within 48 hours of decision

---

### 2.7 Finance Team

| Attribute | Detail |
|-----------|--------|
| **Role** | Revenue management, invoicing, and financial reporting |
| **Primary Users** | Finance managers, accounts receivable |

**Responsibilities:**
- Configure subscription plans and pricing tiers
- Process payments and manage billing cycles
- Generate revenue reports and forecasts
- Handle refund and credit requests
- Reconcile payment gateway transactions
- Support audit and tax reporting requirements

**Pain Points:**
- Manual invoice generation for enterprise clients
- Revenue recognition complexity with annual contracts
- Payment failures not proactively managed (12% involuntary churn)
- No integration with ERP (NetSuite) for automated journal entries
- Difficulty tracking MRR/ARR across plan changes

**Goals:**
- Automated billing with dunning management
- Real-time MRR/ARR dashboard
- ERP integration for seamless revenue posting
- Self-service upgrade/downgrade with prorated billing
- Automated tax calculation (Stripe Tax / Avalara)

**Expectations:**
- Subscription lifecycle fully automated
- Revenue reports exportable to NetSuite format
- Failed payment retry with escalation workflow
- Multi-currency support for international clients
- Contract value tracking with renewal alerts

---

### 2.8 Compliance Team

| Attribute | Detail |
|-----------|--------|
| **Role** | Regulatory compliance, audit, and data governance |
| **Primary Users** | Legal counsel, DPO, compliance officers |

**Responsibilities:**
- Ensure AI hiring compliance (NYC LL144, EEOC, GDPR)
- Conduct periodic bias audits on AI screening models
- Manage data retention and deletion policies
- Review and approve privacy policies and consent flows
- Respond to data subject access requests (DSARs)
- Maintain audit trails for regulatory inspections

**Pain Points:**
- No audit trail for AI screening decisions
- Manual DSAR fulfillment takes 15+ business days
- Cannot demonstrate bias testing for AI models
- Data scattered across systems with unclear retention
- Consent management not tracked per candidate
- Adverse impact analysis requires manual statistics

**Goals:**
- Immutable audit log for every system action
- Automated DSAR processing within 72 hours
- Built-in bias audit reports with demographic breakdowns
- Configurable data retention with auto-deletion
- Consent tracking with version history

**Expectations:**
- One-click adverse impact report generation
- AI explainability for every screening decision
- GDPR-compliant data export in machine-readable format
- Role-based data masking for PII protection
- Annual compliance certification support package

---

## 3. Stakeholder Power-Interest Grid

```
HIGH INTEREST
     │
     │  MANAGE CLOSELY          KEEP SATISFIED
     │  ┌─────────────────┐    ┌─────────────────┐
     │  │ Company Admin   │    │ Super Admin     │
     │  │ Recruiter       │    │ Compliance Team │
     │  │ HR Manager      │    │                 │
     │  │ Candidate       │    │                 │
     │  └─────────────────┘    └─────────────────┘
     │
     │  KEEP INFORMED           MONITOR
     │  ┌─────────────────┐    ┌─────────────────┐
     │  │ Interview Panel │    │ Finance Team    │
     │  │                 │    │                 │
     │  └─────────────────┘    └─────────────────┘
     │
LOW ─┼──────────────────────────────────────────── HIGH
INTEREST                                          INFLUENCE
```

---

## 4. Communication Plan

| Stakeholder | Channel | Frequency | Content |
|-------------|---------|-----------|---------|
| Super Admin | Steering committee | Weekly | Platform metrics, risks |
| Company Admin | Workshop + email | Bi-weekly | Feature updates, training |
| Recruiter | Slack + demo | Daily/Sprint | New features, tips |
| HR Manager | Dashboard + report | Weekly | KPI summary, approvals |
| Interview Panel | Email + training | Per sprint | Scorecard updates |
| Candidate | In-app + email | Event-driven | Status, scheduling |
| Finance Team | Report + meeting | Monthly | Revenue, billing |
| Compliance Team | Review + audit | Quarterly | Compliance status |

---

## 5. Stakeholder Requirements Summary

| Stakeholder | Top 3 Requirements |
|-------------|-------------------|
| Super Admin | Tenant management, platform analytics, feature flags |
| Company Admin | User provisioning, SSO, policy configuration |
| Recruiter | AI screening, scheduling, pipeline management |
| HR Manager | Approvals, dashboards, compliance reports |
| Interview Panel | Scorecards, candidate briefs, calendar sync |
| Candidate | Easy apply, status tracking, self-scheduling |
| Finance Team | Automated billing, MRR tracking, ERP integration |
| Compliance Team | Audit logs, bias reports, DSAR automation |

---

*Document Classification: Internal — Stakeholder Management*
