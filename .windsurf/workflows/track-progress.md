---
title: Track Progress
description: Track execution progress for a Jira story using Jira tasks plus Bitbucket commit and PR evidence.
---

# Track Progress Workflow

## Goal
Provide an evidence-based view of story progress.

## Inputs expected
- parent Jira story key
- child tasks/subtasks from Jira
- commit/PR evidence from Bitbucket
- playbooks/jira-traceability-playbook.md

## Steps
1. fetch child tasks from Jira.
2. for each task collect:
   - Jira status
   - assignee
   - updated time
   - blocker signals
   - commits linked by Jira key
   - PR state
   - merge status
   - review signals if visible
3. classify each task:
   - Not Started
   - In Progress
   - In Review
   - Done in Code
   - Done End-to-End
   - Blocked
   - Needs Human Review
4. derive task health:
   - Green
   - Amber
   - Red
5. compute overall progress.
6. identify blockers, stale work, and next recommended actions.

## Output format

### Overall Summary
- story key
- overall progress
- overall health
- narrative summary

### Progress by Task
For each task:
- key
- title
- status
- derived state
- progress percent
- health
- evidence summary
- blocker or risk note

### Blockers
### Recommended Next Actions

## Constraints
- do not use commit count alone as progress
- do not trust Jira status alone if evidence conflicts
- prefer explicit evidence over optimistic inference