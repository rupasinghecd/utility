# New System Design Policy

## Purpose
Define when and how the team introduces a new microservice, new MFE, or new architectural slice for a change request.

## Why This Exists
Not every feature should create a new service or MFE. New systems add delivery, support, security, operational, and ownership overhead. This policy ensures the decision is deliberate, reviewable, and consistent.

## When to Use
Use this policy when:
- no existing service clearly owns the capability
- no existing MFE clearly owns the journey
- the change creates a new bounded context
- the required release cadence differs from existing owners
- the capability needs a separate security, data, or operational boundary
- extending current systems would create unhealthy coupling

## Core Principles
- prefer extending an existing bounded context when ownership is clear
- introduce a new system only when the boundary is justified
- define ownership before design detail
- define contracts before implementation detail
- make architecture decisions explicit and versioned
- keep the first version of a new system minimal and outcome-focused
- build for traceability, supportability, and controlled rollout

## Decision Criteria

### A. New Microservice Is Justified When
One or more of the following apply:
- the capability has distinct business ownership
- the capability has a clear domain boundary
- the change would significantly bloat an existing service
- the capability needs separate release cadence
- the capability needs separate scaling or runtime characteristics
- the capability has distinct security or compliance needs
- the capability should own its own data and lifecycle

### B. New MFE Is Justified When
One or more of the following apply:
- the journey is distinct and user-facing
- the owning team is separate
- route ownership is clear
- feature boundaries are stable
- release cadence differs from surrounding UI
- extending an existing MFE would create poor cohesion

### C. New System Is Usually Not Justified When
- the change is one endpoint in an already-owned domain
- the change is one screen in an already-owned MFE
- the split is driven only by dissatisfaction with the current codebase
- the ownership boundary is unclear
- the new system would create orchestration complexity without a real domain boundary

## Required Design Outputs
Any approved new-system proposal must define:

### 1. Problem Statement
What capability is being introduced and why current systems are insufficient.

### 2. System Type
State whether this is:
- new microservice
- new MFE
- both
- supporting shared component only

### 3. Ownership Boundary
Define:
- what the system owns
- what it does not own
- which team owns delivery and runtime support

### 4. Contract Boundary
Define:
- APIs exposed
- events produced/consumed
- UI routes/screens owned
- integration boundaries

### 5. Data Ownership
Define:
- data owned by the system
- source of truth
- persistence approach
- migration implications

### 6. Security / Entitlement Expectations
Define:
- who can access the capability
- whether privileged actions exist
- approval or authorization implications

### 7. Audit / Compliance Expectations
Define:
- what actions must be auditable
- what data changes need traceability
- what support evidence is expected

### 8. Operational Expectations
Define:
- logging
- metrics
- tracing
- alerting/watchpoints
- deployment model
- rollback/fallback expectations

### 9. Adoption / Rollout Plan
Define:
- first release scope
- migration/adoption strategy
- coexistence with old systems if relevant
- feature flag or phased rollout expectations

## Required Alternatives Analysis
Before creating a new system, compare at least:
1. extend an existing service/MFE
2. introduce a bounded module inside an existing repo/system
3. create a new service/MFE

For each option, summarize:
- pros
- cons
- coupling impact
- ownership clarity
- release impact
- operational complexity

## Minimum First Version Rules
The first version of a new system should:
- solve one clear outcome
- avoid speculative platform features
- use established team standards
- include only required integrations
- include tests and observability from the start
- keep interfaces simple and explicit

## Required Review Gates
A new system should not proceed to implementation until:
- architecture decision is written
- ownership is agreed
- integration points are known
- rollout approach is understood
- delivery task breakdown exists

## Standard Naming Guidance
Use stable names that reflect ownership and capability.

Examples:
- onboarding-decision-service
- rm-suitability-review-mfe
- client-document-intake-service

Avoid:
- new-service-v2
- temp-review-mfe
- common-engine-final

## Anti-patterns
Avoid:
- creating a new system to escape refactoring
- splitting too early without a stable boundary
- sharing data ownership ambiguously
- creating generic services with unclear purpose
- creating MFEs with no route or journey ownership
- introducing distributed complexity without clear value

## Definition of Completion
A new-system design decision is complete when:
- the boundary is justified
- ownership is clear
- contracts are visible
- operational/security/audit expectations are defined
- implementation can be planned in a controlled way