---
title: Estimate Tasks
description: Estimate end-to-end delivery effort using task breakdown, impact analysis, lineage, dependencies, and shared delivery overhead.
---

# Estimate Tasks Workflow

## Goal
Produce realistic end-to-end effort and likely timeline for a story, initiative, new system, or shared library change.

## Inputs expected
- Jira story key or initiative key
- task breakdown
- impact analysis
- implementation plan or architecture decision
- system lineage if available
- playbooks/metrics/task-estimation-playbook.md

## Optional Inputs
- historical similar stories
- current team capacity
- story complexity classification
- release constraints

## Steps

### 1. Understand estimation scope
Summarize:
- work type
- systems involved
- story size
- whether this is existing-system, new-system, or library work

### 2. Review task breakdown
Check whether tasks already cover:
- frontend
- backend
- db
- kafka/messaging
- integration
- testing
- release
- coordination
- audit/security if relevant

If major workstreams appear missing, flag estimation risk.

### 3. Estimate direct task effort
For each task estimate:
- build effort
- local test effort
- task confidence
- dependency mode

### 4. Estimate shared overhead
Estimate once for the overall scope:
- shared testing/regression effort
- release/devops effort
- coordination effort
- risk buffer

### 5. Check dependency and parallelization
Classify tasks as:
- sequential
- parallel
- partially parallel

Then estimate likely timeline separately from total effort.

### 6. Compare with historical work
If historical data exists:
- compare to similar past work
- adjust obvious under/over-estimation
- note any assumptions

### 7. Produce final estimate
Return:
- task estimates
- shared overhead
- total effort
- likely timeline
- confidence level
- key risk drivers

## Output format

### Scope Summary
- story / initiative
- work type
- systems involved
- confidence level

### Task Estimates
For each task:
- title
- category
- direct build effort
- local testing effort
- total task effort
- dependency mode
- confidence
- notes

### Shared Overhead
- shared testing/regression
- release/devops
- coordination
- risk buffer

### Totals
- total task effort
- total shared overhead
- total end-to-end effort
- likely timeline
- estimation confidence

### Key Risk Drivers
- missing workstreams
- unclear dependencies
- new architecture/library factors
- low-confidence impact areas
- release or compatibility constraints

### Recommendation
Examples:
- estimate accepted
- estimate accepted with caution
- split story further
- re-run after impact/task refinement

## Constraints
- do not estimate only coding work
- do not treat effort and duration as the same
- do not duplicate shared overhead across all tasks
- do not hide low confidence; state it explicitly
- if the story is too large, recommend splitting instead of forcing false precision