---
title: Create Implementation Tasks
description: Break a story or implementation plan into assignable Jira tasks that support execution and progress tracking.
---

# Create Implementation Tasks Workflow

## Goal
Create a practical task list from the story and implementation plan.

## Inputs expected
- Jira story key
- implementation plan
- playbooks/task-decomposition-policy.md
- playbooks/jira-traceability-playbook.md

## Steps
1. review story and implementation plan.
2. identify workstreams:
   - backend
   - frontend
   - integration
   - testing
   - release
   - documentation
3. break work into task-sized deliverables.
4. add acceptance criteria for each task.
5. assign dependency classification:
   - prerequisite
   - parallel
   - follow-up
6. identify risk notes and likely owner role.
7. return the proposed task list in recommended creation order.

## Output format

### Story Understanding
### Proposed Tasks
For each task:
- title
- category
- objective
- acceptance criteria
- dependency classification
- risk notes
- suggested owner role

### Recommended Creation Order

## Constraints
- do not create vague tasks
- do not create very tiny administrative tasks unless needed
- do not create one oversized task hiding multiple streams