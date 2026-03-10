---
title: Track Progress
description: Track implementation progress for a Jira story by evaluating Jira tasks, commits, pull requests, reviews, and blockers.
---

# Track Progress Workflow

## Goal
Provide an evidence-based progress summary for a story or epic.

## Inputs expected
- parent Jira story key or epic key
- child tasks/subtasks from Jira
- linked commit / PR / review evidence if available

## Steps

### 1. Fetch work items
Collect:
- parent item
- child tasks
- subtasks if any

### 2. For each task, collect evidence
Gather:
- Jira status
- assignee
- updated time
- blocker signals
- linked commits
- PR state
- review state
- merge state
- test evidence if visible

### 3. Classify each task
Classify as one of:
- Not Started
- In Progress
- In Review
- Done in Code
- Done End-to-End
- Blocked
- Needs Human Review

### 4. Detect health
Classify health as:
- Green
- Amber
- Red

### 5. Compute overall progress
Use task-level weighted progress and summarize:
- number complete
- number active
- number blocked
- number not started
- key risks
- recommended next actions

## Output format

### Overall summary
- story key
- overall progress percent
- overall health
- short narrative

### Progress by task
For each task include:
- key
- title
- status
- derived progress percent
- health
- evidence summary
- blockers or risks

### Blockers
List blocked or stale tasks clearly.

### Recommended next actions
List the next highest-value actions.

## Classification rules

### Not Started
- no meaningful execution evidence
- Jira still open / to do

### In Progress
- task moved to in progress, or
- meaningful commits exist, but no active review yet

### In Review
- PR opened or review active

### Done in Code
- PR merged, but release or Jira completion still pending

### Done End-to-End
- PR merged
- Jira marked done
- required validation evidence present

### Blocked
- blocked label/status/comment, or
- explicit dependency preventing completion

### Needs Human Review
- conflicting evidence
- descoped work
- special release handling
- no-code operational task

## Constraints
- do not estimate progress from commit count alone
- do not assume Jira status is accurate without other signals
- prefer explicit evidence over inference