# SDLC Playbook

## Purpose
Define how this team delivers work from request intake to production release using human judgment plus Windsurf assistance.

## Principles
- Engineer owns the outcome.
- AI accelerates understanding, drafting, implementation, and review.
- Human owners remain accountable for design, security, production safety, and release decisions.
- Small, traceable, testable changes are preferred over large rewrites.

## Delivery flow

### 1. Story intake
Objective:
Understand the business request before any code changes.

Expected actions:
- review story and linked references
- run story analysis workflow
- identify impacted areas, ambiguity, and risks
- confirm acceptance criteria

Outputs:
- requirement summary
- assumptions / open questions
- impacted component list
- initial risk view

### 2. Solution shaping
Objective:
Choose the lowest-risk approach that fits existing architecture.

Expected actions:
- draft lightweight design for non-trivial work
- identify API, DB, event, config, UI, and integration impact
- check backward compatibility
- check rollout / rollback needs

Outputs:
- short design note
- implementation plan
- testing plan
- dependency list

### 3. Implementation
Objective:
Build only what is needed, aligned with team standards.

Expected actions:
- use existing patterns
- keep changes minimal and focused
- avoid unrelated refactors
- update docs/tests where needed

Outputs:
- code changes
- tests
- implementation summary

### 4. Validation
Objective:
Verify the change is correct and safe.

Expected actions:
- run unit/integration tests as appropriate
- validate acceptance criteria
- review logs, errors, edge cases, and negative paths
- confirm no obvious consumer impact was missed

Outputs:
- test evidence
- known limitations
- residual risk notes

### 5. PR review
Objective:
Catch issues before merge.

Expected actions:
- run PR review workflow
- compare change against requirement and design
- check correctness, security, performance, observability, compatibility, and test coverage

Outputs:
- review findings
- follow-up fixes
- merge recommendation

### 6. Release readiness
Objective:
Ensure production rollout is controlled.

Expected actions:
- identify config and deployment dependencies
- identify rollback approach
- define post-release validation checks
- note feature flag or staged rollout needs if applicable

Outputs:
- release checklist
- rollback note
- production verification steps

### 7. Post-release learning
Objective:
Improve team speed and quality continuously.

Expected actions:
- capture defects, escaped issues, and review misses
- improve prompts, workflows, playbooks, and tests
- update standards when repeated issues appear

Outputs:
- retro note
- playbook updates
- workflow or rule improvements

## Human approval points
Human review is mandatory for:
- architecture changes
- public API contract changes
- auth/security-sensitive code
- production config changes
- data migrations
- cross-team integration impact
- file upload / document handling changes
- large refactors or generated code touching many files

## AI usage guidance

### Good uses
- requirement summarization
- impact analysis
- design draft
- boilerplate generation
- test scaffolding
- code review assistance
- release checklist drafting
- documentation updates

### Bad uses
- blind code generation without context
- changing many files without clear scope
- security decisions without human review
- inventing business rules
- modifying restricted areas without approval

## Definition of ready
Work should not begin until:
- business need is understandable
- acceptance criteria are usable
- dependencies are known or explicitly called out
- impacted systems are identified at a reasonable level
- key risks are visible

## Definition of done
Work is complete only when:
- requirement is implemented
- tests are appropriate
- review findings are addressed
- rollout/rollback concerns are considered
- residual risks are documented
- supporting docs are updated where needed

## Standard prompts to use

### Story analysis
Use `/story-analysis`

### Implementation
Use `/implementation`

### PR review
Use `/pr-review`

## Metrics to track
- time from story start to first technical plan
- PR turnaround time
- escaped defects
- rework after review
- % stories analyzed before coding
- % changes with updated tests