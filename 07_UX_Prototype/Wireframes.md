# Wireframe Specifications
## HireFlow AI — AI-Powered Recruitment & Interview Management Platform

| Field | Value |
|-------|-------|
| **Document ID** | WF-HFA-2026-001 |
| **Version** | 1.0 |
| **Author** | Rohit, Business Analyst |
| **Status** | Approved for Design |
| **Design Tool** | Figma (recommended) |
| **Date** | June 8, 2026 |

---

## 1. Document Purpose

This document provides Figma-ready wireframe specifications for nine core HireFlow AI screens. Each specification includes layout structure, component inventory, interaction behaviors, UX notes, and responsive breakpoints. Designers and developers use this as the single source of truth for UI implementation.

**Design System Reference:** React 18, TypeScript, Tailwind CSS; WCAG 2.1 AA compliance (NFR-012).

**Viewport Targets:** Desktop (1280px+), Tablet (768–1279px), Mobile (320–767px).

---

## 2. Global Design Tokens

| Token | Value | Usage |
|-------|-------|-------|
| Primary Color | `#2563EB` (Blue 600) | CTAs, links, active states |
| Secondary Color | `#0F172A` (Slate 900) | Headers, navigation |
| Success | `#16A34A` | Positive actions, pass states |
| Warning | `#D97706` | Alerts, pending states |
| Error | `#DC2626` | Validation, rejection states |
| Background | `#F8FAFC` | Page background |
| Surface | `#FFFFFF` | Cards, panels |
| Border Radius | `8px` (cards), `6px` (inputs) | Consistent rounding |
| Font Family | Inter, system-ui | All text |
| Base Font Size | 16px | Body text |
| Grid | 12-column, 24px gutter | Desktop layout |
| Spacing Unit | 8px base (8, 16, 24, 32, 48) | Margins and padding |

---

## 3. Screen 1 — Login

### 3.1 Screen Metadata

| Attribute | Value |
|-----------|-------|
| **Screen ID** | SCR-AUTH-001 |
| **Route** | `/login` |
| **Primary Users** | All roles (Recruiter, HR, Panel, Company Admin) |
| **Related Requirements** | FR-AUTH-001 through FR-AUTH-011 |

### 3.2 Layout Description

```
┌──────────────────────────────────────────────────────────────────────┐
│                         VIEWPORT: 100vh                               │
│  ┌─────────────────────┬──────────────────────────────────────────┐  │
│  │                     │                                          │  │
│  │   BRAND PANEL       │           LOGIN FORM PANEL               │  │
│  │   (40% width)       │           (60% width)                    │  │
│  │                     │                                          │  │
│  │   [Company Logo]    │   HireFlow AI                            │  │
│  │                     │   Sign in to your account                │  │
│  │   Tagline:          │                                          │  │
│  │   "Hire smarter     │   [Email Input          ]                │  │
│  │    with AI"         │   [Password Input    👁 ]                │  │
│  │                     │                                          │  │
│  │   [Illustration]    │   ☐ Remember me    Forgot password?      │  │
│  │                     │                                          │  │
│  │                     │   [        Sign In (Primary CTA)       ]   │  │
│  │                     │                                          │  │
│  │                     │   ─────── or continue with ───────       │  │
│  │                     │   [Google SSO]  [Microsoft SSO]          │  │
│  │                     │                                          │  │
│  │                     │   Don't have an account? Register        │  │
│  └─────────────────────┴──────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────────────┘
```

### 3.3 Components

| Component | Type | Properties | Validation |
|-----------|------|------------|------------|
| Email Input | Text field | Label, placeholder, required asterisk | Email format; inline error |
| Password Input | Password field | Show/hide toggle icon | Min 12 chars on reset only |
| Remember Me | Checkbox | Default unchecked | — |
| Forgot Password | Text link | Routes to `/forgot-password` | — |
| Sign In Button | Primary button | Full width, disabled until valid | Loading spinner on submit |
| SSO Buttons | Secondary buttons | Google, Microsoft icons | OAuth redirect |
| Register Link | Text link | Routes to `/register` | — |
| Error Banner | Alert | Top of form; dismissible | Account lockout after 5 attempts |

### 3.4 Interactions

| Action | Trigger | Behavior |
|--------|---------|----------|
| Sign In | Click CTA or Enter key | Validate → API auth → redirect to role-based dashboard |
| SSO Login | Click provider button | Redirect to OIDC/SAML flow (FR-AUTH-004, FR-AUTH-005) |
| Forgot Password | Click link | Navigate to password reset flow |
| Show Password | Click eye icon | Toggle password visibility |
| Failed Login | API 401 | Increment counter; show "4 attempts remaining" |
| Account Locked | 5th failure | Show lockout message with 30-min timer (FR-AUTH-009) |
| MFA Required | API 202 | Redirect to MFA verification screen |

