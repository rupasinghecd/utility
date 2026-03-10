---
title: Generate New MS MFE Scaffold Plan
description: Produce a standardized scaffold and setup plan for a newly approved microservice, MFE, or both.
---

# Generate New MS MFE Scaffold Plan Workflow

## Goal
Create a practical setup plan for a newly approved system without over-generating speculative code.

## Inputs expected
- approved architecture decision
- playbooks/architecture/microservice-template.md
- playbooks/architecture/mfe-template.md
- playbooks/architecture/system-integration-checklist.md
- backend/AGENTS.md
- frontend/AGENTS.md if applicable

## Steps

### 1. Read the approved architecture decision
Identify:
- whether the change includes a new microservice, new MFE, or both
- required ownership and integrations
- delivery constraints

### 2. Generate microservice scaffold plan if applicable
Produce:
- repo/module name
- package structure
- endpoint namespace
- DTO/validation/service/repository structure
- config placeholders
- migration baseline
- audit/security placeholders
- observability placeholders
- test structure

### 3. Generate MFE scaffold plan if applicable
Produce:
- repo/module name
- route ownership
- shell registration needs
- page/component structure
- api client structure
- hooks/store layout
- entitlement/guard integration points
- error/loading handling structure
- test structure

### 4. Identify platform/bootstrap needs
List:
- CI/CD
- secrets/config placeholders
- environment variables
- registration or deployment steps
- shared library dependencies

### 5. Check integration checklist
Ensure architecture and runtime concerns are not missed.

### 6. Produce setup waves
Group work into:
- setup/bootstrap
- contracts/foundations
- functional implementation
- readiness/release

## Output format

### Summary
### New Microservice Scaffold Plan
### New MFE Scaffold Plan
### Platform / Integration Needs
### Delivery Waves
### Open Questions

## Constraints
- do not generate speculative advanced platform code
- optimize for a minimal, controlled first version
- align with AGENTS and templates