# Jira Traceability Playbook

## Purpose
Define how work items, branches, commits, pull requests, reviews, and release signals must connect so implementation progress can be tracked reliably.

## Why this exists
Progress tracking becomes weak when Jira says one thing, commits say another, and PRs are not linked clearly. This playbook makes progress evidence-based.

## Scope
Applies to:
- stories
- tasks
- subtasks
- bug fixes related to a story
- pull requests
- commits
- release readiness tracking

## Principles
- Jira is the work management source of truth.
- Git and PR activity are execution evidence.
- Progress must be derived from explicit signals, not guesswork.
- Every implementation task must be traceable to code, tests, review, or release action.

## Required linkage rules

### 1. Jira key in branch name
Branch names must include the Jira key.

Examples:
- CHN-1423-add-request-validation
- CHN-1424-update-portfolio-dto
- CHN-1425-add-integration-tests

### 2. Jira key in commit message
Every implementation commit must include the Jira key.

Examples:
- CHN-1423 add request validation for onboarding API
- CHN-1424 update mapper for new advisory flag
- CHN-1425 add negative integration tests for invalid status

### 3. Jira key in PR title
Every PR title must include the primary Jira key.

Examples:
- CHN-1423 Add request validation for onboarding API
- CHN-1424 Update portfolio DTO and mapper

### 4. One task, one primary deliverable
Each Jira task should map to one clear unit of work:
- backend logic
- frontend UI change
- test automation
- migration
- config/release step
- documentation

### 5. Do not mix unrelated Jira keys in one PR
A PR should normally focus on one primary implementation task. Small related fixes are acceptable, but avoid bundling many unrelated tasks into one PR.

### 6. Blocked tasks must say why
If a task is blocked, the Jira issue must contain:
- blocker reason
- owner or dependency
- next expected action

### 7. Done means evidence exists
A task should not be marked Done unless the relevant evidence exists:
- code merged, or
- explicit no-code completion note, or
- test/release/documentation evidence if applicable

## Suggested Jira task structure

### Parent story
Contains:
- business requirement
- acceptance criteria
- high-level scope
- linked docs

### Child tasks / subtasks
Each should contain:
- technical objective
- acceptance criteria for that task
- dependency info if any
- owner
- component label if useful

## Preferred task categories
Use these categories when creating implementation tasks:
- design
- backend
- frontend
- api-contract
- migration
- integration
- testing
- release
- documentation

## Task sizing rules
- smaller than 30 minutes: usually keep inside another task
- ideal: 0.5 to 2 days
- larger than 3 days: split further
- avoid vague tasks like "do backend changes"

## Progress evidence hierarchy
Progress should be inferred using this order of confidence:

1. Jira workflow status
2. PR status
3. Commit activity
4. Review outcomes
5. Test evidence
6. Deployment/release evidence

## Task state definitions

### Not Started
- Jira task exists
- no meaningful commits
- no PR
- status still To Do / Open

### In Progress
One or more of:
- Jira moved to In Progress
- meaningful commits linked to issue key
- branch exists and work has started

### In Review
- PR opened
- review requested or comments active
- code packaged for review

### Ready to Complete
- PR approved or close to merge
- major review concerns addressed
- tests are present

### Done in Code
- PR merged

### Done End-to-End
- PR merged
- Jira marked Done
- any required tests/release checks completed

### Blocked
- explicit blocker noted
- dependency or issue prevents progress

## Anti-patterns
- commit without Jira key
- PR without Jira key
- multiple unrelated tasks in one branch
- marking Done before merge
- leaving blocked tasks in In Progress without comments
- using commit count as completion percentage

## Human override
Leads can override computed status when:
- work was descoped
- task completed outside code
- hotfix merged differently
- dependency was restructured
- operational reality differs from system signals

## Minimum fields for tracking
Each task should expose or allow derivation of:
- issue key
- summary
- assignee
- status
- created date
- updated date
- priority
- blocker note if any
- related PRs
- related commits
- review state
- merged state

## Ownership
- engineering lead owns this playbook
- developers must follow branch/commit/PR rules
- reviewers must enforce traceability during PR review

## Review cadence
Review monthly or after any tracking failure or release incident.