### 3.5 UX Notes

- Brand panel hidden on mobile; full-width form only
- Focus order: Email → Password → Remember Me → Sign In → SSO → Register
- Error messages announced via `aria-live="polite"`
- SSO buttons meet 44×44px minimum touch target
- Session persists 7 days if "Remember me" checked

### 3.6 Responsive Behavior

| Breakpoint | Layout Change |
|------------|---------------|
| Desktop (≥1280px) | Split 40/60 brand + form |
| Tablet (768–1279px) | Split 30/70; smaller illustration |
| Mobile (<768px) | Single column; logo above form; stacked SSO buttons |

---

## 4. Screen 2 — Registration

### 4.1 Screen Metadata

| Attribute | Value |
|-----------|-------|
| **Screen ID** | SCR-AUTH-002 |
| **Route** | `/register` (candidates) / `/signup` (company trial) |
| **Primary Users** | Candidate, Company Admin |
| **Related Requirements** | FR-AUTH-001, FR-AUTH-002, BR-021 |

### 4.2 Layout Description

```
┌──────────────────────────────────────────────────────────────────────┐
│  [Logo]  HireFlow AI                              Already a member?   │
│                                                    Sign in →          │
├──────────────────────────────────────────────────────────────────────┤
│                                                                       │
│   Create Your Account                                                 │
│   Step 2 of 3: Profile Details                                        │
│   ●━━━━━━━●━━━━━━━○                                                   │
│                                                                       │
│   ┌─────────────────────────────┐  ┌─────────────────────────────┐   │
│   │ First Name *                │  │ Last Name *                 │   │
│   └─────────────────────────────┘  └─────────────────────────────┘   │
│   ┌───────────────────────────────────────────────────────────────┐  │
│   │ Email Address *                                               │  │
│   └───────────────────────────────────────────────────────────────┘  │
│   ┌───────────────────────────────────────────────────────────────┐  │
│   │ Password *                          Strength: ████░░ Strong   │  │
│   └───────────────────────────────────────────────────────────────┘  │
│   ┌───────────────────────────────────────────────────────────────┐  │
│   │ Confirm Password *                                            │  │
│   └───────────────────────────────────────────────────────────────┘  │
│                                                                       │
│   ☐ I agree to Terms of Service and Privacy Policy *                  │
│   ☐ I consent to data processing per GDPR (EU candidates) *             │
│                                                                       │
│   [ ← Back ]                              [ Continue → ]            │
│                                                                       │
└──────────────────────────────────────────────────────────────────────┘
```

### 4.3 Components

| Component | Type | Properties |
|-----------|------|------------|
| Progress Stepper | Step indicator | 3 steps: Account → Profile → Verify |
| Name Fields | Text inputs | Side-by-side on desktop; stacked mobile |
| Email Input | Text field | Real-time duplicate check debounced 500ms |
| Password Input | Password field | Strength meter (weak/fair/strong) |
| Confirm Password | Password field | Match validation on blur |
| Consent Checkboxes | Checkbox group | Required; links open in modal |
| Back / Continue | Button pair | Back disabled on step 1 |
| Verification Panel | Step 3 content | "Check your email" with resend link |

### 4.4 Interactions

| Action | Trigger | Behavior |
|--------|---------|----------|
| Continue | Click CTA | Validate step → advance stepper |
| Password Strength | Keystroke | Update meter: 12+ chars, upper, lower, number, special |
| Email Verification | Step 3 load | Show instructions; poll status every 5 sec |
| Resend Email | Click link | API call; 60-sec cooldown timer |
| GDPR Consent | EU geo-detected | Auto-display GDPR checkbox (BR-006) |

### 4.5 UX Notes

- Multi-step reduces cognitive load; save progress in session storage
- Password requirements shown as checklist that ticks off progressively
- Company Admin registration includes additional "Company Name" field on step 2
- Candidate registration links to job context if arriving from career portal

### 4.6 Responsive Behavior

| Breakpoint | Layout Change |
|------------|---------------|
| Desktop | Centered card, max-width 640px |
| Tablet | Full-width card with 48px horizontal padding |
| Mobile | Full-width; name fields stack vertically |

---

## 5. Screen 3 — Dashboard

### 5.1 Screen Metadata

