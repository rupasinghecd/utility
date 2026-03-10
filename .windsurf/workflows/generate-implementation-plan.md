---
title: Generate Implementation Plan
description: Generate an engineering implementation plan from the Jira story, PRD, and related context.
---

# Generate Implementation Plan Workflow

## Goal
Convert the approved requirement into a practical engineering plan.

## Inputs expected
- Jira story key
- Jira issue details
- PRD if available
- linked design docs if available
- playbooks/implementation-plan-template.md

## Steps
1. summarize the requirement in engineering terms.
2. identify in-scope and out-of-scope implementation.
3. identify likely impacted components and delivery streams.
4. propose the lowest-risk implementation approach aligned to existing patterns.
5. define testing strategy.
6. define release and rollback considerations.
7. list assumptions, open questions, and risks.
8. propose a recommended task breakdown.

## Output format
Return a complete implementation plan using the template structure.

## Constraints
- prefer existing patterns and minimal safe change
- separate confirmed impact from likely impact
- call out risk and compatibility concerns clearly