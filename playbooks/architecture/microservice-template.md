# Microservice Template

## Purpose
Define the standard skeleton and design expectations for a new Java / Spring microservice.

## Scope
Use when a new backend service is approved.

## Standard Structure

### Suggested Modules / Packages
- controller
- dto
- validation
- service
- repository
- integration
- mapper
- config
- exception
- security
- audit
- metrics
- events
- migration
- test

## Required Technical Foundations

### API Layer
- explicit request/response DTOs
- consistent error model
- validation at request boundary
- backward compatibility note for public APIs

### Service Layer
- clear orchestration logic
- business rules separated from transport concerns
- explicit integration boundaries

### Persistence Layer
- repository/query structure
- migration support
- transaction boundaries considered

### Security
- authn/authz integration point
- entitlement model or delegated check
- no sensitive logging

### Audit
- audit hooks/placeholders where needed
- actor/context handling consideration
- traceability for regulated actions

### Observability
- structured logging
- metrics where meaningful
- trace/troubleshooting readiness

### Testing
- unit tests
- integration tests
- contract tests where needed
- negative-path tests

## Standard Deliverables
A new microservice setup plan should include:
- repo/module name
- package layout
- base endpoint path
- config placeholders
- migration baseline
- README/setup note
- CI/CD/bootstrap needs
- support/monitoring notes

## Naming Guidance
Use stable, domain-based names.

Examples:
- suitability-decision-service
- client-document-intake-service

## Anti-patterns
Avoid:
- giant starter service with unrelated modules
- generic “common engine”
- unclear ownership of data or APIs
- missing migration or observability planning