| Attribute | Value |
|-----------|-------|
| **Screen ID** | SCR-DASH-001 |
| **Route** | `/dashboard` |
| **Primary Users** | Recruiter, HR Manager |
| **Related Requirements** | BR-031, FR-RPT-001, FR-RPT-002 |

### 5.2 Layout Description

```
┌────────────────────────────────────────────────────────────────────────────┐
│ [Logo] HireFlow AI    [Search...]    🔔(3)  [Avatar ▾]                     │
├──────────┬─────────────────────────────────────────────────────────────────┤
│          │  Good morning, Sarah 👋                          [+ New Req]     │
│ SIDEBAR  │  ─────────────────────────────────────────────────────────────  │
│          │                                                                  │
│ Dashboard│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐           │
│ Jobs     │  │ Open Req │ │ Active   │ │ Time to  │ │ Offer    │           │
│ Candidates│ │    24    │ │ Pipeline │ │ Hire     │ │ Accept   │           │
│ Interviews│ │          │ │   156    │ │ 21 days  │ │   86%    │           │
│ Reports  │  └──────────┘ └──────────┘ └──────────┘ └──────────┘           │
│ Settings │                                                                  │
│          │  ┌─────────────────────────────┐ ┌─────────────────────────┐   │
│          │  │ HIRING PIPELINE FUNNEL      │ │ RECENT ACTIVITY         │   │
│          │  │ Applied ████████████ 142     │ │ • John D. advanced      │   │
│          │  │ Screened ████████ 89        │ │ • AI interview done     │   │
│          │  │ Interview ████ 34           │ │ • Offer sent — Jane S.  │   │
│          │  │ Offer ██ 8                  │ │ • New app: Sr. Dev      │   │
│          │  │ Hired █ 3                   │ │ [View all →]            │   │
│          │  └─────────────────────────────┘ └─────────────────────────┘   │
│          │                                                                  │
│          │  ┌──────────────────────────────────────────────────────────┐  │
│          │  │ MY REQUISITIONS                          [Filter ▾] [↻]  │  │
│          │  │ Title          │ Apps │ Pipeline │ Status  │ Aging │ Act │  │
│          │  │ Sr. Developer  │  42  │ 12 active│ Open    │ 12d   │ ••• │  │
│          │  │ Product Mgr    │  28  │  8 active│ Open    │ 31d ⚠│ ••• │  │
│          │  └──────────────────────────────────────────────────────────┘  │
└──────────┴─────────────────────────────────────────────────────────────────┘
```

### 5.3 Components

| Component | Type | Properties |
|-----------|------|------------|
| Top Navigation | Header bar | Logo, global search, notifications bell, user menu |
| Sidebar Navigation | Vertical nav | Collapsible; role-based menu items |
| KPI Cards | Stat cards (4) | Value, label, trend arrow, sparkline |
| Pipeline Funnel | Horizontal bar chart | Stage counts; click to drill down |
| Activity Feed | Timeline list | Last 10 events; real-time WebSocket updates |
| Requisitions Table | Data table | Sortable columns; row actions menu |
| Quick Action FAB | Floating button | Mobile only: New Req, Add Candidate |
| Aging Warning | Badge icon | Amber at 30 days; red at 45 days (PR-005) |

### 5.4 Interactions

| Action | Trigger | Behavior |
|--------|---------|----------|
| KPI Card Click | Click card | Navigate to filtered report view |
| Funnel Stage Click | Click bar segment | Open Candidate List filtered by stage |
| Requisition Row | Click row | Navigate to job detail / candidate list |
| New Requisition | Click CTA | Open requisition creation modal |
| Notification Bell | Click | Dropdown with unread notifications |
| Sidebar Collapse | Click hamburger | Collapse to icon-only (64px) |
| Global Search | Type + Enter | Search candidates, jobs, requisitions |

### 5.5 UX Notes

- Role-based dashboard: HR sees approval queue; Recruiter sees pipeline
- KPI cards load skeleton placeholders; data fetches < 2 sec (NFR-001)
- Aging warning aligns with 45-day escalation business rule
- Empty state for new users: onboarding checklist with 4 setup steps

### 5.6 Responsive Behavior

| Breakpoint | Layout Change |
|------------|---------------|
| Desktop | Sidebar visible (240px); 4-column KPI grid |
| Tablet | Collapsed sidebar; 2×2 KPI grid; table horizontal scroll |
| Mobile | Bottom tab navigation; single-column KPIs; card-based req list |

---

## 6. Screen 4 — Candidate List

### 6.1 Screen Metadata

| Attribute | Value |
|-----------|-------|
| **Screen ID** | SCR-CAND-001 |
| **Route** | `/candidates` or `/jobs/:id/candidates` |
| **Primary Users** | Recruiter, HR Manager |
| **Related Requirements** | BR-003, FR-AIS-002, BR-037 |

