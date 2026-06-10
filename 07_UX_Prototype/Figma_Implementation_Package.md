# Figma Build Plan — 6-Screen BA Portfolio Prototype
## HireFlow AI | Direct Implementation Guide

| Field | Value |
|-------|-------|
| **Document ID** | FIG-HFA-2026-002 |
| **Version** | 2.0 |
| **Author** | Rohit, Business Analyst & UX Consultant |
| **Purpose** | Build-only spec — open Figma and construct frame-by-frame |
| **Prototype scope** | **6 screens only** (no registration, AI interview, settings, HR approval queue) |
| **Frame size** | 1440 × 1024 px (desktop) |
| **Build time** | 2–3 days |

---

## 0. Before You Open Figma

### 0.1 What this prototype proves in interviews

| Story | Screens |
|-------|---------|
| Recruiters need faster screening | Candidate List → Candidate Details |
| Hiring starts with a requisition | Job Requisition |
| HR needs pipeline visibility | Recruiter Dashboard → Reports Dashboard |
| Requirements became UI | Traceability column on every screen below |

### 0.2 Figma file setup

| Step | Action |
|------|--------|
| 1 | Create file: `HireFlow_AI_BA_Prototype.fig` |
| 2 | Create pages: `00 Tokens` → `01 Components` → `02 Screens` → `03 Prototype` |
| 3 | On `02 Screens`, add 6 frames named exactly as in §1 |
| 4 | Link prototype on `03 Prototype` tab (see §3) |
| 5 | Add sticky note on each frame: requirement IDs from §10 |

### 0.3 Design tokens (create on `00 Tokens`)

| Token | Hex | Usage |
|-------|-----|-------|
| Primary | `#2563EB` | CTAs, active nav, links |
| Text | `#0F172A` | Headings, table text |
| Text muted | `#64748B` | Labels, secondary |
| Background | `#F8FAFC` | Page canvas |
| Surface | `#FFFFFF` | Cards, sidebar, inputs |
| Border | `#E2E8F0` | Dividers, input borders |
| Success | `#16A34A` | Score ≥80, pass |
| Warning | `#D97706` | Aging badge, score 40–79 |
| Error | `#DC2626` | Validation, score <40 |
| Font | Inter 14px body / 24px H1 / 16px H2 | All text |
| Radius | 8px cards, 6px inputs | — |
| Spacing | 8px grid (8, 16, 24, 32) | Padding |

---

## 1. Exact Screens to Build

| Priority | Frame name | Screen ID | Route | Role |
|----------|------------|-----------|-------|------|
| **P1** | `01 — Login` | SCR-AUTH-001 | `/login` | Recruiter (entry) |
| **P2** | `02 — Recruiter Dashboard` | SCR-DASH-001 | `/dashboard` | Recruiter |
| **P3** | `03 — Candidate List` | SCR-CAND-001 | `/jobs/REQ-2026-0142/candidates` | Recruiter |
| **P4** | `04 — Candidate Details` | SCR-CAND-002 | `/candidates/CAN-1042` | Recruiter |
| **P5** | `05 — Job Requisition` | SCR-JOB-001 | `/jobs/new` | Recruiter |
| **P6** | `06 — Reports Dashboard` | SCR-RPT-001 | `/reports` | HR Manager / Recruiter |

**Do not build:** Registration, AI Interview, Settings, Subscription, HR Approval Queue, MFA, mobile breakpoints, empty/loading states (annotate with sticky notes only).

---

## 2. Screen Priority & Build Order

| Day | Build | Why this order |
|-----|-------|----------------|
| **Day 1 AM** | Tokens + Components (§5) | Reuse across all 6 screens |
| **Day 1 PM** | P1 Login, P2 Dashboard | Establishes shell (sidebar + top bar) |
| **Day 2 AM** | P3 Candidate List, P4 Candidate Details | Hero AI screening story |
| **Day 2 PM** | P5 Job Requisition | Form components |
| **Day 3 AM** | P6 Reports Dashboard | Reuse KPI cards + charts |
| **Day 3 PM** | Prototype links (§3) + sample data pass (§8) | Interview-ready |

---

## 3. Navigation Flow

### 3.1 Prototype links (Figma Prototype tab)

