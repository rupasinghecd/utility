# MFE Template

## Purpose
Define the standard skeleton and design expectations for a new microfrontend.

## Scope
Use when a new MFE is approved.

## Standard Structure

### Suggested Areas
- route registration
- page/container components
- feature components
- hooks
- api clients
- state/store
- entitlement/guards
- error/loading states
- test
- mfe registration / shell integration

## Required Technical Foundations

### Route Ownership
- clear route(s)
- clear page ownership
- shell registration or host integration defined

### Backend Integration
- explicit API client module
- error handling strategy
- loading state strategy
- compatibility with backend validation/error formats

### Security / Entitlement
- route/page visibility rules
- action-level UI guard points
- no leakage of privileged options without checks

### Observability / Support
- error boundary approach if used
- meaningful UI logging/tracing if supported
- release verification checkpoints

### Testing
- unit/component tests
- route/page-level tests where needed
- negative-path UI behavior for validation/error handling

## Standard Deliverables
A new MFE setup plan should include:
- repo/module name
- route(s)
- page/component structure
- shell registration notes
- API client placeholders
- state/store placeholders
- entitlement integration points
- test setup plan

## Naming Guidance
Use route- or journey-based names.

Examples:
- rm-suitability-review-mfe
- onboarding-document-intake-mfe

## Anti-patterns
Avoid:
- MFE with unclear route ownership
- dumping unrelated screens into one new MFE
- skipping shell/guard integration thinking
- creating a thin wrapper MFE with no real ownership