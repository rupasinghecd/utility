# Jira Story Template

## Purpose
Provide a standard Jira story structure so requirements are clear, assessable, and usable by engineers, reviewers, and AI workflows across the SDLC.

## When to Use
Use this template for:
- feature stories
- change requests
- API enhancements
- onboarding / profile / workflow changes
- integration changes
- validation / audit / entitlement changes
- bugs that require implementation and design thinking

---

# Story Title
Use a concise, outcome-focused title.

Examples:
- Add advisory-profile validation during onboarding update
- Capture field-level audit for client profile status changes
- Reject invalid portfolio preference combinations in onboarding API

---

# 1. Business Objective
Describe why this change is needed.

Prompt:
- What problem are we solving?
- What business, operational, control, or customer outcome is expected?
- Why is this needed now?

Example:
Improve onboarding data quality and auditability by validating advisory-profile updates and recording field-level audit context for advisory-profile changes initiated by RM users.

---

# 2. User / Actor
Who is affected or who performs the action?

Examples:
- RM user
- Operations user
- Internal service
- Downstream integration consumer
- End customer

---

# 3. In Scope
List exactly what is included.

Examples:
- onboarding update API validation
- advisory-profile field checks
- audit capture for successful advisory changes
- standard API validation error handling

---

# 4. Out of Scope
List what is explicitly excluded.

Examples:
- approval workflow redesign
- historical data backfill
- UI redesign
- changes to unrelated profile fields

---

# 5. Functional Requirements
List the required behavior in numbered form.

Template:
1. System must...
2. System must...
3. System must...

Example:
1. System must reject onboarding update requests when advisory-profile mandatory fields are missing.
2. System must reject invalid advisory-profile status combinations.
3. System must record audit details for successful advisory-profile changes.

---

# 6. Acceptance Criteria
Write testable and observable criteria.

Template:
1. Given ...
   When ...
   Then ...

2. Given ...
   When ...
   Then ...

Example:
1. Given an onboarding update request with missing advisory-profile mandatory fields,
   when the API is called,
   then the request is rejected with the standard validation error response.

2. Given a valid advisory-profile update,
   when the onboarding update succeeds,
   then an audit record is stored with actor, timestamp, field name, before value, and after value.

3. Given an existing valid consumer request,
   when no advisory-profile validation rule is violated,
   then the current flow continues without regression.

---

# 7. Business Rules
List specific rules that drive validation or behavior.

Examples:
- advisory-profile status A cannot be paired with risk profile B
- field X is mandatory only when customer segment is Y
- RM can edit only during onboarding status PENDING

If none are known, write:
- No additional business rules currently identified

---

# 8. Impacted Systems
List all known systems, apps, services, or interfaces affected.

Examples:
- onboarding API service
- RM frontend / MFE
- audit persistence service
- Kafka event publisher
- downstream profile service
- document service

If unknown, state:
- Impacted systems to be confirmed

---

# 9. API / Contract Impact
Describe any request, response, or event changes.

Prompt:
- are new fields added?
- are validations changed?
- does error behavior change?
- are downstream consumers impacted?

Template:
- Request impact:
- Response impact:
- Backward compatibility note:
- Consumer impact:

---

# 10. DB / Schema Impact
Describe whether DB or storage changes are expected.

Template:
- Schema change required: Yes / No / Unknown
- Migration required: Yes / No / Unknown
- Data backfill required: Yes / No / Unknown
- Notes:

---

# 11. Event / Integration Impact
Describe upstream/downstream impacts.

Template:
- Event payload impact:
- Consumer impact:
- External service impact:
- Ordering / idempotency concerns:
- Notes:

---

# 12. Security / Entitlement Impact
Describe access control implications.

Prompt:
- who is allowed to perform this action?
- does entitlement logic change?
- are approval rules affected?

Template:
- Entitlement change: Yes / No / Unknown
- Roles affected:
- Approval flow impact:
- Notes:

---

# 13. Data Classification
State the sensitivity of the data involved.

Examples:
- Internal
- Confidential
- Restricted customer data

Prompt:
- does this involve PII?
- does this involve documents/files?
- are masking/redaction rules needed?

Template:
- Data classification:
- Sensitive fields involved:
- Masking/redaction notes:

---

# 14. Audit / Compliance Requirements
State what must be auditable.

Prompt:
- does the action require audit?
- do before/after values need to be captured?
- are file actions/status changes auditable?

Template:
- Audit required: Yes / No / Unknown
- Audit events required:
- Before/after capture needed: Yes / No / Unknown
- Compliance notes:

---

# 15. Validation Notes
Describe known validation expectations.

Examples:
- mandatory fields
- conditional validation
- cross-field validation
- invalid state combinations

Template:
- Mandatory validations:
- Conditional validations:
- Error response expectation:

---

# 16. Test Notes
Describe what should be tested.

Template:
- Happy path:
- Negative path:
- Edge cases:
- Contract/regression concerns:
- Test data considerations:

---

# 17. Rollout Notes
Describe release expectations.