```
[01 Login]
    └── Sign In (button) ──→ [02 Recruiter Dashboard]

[02 Recruiter Dashboard]
    ├── Sidebar: Candidates ──→ [03 Candidate List]
    ├── Sidebar: Reports ──→ [06 Reports Dashboard]
    ├── Top bar: + New Requisition ──→ [05 Job Requisition]
    ├── Funnel: "Screened" segment ──→ [03 Candidate List]
    └── Table row: "Sr. Developer" ──→ [03 Candidate List]

[03 Candidate List]
    └── Row click: "Alex Chen" ──→ [04 Candidate Details]

[04 Candidate Details]
    └── ← Back to Candidates ──→ [03 Candidate List]

[05 Job Requisition]
    └── Submit for Approval (toast annotation) ──→ [02 Recruiter Dashboard]

[06 Reports Dashboard]
    └── Sidebar: Dashboard ──→ [02 Recruiter Dashboard]
```

### 3.2 Information architecture (sidebar — screens 2–6)

| # | Label | Icon (Lucide/Figma) | Destination | Active on |
|---|-------|---------------------|-------------|-----------|
| 1 | Dashboard | Home | P2 | Dashboard |
| 2 | Jobs | Briefcase | P5 (New Req) | Job Requisition |
| 3 | Candidates | Users | P3 | Candidate List, Details |
| 4 | Reports | BarChart2 | P6 | Reports |
| — | *Interviews* | Calendar | *Disabled gray — annotate "Phase 2"* | — |

### 3.3 Top bar (screens 2–6)

| Element | Position | Content | Prototype link |
|---------|----------|---------|----------------|
| Logo | Left | HireFlow AI wordmark | → P2 |
| Search | Center | Placeholder: "Search candidates, jobs…" | None (annotate) |
| Notifications | Right | Bell icon + badge `3` | Annotate only |
| Avatar | Right | `SC` circle + "Sarah Chen" + chevron | Annotate: Recruiter role |
| Primary CTA | Right | `+ New Requisition` button | → P5 |

---

## 4. User Journey (Interview Demo — 5 minutes)

| Step | Screen | What to say | Requirement proof |
|------|--------|-------------|-------------------|
| 1 | Login | "Recruiter authenticates to access hiring workflows." | FR-AUTH-003, US-AUTH-003 |
| 2 | Dashboard | "Pain point: no pipeline visibility. Dashboard shows open reqs, funnel, aging." | BR-031, BR-033, US-JOB-010 |
| 3 | Job Requisition | "Hiring starts with a documented requisition — HR must approve before publish." | BR-019, BUS-001, US-JOB-001 |
| 4 | Candidate List | "AI ranks candidates so recruiters focus on top matches first." | BR-002, BR-003, US-AIS-001 |
| 5 | Candidate Details | "Compliance needs explainable scores; recruiters can override with justification." | BR-017, BUS-003, US-AIS-004, US-AIS-007 |
| 6 | Reports | "HR tracks time-to-hire and funnel conversion from reporting requirements." | BR-031, RR-001, RR-002, US-RPT-001 |

**Process alignment (TO-BE):** Requisition → Publish → Apply → AI Screen → Recruiter Review → Report. Screens 5 → 2 → 3 → 4 → 6 tell this story.

---

## 5. Component Library (build on `01 Components` first)

Create as Figma **Components** with variants where noted.

### 5.1 Buttons

| Component | Variants | Size (W×H) | Style |
|-----------|----------|------------|-------|
| `Button/Primary` | Default, Hover, Disabled | auto × 40px | Fill `#2563EB`, white text, radius 6px |
| `Button/Secondary` | Default | auto × 40px | White fill, `#2563EB` border |
| `Button/Ghost` | Default | auto × 36px | No fill, text `#2563EB` |
| `Button/Danger` | Default | auto × 40px | Fill `#DC2626` — Reject actions |

### 5.2 Form inputs

| Component | States | Spec |
|-----------|--------|------|
| `Input/Text` | Default, Focus, Error, Disabled | Label 12px muted; field 40px height; error text 12px red below |
| `Input/Password` | + Show/Hide icon | Same as text |
| `Input/Textarea` | Default, Error | Min 96px height |
| `Input/Select` | Default | Chevron right; 40px height |
| `Input/Checkbox` | Checked, Unchecked | 16px box + label |
| `Input/Tag` | Skill tag chip | Blue-50 background, blue text, × remove |

