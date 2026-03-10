---
title: Assess Story Quality
description: Assess a Jira story against the story-quality policy and decide whether it is ready for the next SDLC stage.
---

# Assess Story Quality Workflow

## Goal
Evaluate whether a Jira story is clear, complete, implementable, testable, and safe enough to proceed.

## Inputs expected
- Jira story key
- Jira issue content
- linked comments or linked docs if available
- playbooks/story-quality-policy.md

## Steps
1. Read the Jira story and linked context.
2. Evaluate the story against the policy dimensions:
   - business clarity
   - scope clarity
   - acceptance criteria quality
   - engineering implementability
   - risk/compliance readiness
   - testability/release readiness
3. Score each dimension from 0 to 5.
4. check blocker conditions.
5. determine overall classification.
6. list missing items, ambiguities, and risks.
7. recommend one of:
   - ready
   - ready with warnings
   - revise
   - split
   - escalate

## Output format

### Story Summary
### Dimension Scores
### Blockers
### Missing Information
### Risks
### Recommendation

## Constraints
- do not invent facts not present in Jira or linked artifacts
- separate assumptions from confirmed details
- if the story bundles unrelated items, recommend splitting