### 6.2 Layout Description

```
┌────────────────────────────────────────────────────────────────────────────┐
│  Candidates — Sr. Developer (REQ-2026-0142)                    [Export ▾]  │
├────────────────────────────────────────────────────────────────────────────┤
│  [🔍 Search candidates...]  [Stage ▾] [Score ▾] [Source ▾]  [Clear filters]│
│                                                                              │
│  ☐ Select All (42)          [Bulk Actions ▾: Advance | Reject | Email]      │
│  ─────────────────────────────────────────────────────────────────────────  │
│  ☐ │ Rank │ Name          │ AI Score │ Stage      │ Skills Match │ Updated  │
│  ─────────────────────────────────────────────────────────────────────────  │
│  ☐ │  1 ▲ │ Alex Chen     │  92 🟢   │ Screened   │ 8/10 skills  │ 2h ago  │
│  ☐ │  2   │ Maria Santos  │  87 🟢   │ AI Intervw │ 7/10 skills  │ 5h ago  │
│  ☐ │  3   │ James Wilson  │  74 🟡   │ Applied    │ 6/10 skills  │ 1d ago  │
│  ☐ │  4   │ Priya Patel   │  68 🟡   │ Applied    │ 5/10 skills  │ 1d ago  │
│  ☐ │  5 ▼ │ David Kim     │  45 🔴   │ Rejected   │ 3/10 skills  │ 2d ago  │
│  ─────────────────────────────────────────────────────────────────────────  │
│  Showing 1–25 of 42                              [ < 1 2 > ]  [25 ▾/page]  │
└────────────────────────────────────────────────────────────────────────────┘
```

### 6.3 Components

| Component | Type | Properties |
|-----------|------|------------|
| Page Header | Title bar | Job title, req ID, export dropdown |
| Filter Bar | Filter chips + dropdowns | Stage, score range, source, date |
| Bulk Action Bar | Toolbar | Appears when ≥1 row selected |
| Data Table | Sortable table | Checkbox, rank, name, score, stage, skills, date |
| AI Score Badge | Color-coded pill | Green ≥80, Amber 40–79, Red <40 |
| Skills Match | Text indicator | "8/10 skills" with tooltip for details |
| Pagination | Page controls | 25/50/100 per page |
| Empty State | Illustration + CTA | "No candidates yet" with share job link |

### 6.4 Interactions

| Action | Trigger | Behavior |
|--------|---------|----------|
| Row Click | Click name cell | Navigate to Candidate Details |
| Sort Column | Click header | Toggle ascending/descending |
| Bulk Advance | Select + action | Confirmation modal → advance selected |
| Bulk Reject | Select + action | Require justification textarea |
| Filter Apply | Select filter | URL params update; table re-fetches |
| Export | Click dropdown | CSV, Excel, PDF download |
| Score Tooltip | Hover score | Show AI rationale summary |

### 6.5 UX Notes

- Default sort: AI score descending (FR-AIS-002)
- Rejected candidates shown with strikethrough; toggle "Show rejected"
- Rank column shows movement indicator (▲/▼) since last visit
- Virtual scrolling for lists > 100 candidates

### 6.6 Responsive Behavior

| Breakpoint | Layout Change |
|------------|---------------|
| Desktop | Full table with all columns |
| Tablet | Hide Skills Match and Updated columns |
| Mobile | Card layout per candidate; swipe actions for advance/reject |

---

## 7. Screen 5 — Candidate Details

### 7.1 Screen Metadata

| Attribute | Value |
|-----------|-------|
| **Screen ID** | SCR-CAND-002 |
| **Route** | `/candidates/:id` |
| **Primary Users** | Recruiter, HR Manager, Panel |
| **Related Requirements** | FR-AIS-004, FR-AIS-010, FR-CE-006 |

### 7.2 Layout Description