### 5.3 Shell

| Component | Size | Contents |
|-----------|------|----------|
| `Shell/Sidebar` | 240 × full | Logo area, 4 nav items, active state left border 3px primary |
| `Shell/TopBar` | full × 64px | White surface, bottom border, slots for search + actions |
| `Shell/PageHeader` | full × auto | H1 + breadcrumb + right actions |

### 5.4 Data display

| Component | Spec |
|-----------|------|
| `Card/KPI` | 220 × 100px — label 12px, value 28px bold, optional trend arrow |
| `Card/Surface` | White, 8px radius, 1px border, 24px padding |
| `Badge/Score` | Pill 32×24 — Green `#DCFCE7`/`#16A34A`, Amber, Red variants |
| `Badge/Stage` | Pill — Screened, Applied, Rejected, Interview |
| `Badge/Aging` | Amber `31d ⚠` when >30 days |
| `Chart/Funnel` | Horizontal bars — 5 stages, proportional widths |
| `Chart/Bar` | Placeholder rectangles — Reports screen |
| `Table/Header` | 40px row, muted bg, 12px semibold |
| `Table/Row` | 48px row, hover `#F1F5F9` |
| `Tab/Item` | Active underline 2px primary |

### 5.5 Overlays (not separate screens)

| Component | Use on |
|-----------|--------|
| `Modal/Override Score` | P4 — 480px wide, textarea + Save/Cancel |
| `Toast/Success` | P5 — "Requisition submitted for HR approval" |

---

## 6. Tables Specification

### 6.1 Dashboard — My Requisitions table (P2)

| Column | Width | Align | Sample | Sortable |
|--------|-------|-------|--------|----------|
| Title | 200px | Left | Sr. Software Developer | Yes |
| Applications | 80px | Center | 42 | Yes |
| In Pipeline | 90px | Center | 12 | Yes |
| Status | 90px | Center | Open (green pill) | Yes |
| Aging | 70px | Center | 12d / 31d ⚠ | Yes |
| Actions | 48px | Center | ⋮ menu icon | No |

**Rows:** 3 visible (Sr. Developer, Product Manager, Data Analyst). Third row optional.

**Row action menu (annotate):** View Candidates → P3 | Edit Requisition | Close Req

### 6.2 Candidate List table (P3)

| Column | Width | Align | Sample | Notes |
|--------|-------|-------|--------|-------|
| ☐ | 40px | Center | Checkbox | Bulk select header |
| Rank | 56px | Center | 1 ▲, 2, 3… | Movement indicator |
| Name | 160px | Left | Alex Chen (link style) | Click → P4 |
| AI Score | 90px | Center | 92 🟢 | `Badge/Score` |
| Stage | 110px | Center | Screened | `Badge/Stage` |
| Skills Match | 120px | Center | 8/10 skills | Tooltip annotate |
| Updated | 90px | Right | 2h ago | Relative time |

**Toolbar above table:** Search input 320px | Stage ▾ | Score ▾ | Clear filters | Export ▾

**Bulk bar (show 1 row selected state as variant):** `Bulk Actions ▾: Advance | Reject | Email`

**Pagination:** "Showing 1–5 of 42" | `< 1 2 >` | `25/page ▾`

---

## 7. Forms Specification

### 7.1 Login form (P1)

| Field | Type | Required | Placeholder | Notes |
|-------|------|----------|-------------|-------|
| Email | Text | Yes | `you@company.com` | Full width |
| Password | Password | Yes | `Enter password` | Show/hide toggle |
| Remember me | Checkbox | No | — | Left |
| Forgot password? | Link | — | — | Right of checkbox row |

**CTAs:** `Sign In` (primary, full width) | Divider "or continue with" | `Google` + `Microsoft` (secondary, side by side)

**Build 2 frame variants:** `Default` and `Error` (see §9.1)

### 7.2 Job Requisition form (P5)

**Layout:** Single column max-width 800px centered OR two-column 60/40. Recommended: **two-column**.

**Left column — Job Details**

