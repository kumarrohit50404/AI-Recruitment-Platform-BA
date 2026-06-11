# Interview Questions — HireFlow AI Portfolio
## If I Were the Interviewer (Normal → Deep)

| Field | Value |
|-------|-------|
| **Purpose** | Prepare for recruiter, hiring manager, and BA panel questions |
| **Project** | HireFlow AI — Junior / Associate BA Portfolio Case Study |
| **Portfolio** | [github.com/kumarrohit50404/AI-Recruitment-Platform-BA](https://github.com/kumarrohit50404/AI-Recruitment-Platform-BA) |

**How to use:** Pick 2–3 questions per section and practice aloud. Always open with: *"This is a portfolio case study — I documented it as a BA, I did not build production software."*

**Legend:** 🟢 Normal · 🟡 Intermediate · 🔴 Deep

---

## 1. Opening & Project Understanding

| Level | Question | What a strong answer includes |
|-------|----------|--------------------------------|
| 🟢 | Tell me about yourself and this project. | 60-second intro → HireFlow AI → business problem → your BA role → GitHub link |
| 🟢 | What is HireFlow AI? | AI-assisted recruitment platform concept; reduces manual screening; improves pipeline visibility |
| 🟢 | Is this a real product or a case study? | **Portfolio case study** — requirements, process, wireframes, reporting specs documented end-to-end |
| 🟢 | Why did you choose a recruitment domain? | Hiring is relatable; clear stakeholders; measurable KPIs (time-to-hire, funnel, offer acceptance) |
| 🟡 | What was your exact role? | BA: elicitation, BRD, user stories, process flows, RTM, wireframes, KPI/reporting requirements |
| 🟡 | What did you **not** do on this project? | Did not build APIs, database, production UI, or Power BI engineering — defined requirements only |
| 🔴 | If this went to production, what would change in your deliverables? | Same BRD/stories base; add FRD handoff, sprint refinement, live UAT, change control, production data governance |

---

## 2. Business Case & Problem Definition

| Level | Question | What a strong answer includes |
|-------|----------|--------------------------------|
| 🟢 | What business problem were you solving? | Manual screening (23 hrs/week), slow scheduling, no pipeline visibility, inconsistent evaluation |
| 🟢 | Who feels this pain the most? | Recruiters (volume), HR Manager (visibility), CHRO (time-to-hire), Compliance (AI explainability) |
| 🟡 | What does success look like? | BR-012: time-to-hire 42 → 23 days; BR-002: 80% screening time reduction; better funnel visibility |
| 🟡 | Why invest in this vs. keep manual process? | Cost of recruiter time, mis-hires, slow fills, compliance risk — business case in `01_Business_Context/` |
| 🔴 | Walk me through your business case structure. | Current state → pain/cost → options → recommended solution → benefits → risks — **summarize, don't recite ROI/NPV** |
| 🔴 | What assumptions did you make? | Mid-market org, multi-channel applicants, AI screening with human override, 12-month reporting window |

**Trap question:** *"What was the ROI?"*  
**Safe answer:** "The business case outlines expected benefits and costs; my focus was defining requirements that address the pain points behind those benefits."

---

## 3. Stakeholder Analysis

| Level | Question | What a strong answer includes |
|-------|----------|--------------------------------|
| 🟢 | How many stakeholders did you identify? | Eight groups: Recruiter, HR Manager, CHRO, Hiring Manager, Compliance, IT, Finance, Candidate |
| 🟢 | How did you capture stakeholder needs? | Interviews/workshop-style notes (portfolio simulation) → Stakeholder Matrix |
| 🟡 | Give one stakeholder conflict you handled. | Recruiter wants speed vs. Compliance wants explainable AI → BR-017 rationale + BR-010 audit logs |
| 🟡 | What is a power-interest grid and did you use it? | Maps who to manage closely vs. keep informed; referenced in stakeholder analysis |
| 🔴 | CHRO cares about X, Recruiter cares about Y — how do requirements reflect both? | CHRO → BR-012, executive dashboard; Recruiter → BR-002/003, ranked candidate list wireframe |
| 🔴 | Which stakeholder would you revisit first in Phase 2? | Compliance + Candidate — bias reporting, DSAR, candidate experience not fully in 6-screen prototype |

---

## 4. Requirements (BRD)

| Level | Question | What a strong answer includes |
|-------|----------|--------------------------------|
| 🟢 | What is a BRD and what did yours contain? | Business needs, rules, reporting needs, MoSCoW priority, traceable IDs — `03_Business_Requirements/BRD.md` |
| 🟢 | What is MoSCoW? | Must / Should / Could / Won't — prioritization under scope constraints |
| 🟢 | Give 3 example requirements from your BRD. | BR-002 screening reduction, BR-017 explainable AI score, BR-031 executive reporting |
| 🟡 | Difference between business and functional requirements? | BR = what business needs; FR = how system behaves — portfolio leads with BRD for BA interview |
| 🟡 | How do you write a good requirement? | Clear, testable, one need per ID, sourced to stakeholder, prioritized |
| 🟡 | What requirement addresses compliance? | BR-005 NYC LL144, BR-006 GDPR, BR-007 EEOC, BR-010 audit logs |
| 🔴 | Requirement BR-002 says 80% screening reduction — how would you validate it? | UAT scenario: compare time to shortlist N candidates AS-IS vs. TO-BE; trace via RTM |
| 🔴 | What did you put in Won't Have scope? | Reference BRD Won't items if asked — keeps MVP realistic (check your BRD section) |
| 🔴 | How do you prevent scope creep? | Change log, MoSCoW, traceability, explicit Phase 2 backlog |

---

## 5. Process Modeling (AS-IS / TO-BE)

| Level | Question | What a strong answer includes |
|-------|----------|--------------------------------|
| 🟢 | What was wrong with the AS-IS hiring process? | Email resume flood, manual screening, calendar ping-pong, subjective evaluation |
| 🟢 | What improved in TO-BE? | AI-ranked shortlist, structured scorecards, dashboard reporting, approval workflow |
| 🟡 | Where did you place human review in TO-BE? | Recruiter reviews AI-ranked list; can override score with justification (BUS-003) |
| 🟡 | Draw the hiring funnel in words. | Applied → Screened → Interview → Offer → Hired — matches dashboard |
| 🔴 | Biggest bottleneck in the funnel from your data? | Applied 952 → Screened 729 → Interview 102 — largest drop after screening |
| 🔴 | What process change would you recommend first? | AI-assisted screening + explainable scores — highest recruiter time savings |

---

## 6. User Stories & Acceptance Criteria

| Level | Question | What a strong answer includes |
|-------|----------|--------------------------------|
| 🟢 | What format are your user stories? | As a [role], I want [capability], so that [benefit] |
| 🟢 | Read one user story aloud. | Pick US-AIS-001 or similar from `05_User_Stories_and_Acceptance/User_Stories.md` |
| 🟢 | What are acceptance criteria? | Testable conditions — Gherkin Given/When/Then in `Acceptance_Criteria.md` |
| 🟡 | Difference between user story and use case? | Story = agile backlog item; use case = detailed interaction flow — portfolio uses stories |
| 🟡 | How do you split epics into stories? | By persona + workflow step: screening, scheduling, reporting, requisition |
| 🔴 | Write acceptance criteria for "recruiter overrides AI score." | Given score shown, When recruiter overrides with reason, Then audit log captures override |
| 🔴 | What makes acceptance criteria bad? | Vague ("works well"), untestable, mixed multiple behaviors, no edge cases |

---

## 7. Traceability & UAT (RTM)

| Level | Question | What a strong answer includes |
|-------|----------|--------------------------------|
| 🟢 | What is an RTM? | Requirements Traceability Matrix — links need → requirement → story → test/UAT |
| 🟢 | Why does traceability matter? | Proves coverage; supports UAT; reduces gaps and gold-plating |
| 🟡 | Show one traceability chain. | Compliance pain → BR-017 → US-AIS-004 → UAT scenario (open `06_Traceability_and_Validation/RTM.md`) |
| 🟡 | How do you know all Must requirements are covered? | RTM coverage + MoSCoW Must items mapped to stories |
| 🔴 | A requirement has no test case — what do you do? | Flag gap, add UAT scenario or AC, update RTM before sign-off |
| 🔴 | How would you run UAT for this project? | Business users (recruiter, HR) execute plain-language scenarios; pass/fail against AC |

---

## 8. UX / Wireframes / Prototype

| Level | Question | What a strong answer includes |
|-------|----------|--------------------------------|
| 🟢 | Did you design the UI or specify it? | **Specified** wireframes and Figma build plan from requirements — not production design |
| 🟢 | Walk me through your 6 screens. | Login → Recruiter Dashboard → Candidates → Candidate Details → Job Requisition → Reports |
| 🟡 | Which screen best shows your BA value? | Candidate List — AI ranking (BR-002/003) or Candidate Details — explainable AI (BR-017) |
| 🟡 | What happens when user clicks Submit on Job Requisition? | Goes to HR approval (BUS-001) — not published immediately |
| 🟡 | Why SSO on login screen? | BR-009 enterprise authentication requirement |
| 🔴 | Recruiter says dashboard is cluttered — what do you do? | Return to stakeholder need; prioritize KPIs from reporting requirements; iterate wireframe |
| 🔴 | Accessibility — did you consider it? | Mention WCAG if in BRD NFRs; font contrast, keyboard nav as BA consideration in wireframes |

---

## 9. Reporting, KPIs & Dashboard

| Level | Question | What a strong answer includes |
|-------|----------|--------------------------------|
| 🟢 | What is the executive dashboard for? | CHRO/HR leadership — "Are we hiring efficiently and moving candidates through the funnel?" |
| 🟢 | Name 3 KPIs on your dashboard. | Time to Hire (23.9 days), Offer Acceptance (80%), Total Candidates (952) |
| 🟢 | What is Time to Hire and how is it calculated? | Applied date → hire date average — `08_Data_and_Reporting/KPI_Definitions.md` |
| 🟡 | Why is offer acceptance 80% vs 78% target? | Above target — offers are competitive; leadership monitoring metric |
| 🟡 | Explain the hiring funnel numbers. | 952 Applied → 729 Screened → 102 Interview → 52 Offer → 38 Hired |
| 🟡 | Why do Total Candidates (952) differ from unique candidates (350)? | 952 = application records; one candidate can apply to multiple jobs |
| 🟡 | What is conversion rate? | 38 hires ÷ 952 applications = **4.0%** |
| 🔴 | Recruiter Performance table — what action would you recommend? | Compare hires and time-to-hire; investigate low converters; balance workload |
| 🔴 | Department Hiring Trend — what business question does it answer? | Which teams are hiring, when, and whether capacity matches plan |
| 🔴 | How did you validate KPI logic without building Power BI? | Sample SQL in `Business_SQL_Examples.md`; conceptual data model |

**Trap question:** *"Did you build the Power BI dashboard?"*  
**Safe answer:** "I defined KPI and dashboard requirements and created a mockup aligned to sample data. I did not deliver production BI engineering."

---

## 10. Data, SQL & API (BA Level)

| Level | Question | What a strong answer includes |
|-------|----------|--------------------------------|
| 🟢 | Why does a BA need SQL? | Validate reporting requirements and KPI formulas against sample data |
| 🟡 | Give an example SQL use case from your project. | Offer acceptance rate query — `Business_SQL_Examples.md` Example 5 |
| 🟡 | What entities are in your data model? | Candidates, applications, jobs, interviews, offers, recruiters — `Data_Model.md` |
| 🟡 | What is API Analysis in your portfolio? | Summary of integration domains — how modules exchange data (not building APIs) |
| 🔴 | How would applications table link to jobs? | applications.job_id → jobs.job_id (many applications per job) |
| 🔴 | Duplicate candidate profiles — which requirement? | BR-038 deduplication |

---

## 11. Behavioral & Situational (STAR Format)

| Level | Question | What a strong answer includes |
|-------|----------|--------------------------------|
| 🟢 | Tell me about a time you worked with conflicting feedback. | Recruiter vs. Compliance → documented as requirements + business rules |
| 🟡 | Tell me about a time you had unclear requirements. | Ask clarifying questions; prototype/wireframe; confirm with stakeholder sign-off |
| 🟡 | How do you handle tight deadlines? | MoSCoW Must first; Phase 2 for Should/Could; RTM proves coverage |
| 🟡 | Tell me about a mistake you made in this project. | Honest example: early scope too wide → fixed with prioritization and single executive dashboard |
| 🔴 | Hiring manager wants a feature not in BRD — what do you do? | Impact analysis → change request → prioritize → update BRD/RTM |
| 🔴 | Developer says a story is impossible — what do you do? | Clarify AC, split story, discuss MVP alternative, document decision |

---

## 12. Deep / Panel / "Stress" Questions

| Level | Question | What a strong answer includes |
|-------|----------|--------------------------------|
| 🔴 | Defend why AI screening is ethical in your design. | Explainable scores (BR-017), human override, audit trail (BR-010), compliance reqs |
| 🔴 | Your funnel shows huge drop after screening — is AI failing? | Not necessarily — screening filters unqualified; investigate conversion Screened → Interview |
| 🔴 | Maria Lopez has 13 hires, James has 2 — what do you tell HR? | Data-driven coaching; check pipeline quality, req assignment, not blame without context |
| 🔴 | If time-to-hire is 23.9 days but target is 23, are we failing? | Marginal gap — monitor trend; segment by department/recruiter; check interview/offer stages |
| 🔴 | How is this different from Greenhouse or Lever? | Concept portfolio focused on **requirements process**, not commercial feature parity |
| 🔴 | Sell this project in 30 seconds to a CHRO. | Faster screening, visible funnel, measurable KPIs, compliant AI-assisted decisions |
| 🔴 | What would you do in Week 1 if you joined as Junior BA on the real build? | Read BRD, meet recruiters/HR, confirm open questions, refine top stories, validate reporting |

---

## 13. Questions **You** Should Ask the Interviewer

| Question | Why ask |
|----------|---------|
| How does your BA team work with product and engineering? | Shows collaboration mindset |
| What does a typical requirement document look like here? | Fit check |
| How are UAT and sign-off handled? | Traceability culture |
| What tools do you use — Jira, Confluence, Figma? | Practical alignment |
| What would success look like in the first 90 days for this role? | Closes on outcomes |

---

## 14. Quick Cheat Sheet — Numbers to Know

| Item | Value |
|------|-------|
| Stakeholder groups | 8 |
| Prototype screens | 6 |
| Dashboard KPI cards | 6 |
| Dashboard visuals | 9 total (6 cards + funnel + trend + table) |
| Applications (12 mo) | 952 |
| Screened | 729 |
| Interviews completed | 102 |
| Offers released | 52 |
| Hires | 38 |
| Time to Hire | 23.9 days |
| Offer acceptance | 80.0% (target 78%) |
| Funnel conversion | 4.0% |
| Unique candidates | 350 |
| Jobs | 24 |
| Recruiters | 6 |

---

## 15. What NOT to Say (Common Failures)

| Don't say | Say instead |
|-----------|-------------|
| "I built the platform" | "I documented requirements for the platform concept" |
| "I calculated 340% ROI" | "The business case outlines expected benefits" |
| "I wrote 150 SQL queries" | "I used sample SQL to validate reporting logic" |
| "I developed Power BI with DAX" | "I defined dashboard and KPI requirements" |
| "I led the entire program" | "This was my BA portfolio case study" |
| "842 applications" | "**952** — aligned to executive dashboard data" |

---

## 16. 30-Minute Mock Interview Flow (Practice Alone)

| Min | Interviewer asks | You open |
|-----|------------------|----------|
| 0–3 | Tell me about this project | Elevator pitch + GitHub |
| 3–8 | Stakeholders & business problem | Business Case + Stakeholder Matrix |
| 8–15 | Requirements & stories | BR-002, BR-017 + one user story + AC |
| 15–20 | Process & prototype | AS-IS/TO-BE + Candidate Details screen |
| 20–25 | Dashboard & KPIs | Executive dashboard PNG + funnel explanation |
| 25–28 | Traceability | One RTM row end-to-end |
| 28–30 | Your questions to us | Ask 2 from Section 13 |

---

**File:** `09_Interview_Portfolio/Interview_Questions.md`  
**Practice with:** [Interview_Walkthrough.md](Interview_Walkthrough.md) · [Resume_Project_Section.md](Resume_Project_Section.md)
