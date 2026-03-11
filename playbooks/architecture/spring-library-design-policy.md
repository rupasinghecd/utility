# Spring Library Design Policy

## Purpose
Define when and how the team creates a reusable Spring library for shared backend capabilities.

## Why This Exists
A shared library can improve consistency and speed, but it can also create widespread coupling, hidden behavior, and upgrade pain if introduced carelessly.

This policy ensures new libraries are:
- justified
- bounded
- versionable
- safe to consume
- easy to test
- aligned with enterprise standards

## When to Use
Use this policy when:
- multiple services need the same backend capability
- repeated code or patterns are appearing across services
- a standard integration layer is needed
- a standard validation, audit, security, or utility capability is needed
- a shared Spring Boot starter or autoconfiguration module is being proposed

## Do Not Create a Library When
- only one service needs the capability
- the abstraction is still unstable
- the shared logic is too domain-specific
- the library would hide critical business behavior
- copy-paste is temporarily lower risk than premature abstraction
- the main driver is “cleaning up code” without clear reuse need

## Library Categories
A proposed library should be classified as one of:

### 1. Utility Library
Examples:
- common value formatting
- shared mapping helpers
- lightweight reusable support code

### 2. Integration Library
Examples:
- standard client wrapper for a platform service
- document storage client
- notification client
- audit publishing client

### 3. Policy / Validation Library
Examples:
- shared validation rules
- request validators
- entitlement evaluation helpers

### 4. Spring Boot Starter / Auto-Configuration Library
Examples:
- standard logging setup
- audit integration starter
- common observability starter
- redis/session starter

### 5. Testing Support Library
Examples:
- test fixtures
- mock servers
- reusable Spring test utilities

## Decision Criteria

### A. Reuse Justification
A library is justified when:
- at least 2 or more consumers clearly need the same capability, or
- a common platform capability needs one standard integration pattern

Document:
- current consumers
- expected near-term consumers
- why a shared library is better than local implementation

### B. Boundary Clarity
A library must have a clear purpose.
It should state:
- what it does
- what it does not do
- whether it contains business logic or only technical/platform logic

### C. Coupling Risk
Assess:
- whether consumers become tightly coupled to internal design
- whether changes will cause widespread upgrades
- whether runtime behavior becomes hidden or surprising

### D. Versioning Impact
Assess:
- how consumers will upgrade
- compatibility expectations
- breaking-change strategy
- whether semantic versioning will be followed

### E. Spring Behavior Visibility
If using Spring Boot starter/autoconfiguration patterns:
- behavior must be explicit
- activation conditions must be clear
- consumers must be able to override where appropriate
- defaults must be safe

## Required Design Outputs
Any approved library proposal must define:

### 1. Problem Statement
What repeated or shared need is being solved.

### 2. Library Type
State the library category.

### 3. Consumers
List:
- current consumers
- target consumers
- expected adoption scope

### 4. Responsibility Boundary
Define:
- what the library owns
- what stays in consuming services
- what extension points exist

### 5. API Surface
Define:
- public classes/interfaces
- configuration surface
- annotations if any
- autoconfiguration behavior if any

### 6. Dependency Rules
Define:
- allowed dependencies
- forbidden dependencies
- Spring Boot version compatibility
- Java version compatibility

### 7. Security / Audit / Logging Considerations
Define:
- whether library touches sensitive flows
- whether logging is safe
- whether audit behavior is introduced
- whether auth/entitlement behavior is involved

### 8. Testing Strategy
Define:
- unit test approach
- integration test approach
- compatibility tests if needed
- sample consumer validation

### 9. Versioning and Release Strategy
Define:
- artifact coordinates
- versioning approach
- release pipeline
- deprecation and breaking-change policy

## Design Rules

### Public API Design
- keep public API small and explicit
- prefer interfaces and stable contracts where appropriate
- avoid exposing internal implementation details
- avoid overly clever extension models

### Spring Design
- prefer explicit configuration properties
- make defaults safe
- keep autoconfiguration conditional and predictable
- avoid mandatory magic behavior
- avoid forcing component scanning in surprising ways

### Dependency Discipline
- avoid pulling in heavy unnecessary transitive dependencies
- avoid depending on service-specific domain modules
- avoid circular dependency risk
- keep platform dependencies intentional

### Consumer Safety
The library should:
- fail clearly when misconfigured
- document required properties
- document optional overrides
- support safe adoption in one service before wider rollout

## Anti-patterns
Avoid:
- “common” libraries with mixed unrelated concerns
- hiding business logic in shared technical libraries
- autoconfiguration that silently changes runtime behavior
- global interceptors/filters without clear opt-in rules
- unstable public API with many consumers
- library creation before reuse is real

## Required Review Gates
A Spring library should not proceed until:
- reuse case is justified
- boundary is clear
- public API is reviewed
- dependency model is reviewed
- versioning strategy is defined
- consumer adoption approach is defined

## Definition of Completion
Library design is complete when:
- purpose is clear
- consumers are identified
- API/config surface is defined
- Spring behavior is explicit
- adoption and versioning are understood