| Field | Type | Required | Placeholder / Default |
|-------|------|----------|---------------------|
| Job Title | Text | Yes | e.g. Senior Software Developer |
| Department | Select | Yes | Engineering ▾ |
| Employment Type | Select | Yes | Full-time ▾ |
| Location | Select | Yes | Remote / Hybrid / On-site |
| Salary Band Min | Number | Yes | 120000 |
| Salary Band Max | Number | Yes | 160000 |
| Hiring Manager | Select | Yes | James Okonkwo ▾ |
| Job Description | Textarea | Yes | 6 rows rich-text placeholder |

**Right column — Requirements & Rules**

| Field | Type | Required | Notes |
|-------|------|----------|-------|
| Required Skills | Tag input | Yes | Pre-filled: Python, React, AWS |
| Minimum Experience (years) | Number | Yes | Default: 5 |
| Education Level | Select | No | Bachelor's ▾ |
| Knockout: Min years experience | Checkbox | No | Checked — BUS-003 related |
| Knockout: Required skill match | Checkbox | No | Checked |
| AI Screening Enabled | Toggle | Yes | On (default) |

**Footer actions:** `Save Draft` (ghost, left) | `Submit for Approval` (primary, right)

**Build 2 variants:** `Default` | `Validation Error` (see §9.2)

---

## 8. Validation Messages

Use exact copy — put in red 12px below field or in error banner.

### 8.1 Login (P1 — Error variant)

| Trigger | Message | Placement |
|---------|---------|-----------|
| Empty email | `Email is required.` | Below email field |
| Invalid email format | `Enter a valid email address.` | Below email field |
| Empty password | `Password is required.` | Below password field |
| Invalid credentials | `Email or password is incorrect. Please try again.` | Banner top of form |
| Account locked (annotate) | `Account locked after 5 failed attempts. Try again in 30 minutes.` | Banner — FR-AUTH-009 |

### 8.2 Job Requisition (P5 — Error variant)

| Field | Message |
|-------|---------|
| Job Title empty | `Job title is required.` |
| Department empty | `Select a department.` |
| Salary Min > Max | `Minimum salary cannot exceed maximum.` |
| Salary empty | `Enter a salary range.` |
| Job Description empty | `Job description is required.` |
| Required Skills empty | `Add at least one required skill.` |
| Min Experience empty | `Enter minimum years of experience.` |
| Submit without HR fields | `Complete all required fields before submitting.` |

### 8.3 Candidate Details — Override modal (overlay on P4)

| Field | Message |
|-------|---------|
| Justification empty | `A justification is required to override the AI score.` |
| Justification < 20 chars | `Please provide at least 20 characters explaining your override.` |

**Modal title:** `Override AI Score`  
**Helper text:** `BUS-003: Overrides below score 40 require documented justification for audit.`  
**Fields:** Current score (read-only) | New score (select 0–100) | Justification (textarea)

---

## 9. Sample Data (use consistently across all screens)

### 9.1 Tenant & user

| Attribute | Value |
|-----------|-------|
| Company | Acme Corporation |
| Logged-in user | Sarah Chen, Recruiter |
| Avatar initials | SC |
| Email (login demo) | `sarah.chen@acme.com` |

### 9.2 Requisitions

| Req ID | Title | Apps | Pipeline | Status | Aging |
|--------|-------|------|----------|--------|-------|
| REQ-2026-0142 | Sr. Software Developer | 42 | 12 | Open | 12d |
| REQ-2026-0138 | Product Manager | 28 | 8 | Open | 31d ⚠ |
| REQ-2026-0145 | Data Analyst | 15 | 5 | Open | 8d |

**Active job for P3/P4:** REQ-2026-0142 — Sr. Software Developer

### 9.3 Dashboard KPIs (P2)

| Card | Value | Label | Trend |
|------|-------|-------|-------|
| 1 | 24 | Open Requisitions | +2 vs last month |
| 2 | 156 | Active Pipeline | — |
| 3 | 21 days | Avg. Time-to-Hire | ↓ 3 days |
| 4 | 86% | Offer Acceptance | ↑ 4% |

### 9.4 Pipeline funnel (P2 + P6)