```
┌────────────────────────────────────────────────────────────────────────────┐
│  ← Back to Candidates                                                       │
├────────────────────────────────────────────────────────────────────────────┤
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │ [Avatar]  Alex Chen                    AI Score: 92  [Advance ▾]  │   │
│  │           alex.chen@email.com          Stage: Screened  [Reject]    │   │
│  │           Applied: Mar 15, 2026        Source: Career Portal        │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│  [Profile] [Resume] [AI Analysis] [Interviews] [Evaluations] [Activity]     │
│  ─────────────────────────────────────────────────────────────────────────  │
│                                                                              │
│  ┌──────────────────────────────┐  ┌──────────────────────────────────┐   │
│  │ AI MATCH ANALYSIS            │  │ SKILLS MATCH                     │   │
│  │ ████████████████████ 92%    │  │ ✅ Python  ✅ React  ✅ AWS       │   │
│  │                              │  │ ✅ SQL     ✅ Docker ❌ Kubernetes │   │
│  │ "Strong match on technical   │  │ ❌ GraphQL                        │   │
│  │  skills and 7 years exp..."  │  │                                  │   │
│  │ [View Full Rationale]        │  │ [Override Score]                  │   │
│  └──────────────────────────────┘  └──────────────────────────────────┘   │
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │ EXPERIENCE (Parsed)                                                   │  │
│  │ Senior Developer — TechCorp — 2020–Present (5 yrs)                     │  │
│  │ Developer — StartupXYZ — 2018–2020 (2 yrs)                           │  │
│  │ Education: MS Computer Science, State University                       │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
└────────────────────────────────────────────────────────────────────────────┘
```

### 7.3 Components

| Component | Type | Properties |
|-----------|------|------------|
| Profile Header | Hero card | Avatar, name, contact, score badge, stage pill |
| Action Dropdown | Split button | Advance, Schedule Interview, Send Email |
| Tab Navigation | Horizontal tabs | 6 tabs; badge counts on Interviews, Evaluations |
| AI Score Card | Progress + text | Score bar, explainable rationale excerpt |
| Skills Match Grid | Tag grid | Green check / red X per skill |
| Experience Timeline | Parsed data display | Work history, education |
| Resume Viewer | PDF embed tab | Inline viewer with download button |
| Activity Log | Timeline tab | All status changes with timestamps |
| Override Modal | Dialog | Justification textarea (FR-AIS-008) |

### 7.4 Interactions

| Action | Trigger | Behavior |
|--------|---------|----------|
| Advance Stage | Click CTA | Confirm modal → update stage → notification sent |
| Reject | Click button | Require justification → confirm → rejection email |
| Override Score | Click link | Modal with new score + mandatory justification |
| Tab Switch | Click tab | Lazy-load tab content |
| View Rationale | Click link | Expand full AI explanation panel |
| Download Resume | Click icon | Download original file from S3 |

### 7.5 UX Notes

- Panel members see redacted view (no contact info) until interview stage (FR-RM-008)
- Stage progression shown as horizontal stepper above tabs
- All actions logged to audit trail with user and timestamp
- Duplicate candidate merge indicator if profile was merged (BUS-013)

### 7.6 Responsive Behavior

| Breakpoint | Layout Change |
|------------|---------------|
| Desktop | Two-column analysis cards; tabs horizontal |
| Tablet | Single-column cards; tabs scrollable |
| Mobile | Sticky action bar at bottom; accordion instead of tabs |

---

## 8. Screen 6 — AI Interview Screen

### 8.1 Screen Metadata

| Attribute | Value |
|-----------|-------|
| **Screen ID** | SCR-AII-001 |
| **Route** | `/interview/ai/:sessionId` |
| **Primary Users** | Candidate |
| **Related Requirements** | FR-AII-001 through FR-AII-010, BR-014 |

### 8.2 Layout Description

```
┌────────────────────────────────────────────────────────────────────────────┐
│  HireFlow AI Interview — Sr. Developer                                      │
│  Question 3 of 8                              ⏱ 18:42 remaining            │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │                                                                        │  │
│  │                     [ CAMERA PREVIEW AREA ]                            │  │
│  │                     Candidate video feed                               │  │
│  │                     640 × 480                                        │  │
│  │                                                                        │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │ 🤖 "Describe a challenging technical problem you solved recently.      │  │
│  │     What was your approach and what was the outcome?"                  │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                              │
│  ● Recording...  [🎤 Mic: On]  [📷 Camera: On]                             │
│                                                                              │
│  [ ← Previous ]    [ Pause ]    [ Submit Answer & Next → ]                  │
│                                                                              │
│  Progress: ●●●○○○○○  3/8 questions                                          │
└────────────────────────────────────────────────────────────────────────────┘
```

### 8.3 Components

| Component | Type | Properties |
|-----------|------|------------|
| Session Header | Top bar | Job title, question counter, countdown timer |
| Camera Preview | Video element | WebRTC stream; mirror mode for candidate |
| Question Card | Text panel | AI-generated question; text-to-speech option |
| Recording Indicator | Status pill | Pulsing red dot when recording |
| Media Controls | Toggle buttons | Mic on/off, camera on/off |
| Navigation Buttons | Button group | Previous (disabled Q1), Pause, Submit & Next |
| Progress Dots | Step indicator | Filled/unfilled circles per question |
| Pre-Interview Modal | Setup wizard | Camera/mic test, practice mode option |
| Completion Screen | End state | Thank you message, next steps timeline |

