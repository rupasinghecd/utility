# Impact Analysis Policy

## Purpose
Define how a change request, story, or PRD is analyzed to determine technical, functional, operational, and compliance impact before implementation planning and task creation.

## Why This Exists
A team should not jump from a Jira story directly into coding tasks without understanding blast radius.

Impact analysis exists to answer:
- what is affected
- what might break
- what needs validation
- what needs coordination
- what delivery streams must be created

## Scope
Applies to:
- feature stories
- cross-system changes
- API changes
- DB/schema changes
- audit/compliance-related changes
- integration changes
- file/document handling changes
- medium and large bug fixes
- technical changes with consumer or operational impact

## Core Principles
- impact analysis comes before implementation planning
- impact analysis identifies both confirmed and possible impact
- confirmed impact must be separated from assumptions
- task creation must trace back to impact items
- impact analysis should be practical, not theoretical
- the goal is safe delivery, not exhaustive speculation

## Inputs
Impact analysis should use, where available:
- Jira story
- Epic context
- PRD
- linked comments
- current architecture and service map
- API contracts
- DB schema knowledge
- event/integration documentation
- security/audit policies
- codebase context

## Output Requirements
Every impact analysis must produce:

### 1. Requirement Summary
A short technical restatement of the requested change.

### 2. Confirmed Impacted Areas
Areas that are directly indicated by the story, PRD, or known system structure.

### 3. Possible Impacted Areas Requiring Confirmation
Areas that are likely affected but not yet confirmed.

### 4. Delivery Streams
The workstreams that will likely be needed:
- backend-api
- validation
- frontend
- integration
- migration
- audit
- testing
- release
- documentation
- entitlement/security

### 5. Risks
Technical, operational, compliance, or dependency risks.

### 6. Compatibility Assessment
Backward-compatibility and consumer-impact analysis.

### 7. Task-Creation Hints
A bridge section showing what categories of tasks should be created later.

## Impact Dimensions

## A. Functional Impact
Assess:
- affected user journey
- business rule changes
- validation behavior changes
- workflow/status transition changes
- happy path and negative path changes

Questions:
- what user/system behavior changes?
- is this limited to one flow or multiple flows?
- do edge cases become invalid/valid?

## B. Application Component Impact
Assess which code/application areas are affected.

For Java / Spring systems, consider:
- controllers/resources
- request/response DTOs
- validators
- services
- repositories
- mappers
- configuration classes
- exception handlers
- security filters/interceptors
- audit/logging helpers

## C. API / Contract Impact
Assess:
- request payload impact
- response payload impact
- validation/error response impact
- versioning need
- upstream/downstream compatibility

Questions:
- can existing consumers continue working?
- does stricter validation change consumer behavior?
- do documentation or contract tests need updates?

## D. Data / DB Impact
Assess:
- schema changes
- table/column changes
- index/query impact
- migration need
- rollback complexity
- old/new code coexistence risk

Questions:
- is migration additive or breaking?
- can rollout be sequenced safely?
- does audit storage change?

## E. Event / Integration Impact
Assess:
- Kafka/event payload changes
- downstream consumer impact
- external API integration impact
- retry/timeout implications
- ordering/idempotency concerns

Questions:
- do any consumers need coordination?
- does payload structure or meaning change?
- do integration contracts need review?

## F. Security / Entitlement Impact
Assess:
- who can perform the action
- whether authorization changes
- whether approval flow changes
- whether sensitive access paths are affected

Questions:
- does this introduce new access paths?
- does existing entitlement remain sufficient?
- are any privileged actions now impacted?

## G. Audit / Compliance Impact
Assess:
- whether action must be auditable
- whether before/after values are needed
- whether actor/timestamp/context must be recorded
- whether file or status changes must be tracked

Questions:
- what evidence is required later?
- what fields or actions require traceability?
- does this affect regulated records?

## H. Data Classification Impact
Assess:
- whether PII/customer data is involved
- whether document/file sensitivity exists
- whether masking/redaction/logging rules matter

Questions:
- what data sensitivity applies?
- can logs safely include identifiers?
- are retention or handling constraints relevant?

## I. Testing Impact
Assess:
- unit test impact
- integration test impact
- contract test impact
- regression scope
- negative-path testing needs
- test data concerns

Questions:
- what must be tested because of this change?
- what existing tests may break?
- are new edge cases introduced?

## J. Release / Operational Impact
Assess:
- config changes
- deployment order
- rollback path
- feature flag need
- observability/monitoring implications
- production support watchpoints

Questions:
- does release sequencing matter?
- is rollback straightforward?
- what needs post-release verification?

## Confirmed vs Possible Impact Rules

### Confirmed Impact
Use when:
- explicitly stated in story/PRD
- directly inferable from known architecture
- already evidenced by linked system context

### Possible Impact
Use when:
- likely but not confirmed
- dependent on implementation choice
- dependent on architecture detail not yet verified

Possible impact must be clearly labeled as:
- possible impact
- requires confirmation

## Risk Levels

### High
Use when there is likely:
- compatibility break
- security/control risk
- audit/compliance risk
- migration/release hazard
- cross-team dependency with time sensitivity

### Medium
Use when there is:
- meaningful implementation uncertainty
- moderate operational or consumer risk
- partial dependency ambiguity

### Low
Use when:
- change is localized
- compatibility is stable
- operational impact is minimal

## Required Correlation to Implementation Planning
Implementation planning must consume the impact analysis output.

At minimum, implementation planning must map:
- impacted area -> planned approach
- risk -> mitigation
- delivery stream -> task breakdown
- compatibility concern -> validation/release note

## Required Correlation to Task Creation
Task creation must reference impact analysis.

Every created task should be traceable to one or more:
- impacted components
- delivery streams
- risk areas
- compatibility concerns

Prefer adding this in task descriptions:

### Source Impact Item
Example:
- onboarding-api.validation
- audit.persistence
- downstream-consumer.compatibility

## Output Format Standard

### Requirement Summary
### Confirmed Impacted Areas
### Possible Impacted Areas
### Compatibility Impact
### Security / Entitlement Impact
### Audit / Compliance Impact
### Data / DB Impact
### Integration / Event Impact
### Testing Impact
### Release / Operational Impact
### Delivery Streams
### Risks
### Planning and Task Creation Hints

## Anti-patterns
Avoid:
- jumping straight to tasks without impact mapping
- treating all possible impacts as confirmed
- ignoring downstream consumers
- ignoring rollout/rollback implications
- listing generic impact without actionability
- failing to connect impact items to later tasks

## Definition of Completion
Impact analysis is complete when:
- likely blast radius is visible
- confirmed vs possible impact is separated
- major risks are called out
- likely delivery streams are identified
- implementation planning can proceed safely