| Stage | Count |
|-------|-------|
| Applied | 142 |
| Screened | 89 |
| Interview | 34 |
| Offer | 8 |
| Hired | 3 |

### 9.5 Candidates (P3 — show 5 rows)

| Rank | Name | Score | Stage | Skills | Updated |
|------|------|-------|-------|--------|---------|
| 1 ▲ | Alex Chen | 92 | Screened | 8/10 | 2h ago |
| 2 | Maria Santos | 87 | AI Interview | 7/10 | 5h ago |
| 3 | James Wilson | 74 | Applied | 6/10 | 1d ago |
| 4 | Priya Patel | 68 | Applied | 5/10 | 1d ago |
| 5 ▼ | David Kim | 45 | Rejected | 3/10 | 2d ago |

### 9.6 Candidate Details (P4 — Alex Chen)

| Field | Value |
|-------|-------|
| ID | CAN-1042 |
| Email | alex.chen@email.com |
| Phone | (555) 234-8901 |
| Applied | Mar 15, 2026 |
| Source | Career Portal |
| Stage | Screened |
| AI Score | 92 |

**AI Rationale (quote card):**  
*"Strong match on technical skills and 7 years experience. Python and React exceed job requirements. AWS certified. Gap: Kubernetes listed as required but not found in resume."*

**Skills match grid:**

| Match | Skill |
|-------|-------|
| ✅ | Python, React, AWS, SQL, Docker |
| ❌ | Kubernetes, GraphQL |

**Experience (parsed):**
- Senior Developer — TechCorp — 2020–Present (5 yrs)
- Developer — StartupXYZ — 2018–2020 (2 yrs)
- Education: MS Computer Science, State University

### 9.7 Reports (P6)

| KPI tile | Value |
|----------|-------|
| Applied | 842 |
| Hired | 38 |
| Conversion | 4.5% |

**Date range:** Jan 1, 2026 — Jun 8, 2026  
**Department filter:** All Departments

### 9.8 Recent activity feed (P2)

- John D. advanced to Interview — 10 min ago
- AI interview completed — Maria Santos — 1h ago
- Offer sent — Jane S. — 3h ago
- New application — Sr. Developer — 5h ago

---

## 10. Screen-by-Screen Build Guide

---

### SCREEN 1 — Login `01 — Login`

| Attribute | Value |
|-----------|-------|
| **Priority** | P1 |
| **Frame** | 1440 × 1024 |
| **Traceability** | BR-009, BR-011 · FR-AUTH-003, FR-AUTH-005, FR-AUTH-009, FR-AUTH-011 · US-AUTH-003, US-AUTH-006, US-AUTH-009 |

#### Layout structure

```
┌─────────────────────────────────────────────────────────────┐
│ 1440 × 1024 — full viewport                                  │
│ ┌──────────────────┬────────────────────────────────────────┐│
│ │ BRAND PANEL 40%  │ FORM PANEL 60%                         ││
│ │ #2563EB gradient │ white / centered form max 400px        ││
│ │ Logo             │ H1: Sign in to HireFlow AI             ││
│ │ Tagline          │ Subtitle: Acme Corporation              ││
│ │ Illustration     │ Form fields + CTAs                      ││
│ └──────────────────┴────────────────────────────────────────┘│
└─────────────────────────────────────────────────────────────┘
```

#### Widgets

| Zone | Widgets |
|------|---------|
| Brand panel | Acme logo placeholder, "Hire smarter with AI", abstract pipeline illustration |
| Form | Email, Password, Remember me, Forgot link, Sign In, SSO row, Register link (annotate "out of scope") |

#### Fields

See §7.1

#### Actions

| Control | Prototype |
|---------|-----------|
| Sign In | → P2 Dashboard |
| Google / Microsoft | Annotate: SSO — FR-AUTH-005 |
| Forgot password | Annotate only |
| Register | Annotate only |

#### Data displayed

- Static brand content only
- Pre-fill email optional: `sarah.chen@acme.com` in presenter notes, not on frame

#### Build checklist

- [ ] 40/60 split at 576px / 864px
- [ ] Error variant frame with banner + field errors
- [ ] Sign In hotspot linked to P2

---

### SCREEN 2 — Recruiter Dashboard `02 — Recruiter Dashboard`

