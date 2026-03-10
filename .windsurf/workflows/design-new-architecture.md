---
title: Design New Architecture
description: Decide whether a change requires a new microservice, new MFE, or new bounded architectural slice, and produce an architecture decision artifact.
---

# Design New Architecture Workflow

## Goal
Determine whether existing systems can absorb the requested change or whether a new microservice, new MFE, or both should be introduced.

## Inputs expected
- Jira story key
- story details
- PRD if available
- impact analysis if available
- playbooks/architecture/new-system-design-policy.md
- playbooks/architecture/architecture-decision-template.md
- existing architecture maps/catalogs if available

## Steps

### 1. Understand the problem
Summarize:
- business problem
- capability required
- user journey involved
- technical shape of the change

### 2. Assess existing ownership
Check whether an existing service or MFE clearly owns the capability.
State:
- existing systems that could absorb the change
- why they are sufficient or insufficient

### 3. Evaluate architecture options
Compare:
- extend existing service/MFE
- bounded module in existing repo/system
- create new microservice
- create new MFE
- create both

### 4. Decide on new-system need
State whether the recommendation is:
- no new system
- new microservice
- new MFE
- both

### 5. Define boundaries
If a new system is recommended, define:
- purpose
- ownership
- in-scope responsibility
- out-of-scope responsibility
- API/UI boundaries
- data ownership
- integration points

### 6. Define enterprise considerations
Explicitly assess:
- security / entitlement
- audit / compliance
- observability / supportability
- rollout / rollback implications

### 7. Produce architecture decision
Populate the architecture decision template.

## Output format
Return:

### Problem Summary
### Existing-System Assessment
### Options Considered
### Recommendation
### Proposed Boundaries
### Risks and Consequences
### Architecture Decision Draft

## Constraints
- do not create a new system by default
- justify the boundary explicitly
- prefer clear ownership over fashionable decomposition
- distinguish facts from assumptions