### 8.4 Interactions

| Action | Trigger | Behavior |
|--------|---------|----------|
| Start Interview | Pre-interview CTA | Begin recording; start 30-min timer |
| Submit Answer | Click CTA | Stop recording → upload → load next question |
| Pause | Click button | Pause timer and recording; show resume modal |
| Previous | Click button | Review prior answer (read-only); no re-record |
| Timer Expiry | Timer reaches 0 | Auto-submit current answer; proceed or end |
| Practice Mode | Pre-interview toggle | 2 sample questions; no scoring (FR-AII-007) |
| Connection Lost | WebSocket drop | Auto-save; resume on reconnect |

### 8.5 UX Notes

- Calm, focused UI; minimal distractions; no sidebar navigation
- Large readable question text (18px+); high contrast (WCAG AA)
- Camera permission prompt with friendly instructions before session
- Mobile supported but desktop recommended for best video quality
- Inappropriate behavior flag runs in background (FR-AII-008)

### 8.6 Responsive Behavior

| Breakpoint | Layout Change |
|------------|---------------|
| Desktop | Camera preview 640×480 centered; question below |
| Tablet | Camera preview 480×360; buttons full-width |
| Mobile | Camera preview full-width; stacked buttons; landscape encouraged |

---

## 9. Screen 7 — Reports

### 9.1 Screen Metadata

| Attribute | Value |
|-----------|-------|
| **Screen ID** | SCR-RPT-001 |
| **Route** | `/reports` |
| **Primary Users** | HR Manager, CHRO, Compliance |
| **Related Requirements** | FR-RPT-001 through FR-RPT-010, RR-001 through RR-015 |

### 9.2 Layout Description

```
┌────────────────────────────────────────────────────────────────────────────┐
│  Reports & Analytics                                                        │
├──────────┬─────────────────────────────────────────────────────────────────┤
│ REPORT   │  Hiring Pipeline Funnel                    [Date Range ▾] [↻]  │
│ CATALOG  │  Jan 1, 2026 — Jun 8, 2026                                    │
│          │                                                                  │
│ ▸ Funnel │  ┌────────────────────────────────────────────────────────────┐  │
│ ▸ Time   │  │     [Stacked bar / funnel chart visualization]              │  │
│ ▸ Cost   │  │                                                            │  │
│ ▸ Recruiter│ │                                                            │  │
│ ▸ Diversity│ └────────────────────────────────────────────────────────────┘  │
│ ▸ AI Audit│                                                                  │
│ ▸ Source  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐              │
│          │  │ Applied 842  │ │ Hired 38    │ │ Conv. 4.5%  │              │
│          │  └─────────────┘ └─────────────┘ └─────────────┘              │
│          │                                                                  │
│          │  [Export PDF]  [Export CSV]  [Schedule Email ▾]  [Fullscreen]   │
└──────────┴─────────────────────────────────────────────────────────────────┘
```

### 9.3 Components

| Component | Type | Properties |
|-----------|------|------------|
| Report Catalog | Left sidebar list | 15 report types grouped by category |
| Date Range Picker | Filter control | Presets: 7d, 30d, 90d, YTD, custom |
| Chart Area | Visualization | Bar, funnel, line, pie per report type |
| Summary Stats | KPI row | 3–4 key metrics for selected report |
| Department Filter | Multi-select | Filter by department, location, recruiter |
| Export Controls | Button group | PDF, CSV, Excel (FR-RPT-004) |
| Schedule Modal | Dialog | Email, frequency, recipient list |
| Compliance Badge | Report header | EEOC, bias audit reports marked "Restricted" |

### 9.4 Interactions

| Action | Trigger | Behavior |
|--------|---------|----------|
| Select Report | Click catalog item | Load report with default date range |
| Date Change | Select range | Re-fetch data; update charts |
| Export | Click format | Generate file download |
| Schedule | Click + configure | Create scheduled delivery (FR-RPT-005) |
| Drill Down | Click chart segment | Filter dashboard to that segment |
| Fullscreen | Click icon | Expand chart to full viewport |

### 9.5 UX Notes

- Compliance reports (EEOC, Bias Audit) restricted to Compliance + HR roles
- Charts render with skeleton loaders; target < 2 sec load
- Scheduled reports shown in "My Scheduled Reports" sub-section
- Empty state: "Not enough data" with minimum data requirements note