Template:
- Feature toggle needed: Yes / No / Unknown
- Config dependency:
- Environment sequencing:
- Deployment constraint:
- Notes:

---

# 18. Rollback Notes
Describe rollback expectations.

Template:
- Rollback possible: Yes / No / Unknown
- Constraints:
- Migration rollback concern:
- Operational fallback:

---

# 19. Dependencies
List dependencies explicitly.

Examples:
- waiting for downstream API confirmation
- requires DB migration
- requires risk/compliance sign-off
- depends on audit table update

If none are known, write:
- No known dependencies

---

# 20. Assumptions
List assumptions clearly.

Examples:
- no entitlement change expected
- schema change will be additive only
- existing error response format remains unchanged

---

# 21. Open Questions
List unresolved points that block or weaken implementation.

Examples:
- are before/after values mandatory for all advisory fields?
- does downstream event payload need to include validation result?
- does this apply only to onboarding update API or all profile update paths?

---

# 22. Owner / Owning Team
Template:
- Product owner:
- Engineering owner:
- Owning team:

---

# 23. Linked Artifacts
Template:
- Epic:
- PRD Link:
- Design Note Link:
- Related Jira items:
- Reference documents:

---

# 24. Definition of Ready Checklist
Mark each item before moving the story forward.

- [ ] Business objective is clear
- [ ] Scope is bounded
- [ ] Acceptance criteria are testable
- [ ] Impacted systems are known or explicitly unknown
- [ ] Security/entitlement impact is considered
- [ ] Audit/compliance impact is considered
- [ ] API/DB/integration impact is noted
- [ ] Test expectations are visible
- [ ] Rollout/rollback notes are present for non-trivial changes
- [ ] Dependencies and open questions are listed

---

# Story Writing Rules

## Good Story Characteristics
A good story is:
- clear
- bounded
- testable
- implementation-friendly
- risk-aware
- traceable

## Avoid
- vague goals like "improve process"
- bundling multiple unrelated deliverables
- missing acceptance criteria
- hiding risky changes without security/audit notes
- saying "do validation" without stating what validation means
- saying "add audit" without specifying what must be captured

## Minimum Required Fields
At minimum, every story should contain:
- Title
- Business Objective
- In Scope
- Acceptance Criteria
- Impacted Systems
- Dependencies
- Owner / Team

## Required for Sensitive or Non-Trivial Stories
Also include:
- API / Contract Impact
- DB / Schema Impact
- Security / Entitlement Impact
- Data Classification
- Audit / Compliance Requirements
- Rollout Notes
- Rollback Notes
- PRD Link or equivalent

---

# Example Filled Story

## Story Title
Add advisory-profile validation and audit capture during client onboarding update

## Business Objective
Improve onboarding data quality and auditability by validating advisory-profile updates and recording field-level audit context for advisory-profile changes initiated by RM users.

## User / Actor
RM user

## In Scope
- onboarding update API validation for advisory-profile fields
- audit capture for successful advisory-profile changes
- standard validation error response usage

## Out of Scope
- non-advisory profile updates
- approval flow redesign
- historical backfill

## Functional Requirements
1. System must reject requests with missing advisory-profile mandatory fields.
2. System must reject invalid advisory-profile status combinations.
3. System must record audit details for successful advisory-profile changes.

## Acceptance Criteria
1. Given a request missing mandatory advisory-profile fields, when the API is called, then the request is rejected using the standard validation error format.
2. Given a valid advisory-profile update, when onboarding update succeeds, then an audit record is stored with actor, timestamp, onboarding reference, changed field names, before value, and after value.
3. Given existing valid consumers, when advisory validation passes, then no existing flow is broken.

## Impacted Systems
- onboarding API service
- audit persistence service
- RM channel consumer

## API / Contract Impact
- Request impact: validation behavior changes for advisory-profile fields
- Response impact: existing validation error format reused
- Backward compatibility note: no response schema change expected
- Consumer impact: consumers must handle stricter validation outcomes

## DB / Schema Impact
- Schema change required: Unknown
- Migration required: Unknown
- Notes: depends on audit storage approach

## Security / Entitlement Impact
- Entitlement change: No
- Roles affected: RM users only
- Notes: existing authorization model assumed unchanged

## Data Classification
- Data classification: Confidential customer data
- Sensitive fields involved: advisory-profile details

## Audit / Compliance Requirements
- Audit required: Yes
- Before/after capture needed: Yes
- Compliance notes: advisory-profile changes must be traceable

## Test Notes
- Happy path: valid advisory update succeeds
- Negative path: invalid field combinations rejected
- Edge cases: missing mandatory field, invalid status combination

## Rollout Notes
- Feature toggle needed: No
- Deployment constraint: DB migration first if audit schema changes are required

## Rollback Notes
- Rollback possible: Yes, if schema changes are additive only

## Dependencies
- audit persistence approach confirmation
- downstream consumer validation if contract behavior changes

## Assumptions
- entitlement model unchanged
- existing validation error response format reused

## Open Questions
- does before/after capture apply to all advisory fields?
- is DB migration needed or can existing audit structure be reused?