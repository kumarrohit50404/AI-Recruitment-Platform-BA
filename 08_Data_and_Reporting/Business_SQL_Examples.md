# Business SQL Examples
## HireFlow AI | Portfolio Case Study

**Author:** Rohit Kumar | Business Analyst Portfolio Project

**Purpose:** Sample SQL queries used to **validate reporting requirements and KPI logic** — not database administration.

---

## Why a BA Uses SQL

- Confirm KPI formulas match available data
- Validate funnel and pipeline reports before UAT
- Answer stakeholder questions with sample data checks

These examples span basic pipeline queries through KPI validation.

---

## 2. Basic Examples (Pipeline Visibility)

### Example 1 — Applications by pipeline stage
*Validates: Hiring Pipeline Funnel (RR-001)*

```sql
SELECT stage, COUNT(*) AS application_count
FROM hireflow.applications
GROUP BY stage
ORDER BY application_count DESC;
```

### Example 2 — Applications with job titles
*Validates: Recruiter requisition view*

```sql
SELECT a.application_id, j.title AS job_title, a.stage, a.applied_at
FROM hireflow.applications a
JOIN hireflow.jobs j ON a.job_id = j.job_id
ORDER BY a.applied_at DESC;
```

### Example 3 — Open requisitions
*Validates: Open Requisition Aging (RR-014)*

```sql
SELECT job_id, title, department, published_at
FROM hireflow.jobs
WHERE status = 'OPEN'
ORDER BY published_at DESC;
```

---

## 3. Intermediate Examples (KPI Validation)

### Example 4 — Average AI match score by job
*Validates: AI Screening Accuracy (KPI-018)*

```sql
SELECT j.title, ROUND(AVG(a.ai_match_score), 2) AS avg_ai_score,
       COUNT(a.application_id) AS total_applications
FROM hireflow.jobs j
JOIN hireflow.applications a ON j.job_id = a.job_id
WHERE a.ai_match_score IS NOT NULL
GROUP BY j.job_id, j.title
ORDER BY avg_ai_score DESC;
```

### Example 5 — Offer acceptance rate
*Validates: Offer Acceptance Rate (KPI-011)*

```sql
SELECT COUNT(*) FILTER (WHERE status = 'SENT') AS offers_sent,
       COUNT(*) FILTER (WHERE status = 'ACCEPTED') AS offers_accepted,
       ROUND(100.0 * COUNT(*) FILTER (WHERE status = 'ACCEPTED') /
             NULLIF(COUNT(*) FILTER (WHERE status IN ('SENT','ACCEPTED','DECLINED')), 0), 2)
             AS acceptance_rate_pct
FROM hireflow.offers;
```

### Example 6 — Recruiter workload
*Validates: Recruiter Performance (RR-004)*

```sql
SELECT u.first_name || ' ' || u.last_name AS recruiter,
       COUNT(a.application_id) AS active_applications
FROM hireflow.applications a
JOIN hireflow.users u ON a.assigned_recruiter_id = u.user_id
WHERE a.stage NOT IN ('HIRED', 'REJECTED')
GROUP BY u.user_id, u.first_name, u.last_name
ORDER BY active_applications DESC;
```

### Example 7 — Monthly application trend
*Validates: Monthly Hiring Trend (KPI reporting)*

```sql
SELECT TO_CHAR(applied_at, 'YYYY-MM') AS application_month,
       COUNT(*) AS applications_received
FROM hireflow.applications
GROUP BY TO_CHAR(applied_at, 'YYYY-MM')
ORDER BY application_month DESC;
```

---

## 4. Advanced Examples (Executive Reporting)

### Example 8 — Time-to-hire by department
*Validates: Time-to-Hire (KPI-006, RR-002)*

```sql
SELECT j.department,
       ROUND(AVG(EXTRACT(DAY FROM a.stage_changed_at - a.applied_at)), 1) AS avg_days_to_hire
FROM hireflow.applications a
JOIN hireflow.jobs j ON a.job_id = j.job_id
WHERE a.stage = 'HIRED'
GROUP BY j.department
ORDER BY avg_days_to_hire;
```

### Example 9 — Interview-to-offer conversion (CTE)
*Validates: Pipeline funnel conversion metrics*

```sql
WITH interview_completed AS (
    SELECT a.application_id, j.department
    FROM hireflow.interviews i
    JOIN hireflow.applications a ON i.application_id = a.application_id
    JOIN hireflow.jobs j ON a.job_id = j.job_id
    WHERE i.interview_type = 'PANEL' AND i.status = 'COMPLETED'
),
offers_made AS (
    SELECT a.application_id FROM hireflow.offers o
    JOIN hireflow.applications a ON o.application_id = a.application_id
    WHERE o.status IN ('SENT', 'ACCEPTED', 'DECLINED')
)
SELECT ic.department,
       COUNT(DISTINCT ic.application_id) AS interviews_completed,
       COUNT(DISTINCT om.application_id) AS offers_made,
       ROUND(100.0 * COUNT(DISTINCT om.application_id) /
             NULLIF(COUNT(DISTINCT ic.application_id), 0), 2) AS conversion_rate
FROM interview_completed ic
LEFT JOIN offers_made om ON ic.application_id = om.application_id
GROUP BY ic.department;
```

### Example 10 — Executive KPI summary
*Validates: Executive Dashboard (BR-031, RR-001)*

```sql
-- Simplified: time-to-hire and offer acceptance in one result set
SELECT 'Time-to-Hire (days)' AS kpi,
       ROUND(AVG(EXTRACT(DAY FROM stage_changed_at - applied_at)), 0) AS value
FROM hireflow.applications WHERE stage = 'HIRED'
UNION ALL
SELECT 'Offer Acceptance Rate (%)',
       ROUND(100.0 * COUNT(*) FILTER (WHERE status = 'ACCEPTED') /
             NULLIF(COUNT(*) FILTER (WHERE status IN ('ACCEPTED','DECLINED')), 0), 0)
FROM hireflow.offers;
```

---

## 5. BA Usage in Interviews

| Interview Question | Show Example |
|--------------------|--------------|
| "How do you validate a KPI?" | Example 5 or 10 |
| "How do you analyze hiring funnel?" | Example 1 or 9 |
| "Can you work with data?" | Examples 4, 6, 8 |

---

*12 curated examples | Full 150-query library archived for depth-on-request*
