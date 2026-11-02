# ICI Local 2.0 — dependency register

Updated: 2 November 2026. Based on the supplied implementation plan and Jira screenshots; inferred planning dependencies, not a live Jira audit.

## Reading the links

A → B means A blocks B. In ticket B, choose **is blocked by A**. Dependencies describe integrated completion, not a prohibition on starting parallel work. No ticket is assumed Done.

Confirmed screenshot IDs: ICI2-5–9, ICI2-12–19, ICI2-23–41. SETUP, GRADE, ATTEND, RULES and SO are local aliases; their Jira IDs have not been supplied.

## Required links

| Ticket | Feature | Is blocked by |

|---|---|---|
| ICI2-5 | Database foundation | No feature-specific prerequisite |
| ICI2-6 | Authentication & JWT | ICI2-5 |
| ICI2-7 | Role-based access control | ICI2-6 |
| ICI2-8 | React shell & design system | No feature-specific prerequisite |
| ICI2-9 | User account panel | ICI2-7, ICI2-8 |
| ICI2-12 | Student master record API | ICI2-5 |
| ICI2-13 | Duplicate applicant detection | ICI2-12 |
| ICI2-14 | Enrollment queue & intake | ICI2-12, ICI2-13, ICI2-8 |
| ICI2-15 | Requirement checklist service | ICI2-12 |
| ICI2-16 | Requirement verification screen | ICI2-15, ICI2-8 |
| ICI2-17 | Attendance & enrollment confirmation | ICI2-15 |
| ICI2-18 | Section configuration API | ICI2-5 |
| ICI2-19 | Section allocation workspace | ICI2-18, ICI2-12, ICI2-8 |
| SETUP (Jira ID unconfirmed) | Subjects, years & grading periods | ICI2-5 |
| ICI2-41 | Teacher & adviser assignments | ICI2-18, ICI2-7, SETUP (Jira ID unconfirmed) |
| GRADE (Jira ID unconfirmed) | Grade draft & submission API | ICI2-41, SETUP (Jira ID unconfirmed) |
| ICI2-23 | Advisory section roster | ICI2-19, ICI2-15, ICI2-17, ICI2-41 |
| ICI2-24 | Subject grade encoding grid | ICI2-19, ICI2-41, GRADE (Jira ID unconfirmed) |
| ICI2-25 | Grading period finalization & locks | ICI2-24, SETUP (Jira ID unconfirmed) |
| ICI2-26 | Grade correction requests | ICI2-25 |
| ICI2-27 | Grade correction review & approval | ICI2-26 |
| ICI2-28 | Incomplete grade monitoring | ICI2-24 |
| ICI2-29 | Consolidated academic history | ICI2-24, ICI2-15, ICI2-19 |
| ICI2-30 | Withdrawal clearance workflow | ICI2-12, ICI2-41 |
| ICI2-31 | Dynamic report query engine | ICI2-12, ICI2-18 |
| ICI2-32 | Operational reports & exports | ICI2-31, ICI2-15, ICI2-17 |
| ATTEND (Jira ID unconfirmed) | Daily attendance recording / import | ICI2-12, ICI2-19 |
| RULES (Jira ID unconfirmed) | Honor rules & eligibility | No feature-specific prerequisite |
| SO (Jira ID unconfirmed) | Special Order capture & validation | ICI2-12 |
| ICI2-33 | Guidance at-risk monitoring | ICI2-31, ICI2-24, ICI2-15, ATTEND (Jira ID unconfirmed) |
| ICI2-34 | Honor roll computation | ICI2-24, RULES (Jira ID unconfirmed) |
| ICI2-35 | Official documents: Form 137 / TOR | ICI2-29, ICI2-28, ICI2-30, SO (Jira ID unconfirmed) |
| ICI2-36 | Cashiering reference export | ICI2-12, ICI2-17 |
| ICI2-37 | Legacy student CSV ingestion | ICI2-5 |
| ICI2-38 | Historical grade matrix parser | ICI2-37 |
| ICI2-39 | Spreadsheet cleaning & import | ICI2-37 |
| ICI2-40 | Cutover reconciliation | ICI2-37, ICI2-38, ICI2-39 |
## Conditional and data-model links
| Prerequisite | Dependent | Type | Condition |
|---|---|---|---|
| ICI2-27 | ICI2-28 | conditional | Only if locked INC completion requires registrar approval. |
| ICI2-25 | ICI2-34 | conditional | Required for official finalized honor lists. |
| ICI2-38 | ICI2-35 | conditional | Required for transcripts containing legacy grades. |
| ICI2-12 | ICI2-37 | model | Student model must be finalized; the whole CRUD feature need not be complete. |
| ICI2-24 | ICI2-38 | model | Subject, term and grade model only; grade grid completion is not required. |
| ICI2-18 | ICI2-39 | model | Section target model only. |
| ICI2-15 | ICI2-39 | model | Checklist target model only. |
| ICI2-30 | ICI2-39 | model | Withdrawal target model only. |
## Shared foundations and boundaries
- Database-backed features require their relevant schema. Protected operations require RBAC; screens require the UI shell. Repeated shared links are omitted for readability.
- SETUP: configure subjects, academic years/terms and grading periods, permissions, valid dates and reference integrity.
- GRADE: save/retrieve drafts, validate numeric and INC marks, submit grades, enforce assignment authorization, record audit fields. Integrate period-lock enforcement with ICI2-25 before release; do not create a circular blocker link.
- ATTEND: agree recording/import method, daily statuses, excused/unexcused absence rules and school-day calendar.
- RULES: obtain school approval of weights, rounding, eligibility thresholds, ties, failing/missing/INC handling and verification examples.
- SO: confirm applicability and record ownership with registrar; validate required SO information before document generation.
- ICI2-26: include evidence upload/storage as a subtask, not a separate missing feature if already in scope.
- ICI2-40: building the dashboard can start before imports finish. Final reconciliation needs all imports; decommissioning additionally requires replacement readiness and administrative sign-off.
- ICI2-19 is not automatically blocked by enrollment confirmation; confirm school sectioning policy first.
- Duplicate resolution blocks confirmation only if school policy requires it.
- No actual Jira board changes were made by generating these files.
## Source and review notes
The original pasted plan is unchanged. This register is the updated companion documentation. The active workspace contains the unrelated LogEZ project, so its architecture documents were not modified.
Open index.html locally for the interactive mockup. Its completion checkboxes are local planning simulations, not Jira status updates.