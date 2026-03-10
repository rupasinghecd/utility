---
title: Create Implementation Tasks
description: Break a Jira story into implementation tasks with acceptance criteria, dependencies, and delivery streams.
---

# Create Implementation Tasks Workflow

## Goal
Convert one Jira story into a practical implementation task list that can be created in Jira.

## Inputs expected
- parent Jira story key
- story description
- acceptance criteria
- linked product/design context if available
- impacted systems or modules if known

## What to optimize for
- low-risk delivery
- clear ownership
- traceability
- reviewable work units
- realistic task sizes

## Steps

### 1. Understand the story
Summarize:
- business goal
- technical impact
- non-functional expectations
- assumptions and gaps

### 2. Identify delivery streams
Check whether the story affects:
- design / analysis
- backend
- frontend
- api contract
- db / migration
- integration / events
- testing
- release / config
- documentation

### 3. Split work into executable tasks
Create tasks only when they are:
- assignable
- testable or reviewable
- traceable to a concrete outcome
- appropriately sized

### 4. Add acceptance criteria for each task
Each task must state:
- what must be implemented
- what completion means
- any exclusions
- any dependency

### 5. Mark dependency order
Classify each task as:
- prerequisite
- parallel
- follow-up

### 6. Flag risk
For each task, mention if it has:
- backward compatibility risk
- security sensitivity
- migration/release risk
- cross-team dependency

## Output format

### Story understanding
- short summary
- assumptions
- open questions

### Proposed tasks
For each task provide:
- title
- type
- summary
- acceptance criteria
- dependency classification
- risk notes
- suggested owner role

### Recommended creation order
List tasks in dependency order.

## Task title conventions
Prefer titles like:
- Add request validation for onboarding API
- Update portfolio summary DTO and mapper
- Add Flyway migration for audit field
- Add negative integration tests for invalid status
- Prepare release validation checklist

Avoid titles like:
- backend work
- testing
- complete feature
- fixes

## Constraints
- do not create vague tasks
- do not create overly tiny tasks unless required for ownership separation
- do not create one large task that hides multiple streams
- do not invent unsupported business scope