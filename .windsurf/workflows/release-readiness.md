---
title: Release Readiness
description: Assess whether a change is ready for release based on implementation completion, validation, dependency readiness, and rollback preparedness.
---

# Release Readiness Workflow

## Goal
Determine whether a story/change is ready for production release.

## Inputs expected
- parent Jira story key
- implementation tasks and statuses
- validation evidence if available
- release notes/config details if available
- playbooks/release-readiness-policy.md

## Steps
1. review implementation completion status.
2. review test and validation evidence.
3. review deployment/config dependencies.
4. review rollback preparedness.
5. review operational readiness and dependency alignment.
6. classify readiness:
   - Ready for Release
   - Ready with Warnings
   - Not Ready
   - Needs Human Decision
7. produce a release summary.

## Output format

### Release Summary
### Readiness Classification
### Completed Checks
### Open Risks / Blockers
### Deployment Steps
### Rollback Steps
### Post-Release Validation Checklist

## Constraints
- do not mark ready if critical blockers remain
- call out missing rollback or missing validation clearly
- use “Needs Human Decision” when facts are conflicting or incomplete