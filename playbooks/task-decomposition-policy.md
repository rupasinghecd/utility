# Task Decomposition Policy

## Purpose
Define how a story or implementation plan is split into Jira tasks/subtasks that are executable, reviewable, and trackable.

## Objectives
Tasks should be:
- small enough to complete predictably
- large enough to be meaningful
- easy to assign
- easy to review
- traceable to code, testing, or release evidence

## Task Design Principles
- one task should represent one primary deliverable
- avoid mixing unrelated work in the same task
- tasks should align to delivery streams where possible
- dependencies should be visible
- task titles should clearly state the outcome

## Preferred Task Categories
Use one or more of:
- design
- backend
- frontend
- api-contract
- migration
- integration
- testing
- release
- documentation

## Good Task Examples
- Add backend validation for onboarding API
- Update frontend field handling for advisory profile
- Add integration test for invalid account status
- Prepare release verification checklist
- Add Flyway migration for audit context column

## Bad Task Examples
- Backend work
- Complete feature
- Testing
- Fix things
- Review changes

## Sizing Guidelines
- under 30 minutes: usually do not create separate Jira task
- 0.5 to 2 days: ideal
- above 3 days: split further unless there is a strong reason not to

## Dependency Classification
Every task should be marked as one of:
- prerequisite
- parallel
- follow-up

## Required Task Content
Each created task should include:
- objective
- scope
- acceptance criteria
- dependency notes
- risk notes if relevant
- owner role if known

## Task Title Standard
Use verb-led, outcome-focused titles.

Pattern:
`<Action> <object> <context>`

Examples:
- Add validation for onboarding request
- Update mapper for advisory profile field
- Create release checklist for profile update rollout

## When to Split a Story
Split if:
- multiple systems are affected with independent work
- different teams/roles are needed
- backend/frontend/testing/release are distinct streams
- one ticket would be too large to review safely
- dependencies need explicit sequencing

## When Not to Split Too Much
Avoid over-splitting if:
- work is tightly coupled and tiny
- multiple tasks would create admin noise without real value
- one engineer will complete it in a few focused steps

## Output of Task Creation
The task creation workflow should return:
- story summary
- proposed tasks
- task descriptions
- acceptance criteria
- dependency order
- risk notes
- suggested creation sequence