| Attribute | Value |
|-----------|-------|
| **Priority** | P2 |
| **Traceability** | BR-031, BR-033, BR-037 · FR-RPT-001, FR-RPT-002 · US-JOB-010, US-RPT-009 · RR-001 · KPI-003, KPI-006, KPI-011 |

#### Layout structure

```
┌─────────────────────────────────────────────────────────────┐
│ TopBar 64px                                                  │
├──────────┬──────────────────────────────────────────────────┤
│ Sidebar  │ Main 1200px                                       │
│ 240px    │ Greeting row + [+ New Requisition]                │
│          │ KPI row — 4 cards                                  │
│          │ ┌─────────────────────┬──────────────────────┐    │
│          │ │ Funnel chart 60%    │ Activity feed 40%    │    │
│          │ └─────────────────────┴──────────────────────┘    │
│          │ Requisitions table full width                      │
└──────────┴──────────────────────────────────────────────────┘
```

#### Widgets

| Zone | Widgets |
|------|---------|
| Top bar | `Shell/TopBar` — search, bell(3), avatar Sarah Chen, + New Requisition |
| Sidebar | `Shell/Sidebar` — Dashboard **active** |
| Row 1 | "Good morning, Sarah" H1 |
| Row 2 | 4 × `Card/KPI` — §9.3 |
| Row 3 | `Chart/Funnel` + activity list (4 items from §9.8) |
| Row 4 | Requisitions table — §6.1 |

#### Fields

None (read-only dashboard)

#### Actions

| Control | Prototype / Annotate |
|---------|---------------------|
| + New Requisition | → P5 |
| Sidebar: Candidates | → P3 |
| Sidebar: Reports | → P6 |
| Funnel segment click | → P3 (annotate: filtered by stage) |
| Table row Sr. Developer | → P3 |
| KPI card Time-to-Hire | → P6 (annotate) |
| ⋮ menu | Annotate only |

#### Data displayed

§9.2, §9.3, §9.4, §9.8

#### Build checklist

- [ ] Sidebar active = Dashboard
- [ ] Product Manager row shows amber aging badge 31d ⚠
- [ ] Funnel bar widths proportional to counts

---

### SCREEN 3 — Candidate List `03 — Candidate List`

| Attribute | Value |
|-----------|-------|
| **Priority** | P3 — **Hero screen for interviews** |
| **Traceability** | BR-002, BR-003, BR-037 · FR-AIS-002, FR-AIS-010 · US-AIS-001, US-AIS-005, US-AIS-006 · BUS-003 |

#### Layout structure

```
┌─────────────────────────────────────────────────────────────┐
│ TopBar + Sidebar (Candidates ACTIVE)                         │
├─────────────────────────────────────────────────────────────┤
│ Breadcrumb: Dashboard → Jobs → Sr. Software Developer        │
│ Page title: Candidates — Sr. Software Developer (REQ-0142)   │
│ Filter toolbar                                               │
│ Bulk actions bar (optional variant)                          │
│ Data table §6.2                                              │
│ Pagination                                                   │
└─────────────────────────────────────────────────────────────┘
```

#### Widgets

| Zone | Widgets |
|------|---------|
| Header | Breadcrumb, H1, Export ▾ dropdown |
| Toolbar | Search, Stage/Score filters, Clear |
| Table | 5 rows §9.5 with score badges |
| Footer | Pagination |

#### Fields

Filter dropdowns only (no free-text forms except search)

#### Actions

| Control | Prototype |
|---------|-----------|
| Alex Chen row / name | → P4 |
| Export | Annotate: CSV — BR-037 |
| Bulk Reject | Annotate: requires justification |
| Score badge hover | Sticky: "AI rationale summary" |

#### Data displayed

§9.2 (job context), §9.5

#### Build checklist

- [ ] Default sort: score descending (92 at top)
- [ ] David Kim row: red score 45, Rejected stage
- [ ] Page title includes REQ-2026-0142

---

### SCREEN 4 — Candidate Details `04 — Candidate Details`

| Attribute | Value |
|-----------|-------|
| **Priority** | P4 |
| **Traceability** | BR-017, BR-005 · FR-AIS-004, FR-AIS-008, FR-AIS-010, FR-RM-005 · US-AIS-004, US-AIS-007, US-RES-006 · BUS-003 |

