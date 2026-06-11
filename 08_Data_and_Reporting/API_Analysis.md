# API Analysis — Integration Summary
## HireFlow AI | Portfolio Case Study

**Author:** Rohit Kumar | Business Analyst

**Purpose:** Document integration needs from a Business Analyst perspective — what systems connect, what data flows, and who consumes it. This is not an API development specification.

---

## 1. Integration Domains

| Domain | Business need | Stakeholders | Requirements |
|--------|---------------|--------------|--------------|
| Authentication | Secure login and role-based access | HR Manager, Recruiter | BR-009 |
| Candidate | Apply, upload resume, track status | Candidate, Recruiter | BR-021 |
| Screening | AI score and ranking | Recruiter | BR-002, BR-003 |
| Interview | Schedule, scorecard | Recruiter, Panel | Scheduling & evaluation stories |
| Reporting | Dashboard and exports | HR Manager | BR-031, reporting requirements |
| Audit | Action logging for compliance review | Compliance | BR-010 |

---

## 2. External Dependencies

| System | Why it matters |
|--------|----------------|
| Calendar systems | Panel availability for interview scheduling (BR-023) |
| HRIS (e.g., Workday) | Headcount validation for requisition approval (Phase 2) |
| Email / notifications | Interview reminders, offer letters |

---

## 3. Data Flow (BA View)

```
Candidate applies → Resume stored → AI screening score
                         ↓
Recruiter reviews ranked list → Schedules interview → Panel scorecard
                         ↓
Offer sent → Hire recorded → Metrics appear on executive dashboard
```

---

## 4. BA Deliverable vs. Engineering Deliverable

| Business Analyst defines | Engineering team builds |
|--------------------------|-------------------------|
| Which integrations are required | REST endpoints and schemas |
| What data must sync | Authentication and error handling |
| Who consumes each data flow | Performance and deployment |

---

*Integration summary supporting workflow and reporting requirements in the BRD.*