### 9.6 Responsive Behavior

| Breakpoint | Layout Change |
|------------|---------------|
| Desktop | Sidebar + chart area side by side |
| Tablet | Collapsible report catalog drawer |
| Mobile | Report selector dropdown; simplified charts; export via share sheet |

---

## 10. Screen 8 — Settings

### 10.1 Screen Metadata

| Attribute | Value |
|-----------|-------|
| **Screen ID** | SCR-SET-001 |
| **Route** | `/settings` |
| **Primary Users** | Company Admin, All users (personal settings) |
| **Related Requirements** | FR-UM-001, FR-AUTH-007, FR-NOT-004, BR-039 |

### 10.2 Layout Description

```
┌────────────────────────────────────────────────────────────────────────────┐
│  Settings                                                                   │
├──────────┬─────────────────────────────────────────────────────────────────┤
│          │  Company Profile                                                 │
│ NAV      │  ─────────────────────────────────────────────────────────────  │
│          │                                                                  │
│ Company  │  Company Name        [ Acme Corporation          ]               │
│ Users    │  Logo                [Upload] [logo_preview.png]                 │
│ Roles    │  Career Portal URL   https://acme.hireflow.ai/careers  [Copy]   │
│ Policies │  Brand Color         [#2563EB] 🎨                                │
│ Integrations│                                                              │
│ Notif.   │  Departments         [+ Add Department]                          │
│ Security │  ┌──────────────────────────────────────────────────────────┐   │
│ Audit    │  │ Engineering (42 users) │ Sales (18 users) │ HR (8)     │   │
│          │  └──────────────────────────────────────────────────────────┘   │
│          │                                                                  │
│          │  [Cancel]  [Save Changes]                                        │
└──────────┴─────────────────────────────────────────────────────────────────┘
```

### 10.3 Components

| Component | Type | Properties |
|-----------|------|------------|
| Settings Nav | Left sidebar | 8 sections; role-based visibility |
| Form Sections | Grouped inputs | Company, users, roles, policies, etc. |
| Logo Upload | File upload | PNG/SVG, max 2MB; preview thumbnail |
| Color Picker | Input + swatch | Brand color for career portal (BR-039) |
| Department Manager | Inline table | Add, edit, delete departments |
| User Table | Data table | Name, role, status, last login; bulk import |
| Role Permissions | Matrix grid | Checkbox grid: role × permission |
| Integration Cards | Card grid | SSO, Calendar, HRIS — connect/disconnect |
| Notification Prefs | Toggle list | Per-event email/in-app toggles |
| Audit Log Viewer | Searchable table | Date, user, action, entity — read only |

### 10.4 Interactions

| Action | Trigger | Behavior |
|--------|---------|----------|
| Save Changes | Click CTA | Validate → API PATCH → success toast |
| Upload Logo | File select | Preview → upload to S3 on save |
| Add User | Click CTA | Modal form; sends welcome email (FR-UM-006) |
| Bulk Import | CSV upload | Validation report; confirm import |
| Connect SSO | Click card | SAML/OIDC configuration wizard |
| Toggle Notification | Flip switch | Auto-save per preference (FR-NOT-004) |

### 10.5 UX Notes

- Company Admin sees all sections; regular users see only Profile + Notifications
- Destructive actions (delete user, disconnect SSO) require confirmation modal
- Unsaved changes warning on navigation away
- Audit log section read-only for all except Compliance (FR-AUD-003)

### 10.6 Responsive Behavior

| Breakpoint | Layout Change |
|------------|---------------|
| Desktop | Sidebar nav + content area |
| Tablet | Horizontal scrollable nav tabs |
| Mobile | Accordion sections; nav as dropdown selector |

---

## 11. Screen 9 — Subscription Management

### 11.1 Screen Metadata

| Attribute | Value |
|-----------|-------|
| **Screen ID** | SCR-BIL-001 |
| **Route** | `/settings/subscription` |
| **Primary Users** | Company Admin, Finance |
| **Related Requirements** | FR-BIL-001 through FR-BIL-010, BR-008 |

### 11.2 Layout Description