#### Layout structure

```
┌─────────────────────────────────────────────────────────────┐
│ TopBar + Sidebar (Candidates ACTIVE)                         │
├─────────────────────────────────────────────────────────────┤
│ ← Back to Candidates                                         │
│ Profile header card — avatar, name, score, stage, actions    │
│ Tab bar: Profile | Resume | AI Analysis* | Interviews | ...  │
│ ┌────────────────────────┬─────────────────────────────┐      │
│ │ AI Match card 50%      │ Skills Match grid 50%       │      │
│ └────────────────────────┴─────────────────────────────┘      │
│ Experience card full width                                    │
│ [Override Score] link → opens Modal component overlay           │
└─────────────────────────────────────────────────────────────┘
```

*Active tab for demo: **AI Analysis** (or Profile with analysis visible)

#### Widgets

| Zone | Widgets |
|------|---------|
| Header card | Avatar 64px, name H1, email, applied date, source, score badge 92, stage pill |
| Actions | `Advance ▾` split button, `Reject` danger |
| Tabs | 6 tabs — bold AI Analysis |
| AI card | Progress bar 92%, rationale quote, "View Full Rationale" link |
| Skills card | Tag grid ✅/❌, `Override Score` button |
| Experience | Parsed timeline |
| Modal | `Modal/Override Score` — attach as overlay variant |

#### Fields (modal only)

New score (dropdown), Justification (textarea)

#### Actions

| Control | Behavior |
|---------|----------|
| ← Back | → P3 |
| Advance | Annotate: stage change + notification BR-022 |
| Reject | Annotate: justification required |
| Override Score | Open modal overlay |
| View Full Rationale | Expand sticky note with full text §9.6 |
| Resume tab | Annotate: PDF viewer — US-RES-006 |

#### Data displayed

§9.6

#### Build checklist

- [ ] Stage stepper above tabs: Applied → **Screened** → Interview → Offer → Hired
- [ ] Modal component with §9.3 validation messages
- [ ] Sticky note: "BR-017 explainable AI | BUS-003 override audit"

---

### SCREEN 5 — Job Requisition `05 — Job Requisition`

| Attribute | Value |
|-----------|-------|
| **Priority** | P5 |
| **Traceability** | BR-019, BR-018, BR-020 · FR-JM-001, FR-JM-002 · US-JOB-001, US-JOB-002, US-JOB-003 · BUS-001 |

#### Layout structure

```
┌─────────────────────────────────────────────────────────────┐
│ TopBar + Sidebar (Jobs ACTIVE)                               │
├─────────────────────────────────────────────────────────────┤
│ Breadcrumb: Dashboard → Jobs → New Requisition               │
│ H1: Create Job Requisition                                   │
│ ┌─────────────────────────┬─────────────────────────┐       │
│ │ Job Details 60%         │ Requirements 40%        │       │
│ │ §7.2 left fields        │ §7.2 right fields       │       │
│ └─────────────────────────┴─────────────────────────┘       │
│ Footer: Save Draft | Submit for Approval                     │
│ Toast overlay variant (success)                              │
└─────────────────────────────────────────────────────────────┘
```

#### Widgets

| Zone | Widgets |
|------|---------|
| Form left | All Job Details fields §7.2 |
| Form right | Skills tags (pre-filled), knockouts, AI toggle |
| Footer | Ghost + Primary buttons |
| Success variant | Green toast top-right |

#### Fields

§7.2 — pre-fill with Sr. Software Developer sample data for demo

#### Actions

| Control | Prototype |
|---------|-----------|
| Submit for Approval | → P2 + show toast "Requisition submitted to HR Manager for approval" |
| Save Draft | Annotate only |
| Cancel / Back | → P2 |

#### Data displayed

Pre-filled example:
- Title: Senior Software Developer
- Department: Engineering
- Skills: Python, React, AWS
- Min experience: 5

#### Build checklist

- [ ] Error variant with §9.2 messages
- [ ] Sticky: "BUS-001: HR approval required before publish"
- [ ] AI Screening toggle ON

---

### SCREEN 6 — Reports Dashboard `06 — Reports Dashboard`

