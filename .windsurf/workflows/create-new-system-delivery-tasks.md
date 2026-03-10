---
title: Create New System Delivery Tasks
description: Create sequenced Jira tasks for delivering a newly approved microservice, MFE, or architectural slice.
---

# Create New System Delivery Tasks Workflow

## Goal
Translate an approved new-system design and scaffold plan into an execution-ready Jira task list.

## Inputs expected
- approved architecture decision
- scaffold plan
- impact analysis
- playbooks/sdlc/task-decomposition-policy.md
- playbooks/architecture/system-integration-checklist.md
- playbooks/sdlc/jira-traceability-playbook.md

## Steps

### 1. Read the approved design and scaffold plan
Identify:
- system types being introduced
- dependencies
- delivery risks
- integration points

### 2. Create setup/bootstrap tasks
Examples:
- create repo/module
- register MFE in shell
- set up CI/CD
- define config placeholders
- establish project skeleton

### 3. Create contract/foundation tasks
Examples:
- define API contract
- define DTO/schema/event model
- define migration baseline
- define entitlement model
- define audit/logging model

### 4. Create functional implementation tasks
Examples:
- implement core backend flow
- implement core UI flow
- implement validations
- implement integration adapters
- add tests

### 5. Create readiness tasks
Examples:
- observability setup
- documentation
- rollout checklist
- rollback/fallback checklist
- production verification steps

### 6. Sequence the tasks
Mark each as:
- prerequisite
- parallel
- follow-up

### 7. Add traceability notes
For each task include:
- source system
- source decision section
- source impact item if relevant

## Output format

### Delivery Summary
### Wave 1: Setup / Bootstrap
### Wave 2: Contracts / Foundations
### Wave 3: Functional Implementation
### Wave 4: Readiness / Release

For each task include:
- title
- category
- objective
- acceptance criteria
- dependency classification
- source system
- suggested owner role
- risk notes

## Constraints
- do not collapse all work into one giant task
- do not create noisy micro-tasks without value
- keep the waves clear and reviewable