```
┌────────────────────────────────────────────────────────────────────────────┐
│  Subscription & Billing                                                     │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  Current Plan: Professional                    Status: ● Active              │
│  Billing Cycle: Annual                         Renews: Jan 15, 2027          │
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │ USAGE                                                                 │  │
│  │ Seats:     ████████████░░░░  12 / 15 used                              │  │
│  │ AI Interviews: ██████░░░░░░  156 / 500 this month                     │  │
│  │ Storage:   ███░░░░░░░░░░░░  2.1 / 10 GB                              │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                              │
│  ┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐              │
│  │ Starter         │ │ Professional ★  │ │ Enterprise      │              │
│  │ $49/user/mo     │ │ $89/user/mo     │ │ Custom pricing  │              │
│  │ 5 seats         │ │ 15 seats        │ │ Unlimited       │              │
│  │ Basic screening │ │ AI interviews   │ │ SSO + API       │              │
│  │ [Current: —]    │ │ [Current Plan]  │ │ [Contact Sales] │              │
│  └─────────────────┘ └─────────────────┘ └─────────────────┘              │
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │ INVOICE HISTORY                                    [Download All]     │  │
│  │ INV-2026-0042  │  May 15, 2026  │  $1,068.00  │  Paid  │  [PDF]     │  │
│  │ INV-2026-0038  │  Apr 15, 2026  │  $1,068.00  │  Paid  │  [PDF]     │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                              │
│  Payment Method: Visa •••• 4242    [Update Payment Method]                  │
└────────────────────────────────────────────────────────────────────────────┘
```

### 11.3 Components

| Component | Type | Properties |
|-----------|------|------------|
| Plan Summary | Header card | Plan name, status badge, renewal date |
| Usage Meters | Progress bars | Seats, AI interviews, storage vs. limits |
| Plan Comparison | 3-column cards | Starter, Professional, Enterprise tiers |
| Current Plan Badge | Label | Highlighted on active tier card |
| Upgrade CTA | Button per card | Upgrade, Contact Sales, Downgrade |
| Invoice Table | Data table | Invoice #, date, amount, status, PDF link |
| Payment Method | Card display | Last 4 digits, expiry; update link |
| Upgrade Modal | Dialog | Prorated charge preview (FR-BIL-006) |
| Trial Banner | Alert bar | Shown during 14-day trial (FR-BIL-009) |

### 11.4 Interactions

| Action | Trigger | Behavior |
|--------|---------|----------|
| Upgrade Plan | Click CTA | Show prorated pricing → Stripe checkout |
| Downgrade Plan | Click CTA | Confirm at end of cycle; feature warning |
| Update Payment | Click link | Stripe payment method portal |
| Download Invoice | Click PDF | Generate/download invoice PDF |
| Seat Limit Warning | 90% usage | Amber banner: "3 seats remaining" |
| Seat Limit Block | 100% usage | Block new user creation (BUS-007) |
| Trial Expiry | Day 12 of trial | Banner: "Trial ends in 2 days" |

### 11.5 UX Notes

- Prorated charges displayed before upgrade confirmation (FR-BIL-006)
- Failed payment shows red banner with "Update payment" CTA (FR-BIL-005)
- Enterprise tier links to sales contact form, not self-serve checkout
- Finance role has read-only access; Company Admin has full management

### 11.6 Responsive Behavior

| Breakpoint | Layout Change |
|------------|---------------|
| Desktop | 3-column plan cards; side-by-side usage meters |
| Tablet | 3-column cards shrink; stacked usage meters |
| Mobile | Single-column plan cards (swipeable carousel); stacked invoices |

---

## 12. Cross-Screen Navigation Map

```
Login ──→ Dashboard ──┬──→ Candidate List ──→ Candidate Details
                      ├──→ Reports
                      ├──→ Settings ──→ Subscription Management
                      └──→ AI Interview (candidate-facing)

Registration ──→ Email Verify ──→ Dashboard (or AI Interview)
```

---

## 13. Figma Handoff Checklist

| Item | Status | Notes |
|------|--------|-------|
| Design tokens defined | ✅ | Section 2 |
| All 9 screens specified | ✅ | Sections 3–11 |
| Component inventory per screen | ✅ | Tables in each section |
| Interaction states documented | ✅ | Hover, loading, error, empty |
| Responsive breakpoints defined | ✅ | Desktop, tablet, mobile |
| Accessibility requirements | ✅ | WCAG 2.1 AA, focus order, ARIA |
| Role-based visibility noted | ✅ | Per-screen UX notes |
| Requirements traceability | ✅ | FR/BR references per screen |

---

## 14. Document Approval

| Role | Name | Date | Signature |
|------|------|------|-----------|
| UX Lead | _________________ | ___/___/2026 | _________ |
| Product Owner | _________________ | ___/___/2026 | _________ |
| Business Analyst | Rohit | 06/08/2026 | _________ |
| Engineering Lead | _________________ | ___/___/2026 | _________ |

---

## 15. Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 06/08/2026 | Rohit | Initial release — 9 screen specifications |

---

*Document Classification: Internal — Design Specification*
