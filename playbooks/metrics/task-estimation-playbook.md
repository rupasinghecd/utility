# Task Estimation Playbook

## Purpose
Provide consistent end-to-end effort estimation for delivery work using task breakdown, impact analysis, lineage, and implementation context.

## Why This Exists
Engineering estimation often undercounts:
- integration work
- testing effort
- release effort
- dependency coordination
- uncertainty and rework risk

This playbook ensures estimation reflects total delivery effort, not just coding time.

## Estimation Principles
- estimate end-to-end effort, not just implementation effort
- estimate after impact analysis and task creation, not before
- distinguish effort from elapsed timeline
- distinguish direct build effort from shared overhead
- avoid double-counting testing/release effort across tasks
- include uncertainty explicitly
- use historical comparison when possible
- state confidence, not just numbers

## Inputs
Use:
- story / PRD
- impact analysis
- implementation plan
- task breakdown
- system lineage
- historical similar stories if available

## Output Required
Every estimation should provide:
- effort per task
- effort per category
- shared overhead effort
- total effort
- likely timeline
- confidence level
- key risk drivers

## Effort Categories

### 1. Frontend Effort
Includes:
- route/page/component updates
- API integration
- validation/error state handling
- state/store updates
- UI test updates

### 2. Backend Effort
Includes:
- controller/service/validation logic
- DTO and mapper changes
- repository/query changes
- security/audit handling
- backend unit/integration tests

### 3. Database Effort
Includes:
- schema changes
- migrations
- compatibility handling
- backfill/data correction if needed
- DB validation/testing

### 4. Messaging Effort
Includes:
- Kafka producer/consumer updates
- topic/schema changes
- retry/idempotency/error-path changes
- event validation/testing

### 5. Integration Effort
Includes:
- downstream REST changes
- contract compatibility checks
- external service coordination
- mocks/stubs/supporting setup

### 6. Testing Effort
Includes:
- integration test coverage
- regression test scope
- contract test updates
- QA/UAT support where relevant

### 7. Release / DevOps Effort
Includes:
- config changes
- environment setup
- deployment coordination
- rollback/fallback preparation
- release verification steps

### 8. Coordination Effort
Includes:
- dependency clarification
- cross-team alignment
- architecture/security/review discussions
- consumer communication if needed

### 9. Risk / Uncertainty Buffer
Includes:
- unclear requirements
- unknown dependencies
- new architecture/library patterns
- low-confidence lineage/impact mapping
- production-risk-sensitive changes

## Estimation Levels

### Tiny
- very localized
- single component
- no meaningful dependency
- minimal testing overhead

### Small
- one primary system
- little or no downstream impact
- known pattern
- straightforward validation/testing

### Medium
- multiple components or one system plus integration
- moderate validation/testing
- some release or dependency overhead

### Large
- multiple systems / MFEs / DB / Kafka / release complexity
- significant testing and coordination

### Extra Large
- new architecture
- new microservice/MFE/library
- unclear boundaries
- significant coordination, setup, and rollout risk

## Suggested Base Ranges
These are starting ranges, not fixed truth.

- Tiny: 0.5 to 1.0 day
- Small: 1 to 3 days
- Medium: 3 to 6 days
- Large: 6 to 12 days
- Extra Large: 12+ days or split further

## Estimation Method

### Step 1: Confirm work type
Classify as one of:
- existing-system enhancement
- cross-system enhancement
- new system introduction
- spring library introduction
- UI-only
- backend-only
- API/DB-heavy
- Kafka/integration-heavy

### Step 2: Estimate task-level direct effort
For each task estimate:
- build effort
- test effort
- local validation effort

Do not include shared release overhead in every task.

### Step 3: Identify shared overhead
Estimate once at story/initiative level:
- shared testing effort
- shared release effort
- shared coordination effort
- shared risk buffer

### Step 4: Mark dependency mode
For each task mark:
- sequential
- parallel
- partially parallel

This is required to separate total effort from likely timeline.

### Step 5: Add confidence
Confidence levels:
- High: clear scope, known patterns, low dependency uncertainty
- Medium: some unknowns or moderate integration complexity
- Low: unclear requirements, new architecture, unresolved dependencies

### Step 6: Compare with historical work
If similar stories exist:
- compare estimated effort to actual effort
- adjust if prior actuals show systematic under/over-estimation

## Complexity Drivers
Increase effort when these are present:
- more than one backend service
- frontend + backend both change
- DB migration needed
- Kafka/topic change needed
- contract compatibility review needed
- cross-team dependency exists
- entitlement/security/audit implications exist
- new repo/module/setup work exists
- release sequencing is sensitive

## Reduction Factors
Reduce effort only when clearly true:
- known repeated pattern
- no consumer-facing contract impact
- no schema or event changes
- no cross-team dependency
- existing tests and scaffolding are strong

## Shared Overhead Rules
Do not duplicate these across every task:
- release checklist creation
- rollout/rollback documentation
- broad regression coordination
- architecture review meeting
- shared integration environment setup

Estimate them once and apply at story/initiative level.

## Timeline Calculation
Total effort is not the same as timeline.

### Total Effort
Sum of all task direct effort + shared overhead

### Likely Timeline
Depends on:
- dependency order
- number of people/roles involved
- parallel work possible
- approval/waiting time
- release window constraints

Output both values separately.

## Recommended Output Format

### Story / Initiative Summary
- work type
- scope size
- confidence level

### Task Estimates
For each task:
- title
- category
- direct effort
- testing effort
- dependency mode
- confidence
- notes

### Shared Overhead
- shared testing effort
- shared release effort
- shared coordination effort
- shared risk buffer

### Totals
- total direct effort
- total shared overhead
- total end-to-end effort
- likely delivery timeline

### Key Risk Drivers
List major uncertainty factors.

## Example
Task A: backend validation change
- direct build effort: 2.0 days
- local testing effort: 0.5 day
- dependency mode: sequential
- confidence: high

Task B: frontend validation rendering
- direct build effort: 1.5 days
- local testing effort: 0.5 day
- dependency mode: parallel
- confidence: medium

Task C: integration test updates
- direct build effort: 1.0 day
- local testing effort: 0.5 day
- dependency mode: follow-up
- confidence: medium

Shared overhead:
- release effort: 0.5 day
- coordination effort: 0.5 day
- risk buffer: 1.0 day

Totals:
- total effort: 7.5 days
- likely timeline: 4 to 5 working days with 2 contributors

## Anti-patterns
Avoid:
- one-number estimates with no breakdown
- estimating before impact analysis
- ignoring release/testing/coordination
- counting the same regression effort in every task
- equating effort with duration
- keeping extra-large items unsplit

## Definition of Completion
An estimate is complete when:
- task-level effort exists
- shared overhead is separated
- timeline is distinct from effort
- confidence is stated
- risk drivers are visible