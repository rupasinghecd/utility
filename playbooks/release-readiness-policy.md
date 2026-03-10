# Release Readiness Policy

## Purpose
Define how a change is assessed before release so that production rollout is controlled, observable, and reversible where needed.

## When to Use
Use for:
- any production-bound implementation
- changes with config, migration, integration, security, or consumer impact
- changes requiring staged rollout, validation, or rollback planning

## Release Readiness Dimensions

### 1. Functional Completeness
Check whether:
- implementation scope is complete
- required subtasks are complete
- critical acceptance criteria are met

### 2. Test Evidence
Check whether:
- required tests exist
- critical paths were validated
- negative paths were considered where relevant
- regression risks were reviewed

### 3. Deployment Readiness
Check whether:
- config changes are known
- infra/runtime dependencies are known
- migration sequencing is understood
- environment-specific needs are documented

### 4. Rollback Readiness
Check whether:
- rollback path exists
- fallback behavior is known
- irreversible changes are called out
- emergency actions are documented where needed

### 5. Operational Readiness
Check whether:
- logging/metrics/monitoring are adequate
- support teams know what to verify
- expected failure modes are understood
- post-release checks are defined

### 6. Consumer / Dependency Readiness
Check whether:
- downstream or upstream impacts are known
- dependent teams are aligned
- contract or compatibility implications are handled

## Output States
- Ready for Release
- Ready with Warnings
- Not Ready
- Needs Human Decision

## Blocker Conditions
A change is not ready if:
- critical implementation tasks are incomplete
- no meaningful validation evidence exists
- release dependencies are unknown
- rollback is undefined for a high-risk change
- major open blockers remain unresolved

## Required Release Output
The release-readiness workflow should produce:
- readiness classification
- unresolved blockers
- deployment steps
- rollback steps
- post-release validation checklist
- operational watch items

## Review Cadence
Use before production release and update after incidents/postmortems.