| Attribute | Value |
|-----------|-------|
| **Priority** | P6 |
| **Traceability** | BR-031, BR-033, BR-007 · FR-RPT-001, FR-RPT-004 · US-RPT-001, US-RPT-002, US-RPT-003, US-RPT-006 · RR-001, RR-002, RR-006 · KPI-002, KPI-006, KPI-011 |

#### Layout structure

```
┌─────────────────────────────────────────────────────────────┐
│ TopBar + Sidebar (Reports ACTIVE)                            │
├─────────────────────────────────────────────────────────────┤
│ H1: Reports & Analytics                                      │
│ ┌──────────┬──────────────────────────────────────────────┐  │
│ │ Report   │ Main panel                                    │  │
│ │ catalog  │ Date range + Department filter                │  │
│ │ 200px    │ H2: Hiring Pipeline Funnel                    │  │
│ │          │ Funnel chart (large)                          │  │
│ │          │ 3 KPI tiles                                   │  │
│ │          │ Export PDF | Export CSV | Fullscreen           │  │
│ └──────────┴──────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

#### Widgets

| Zone | Widgets |
|------|---------|
| Catalog | List: **Pipeline Funnel** (active), Time-to-Hire, Offer Acceptance, Recruiter Performance (others grayed) |
| Filters | Date range picker, Department ▾ |
| Chart | Large `Chart/Funnel` — §9.4 with labels |
| KPI row | 3 tiles §9.7 |
| Actions | Export PDF, Export CSV (secondary buttons) |

#### Fields

Date range (display only), Department select

#### Actions

| Control | Annotate |
|---------|----------|
| Export CSV | US-RPT-006, FR-RPT-004 |
| Time-to-Hire catalog item | Switch content — annotate second variant optional |
| Chart segment click | Drill to candidate list — US-RPT-013 |
| Fullscreen | Annotate only |

#### Data displayed

§9.4, §9.7

#### Build checklist

- [ ] Pipeline Funnel selected in catalog
- [ ] Conversion rate 4.5% visible
- [ ] Sticky: "RR-001 real-time funnel | KPI-006 time-to-hire"

---

## 11. Traceability Matrix (paste on `03 Prototype` page)

| Screen | Business Req | User Stories | Process / Rules |
|--------|--------------|--------------|-----------------|
| Login | BR-009, BR-011 | US-AUTH-003 | Recruiter access to TO-BE workflow |
| Dashboard | BR-031, BR-033 | US-JOB-010, US-RPT-009 | PR-005 aging escalation |
| Candidate List | BR-002, BR-003 | US-AIS-001, US-AIS-005 | AI screen step in TO-BE |
| Candidate Details | BR-017, BR-005 | US-AIS-004, US-AIS-007 | BUS-003 override rule |
| Job Requisition | BR-019, BR-018 | US-JOB-001, US-JOB-002 | BUS-001 HR approval |
| Reports | BR-031, BR-007 | US-RPT-001, US-RPT-002 | RR-001, RR-002 |

---

## 12. Figma Prototype Settings

| Setting | Value |
|---------|-------|
| Device | None (desktop frame) |
| Interaction | On click |
| Animation | Instant (or Smart animate 200ms for modal) |
| Starting frame | `01 — Login` |
| Flow cover | "HireFlow AI — BA Portfolio Demo" |

---

## 13. Interview Talking Points (per screen)

| Screen | 20-second script |
|--------|------------------|
| Login | "FR-AUTH covers secure recruiter access; SSO buttons show enterprise requirement BR-009." |
| Dashboard | "Recruiters needed pipeline visibility — BR-031. Aging flag implements PR-005 escalation." |
| Candidate List | "BR-002 and BR-003: AI ranks candidates so recruiters review top matches first, not 200 resumes." |
| Candidate Details | "BR-017 requires explainable AI. BUS-003: override below 40 needs justification — modal captures that." |
| Job Requisition | "BR-019: every hire starts with a structured req. BUS-001: submit routes to HR approval before publish." |
| Reports | "RR-001 funnel and KPI-006 time-to-hire — I defined these in reporting requirements, not built BI." |

---

*Build this file only. Six screens. No additional pages. Annotate everything else with sticky notes.*
