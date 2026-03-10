---
title: Story Analysis
description: Analyze a story or requirement before coding.
---

# Story Analysis Workflow

## Goal
Understand the requirement fully before implementation starts.

## Inputs expected
- Jira story, ticket, or requirement text
- linked design notes if available
- impacted files or modules if already known
- any relevant product or SDLC playbooks

## Steps
1. Summarize the business need in simple terms.
2. Extract functional requirements and non-functional expectations.
3. Identify ambiguity, missing acceptance criteria, and dependencies.
4. List impacted systems, services, modules, APIs, DB objects, configs, and tests.
5. Identify risks:
   - backward compatibility
   - security
   - performance
   - observability
   - release risk
6. Propose a lowest-risk implementation approach.
7. Suggest a validation and test approach.
8. If information is insufficient, list the exact questions that need answers.

## Output format
Return the response under these headings:

### Requirement understanding
### Impacted areas
### Assumptions / missing details
### Risks
### Proposed implementation approach
### Testing approach
### Questions for clarification

## Constraints
- Do not start coding.
- Do not invent business rules not present in the requirement or playbooks.
- Prefer an incremental approach over a broad redesign.