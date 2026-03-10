---
title: Bootstrap System Maps From MFE
description: Generate architecture map files from a UI entrypoint when no service catalog exists.
---

# Bootstrap System Maps From MFE

## Goal
Create draft architecture maps starting from a known MFE, route, page, or UI entry component.

## Inputs expected
One or more of:
- MFE repo name
- MFE module path
- route path
- page/component path
- screen name
- API client file

Also use:
- playbooks/architecture/system-map-extraction-policy.md

## What to optimize for
- practical ownership discovery
- traceable evidence
- useful draft outputs
- clear uncertainty handling

## Steps

### 1. Identify the UI entry boundary
Determine:
- MFE/module name
- route(s)
- entry page/component(s)
- shell registration or host reference if applicable

Output:
- initial MFE identity
- routes/screens
- confidence and evidence

### 2. Trace outbound dependencies from the UI
Inspect:
- API client imports
- fetch/axios/sdk wrappers
- config-driven base URLs
- route guards / entitlement checks
- document/file modules
- shared utility clients that call backend APIs

Output:
- candidate API endpoints
- candidate backend targets
- candidate supporting services

### 3. Resolve primary backend services
For each API call or client wrapper:
- identify path prefixes
- identify likely owning service
- inspect codebase for controller mappings and DTO matches
- inspect gateway/BFF config if direct ownership is unclear

Output:
- MFE -> endpoint -> service mapping
- confidence and evidence for each mapping

### 4. Expand into secondary dependencies
For each identified service, inspect:
- downstream REST clients
- Kafka/event usage
- Redis/cache usage
- audit service usage
- entitlement/security integrations
- document/storage integrations
- repositories and migration folders

Output:
- primary services
- supporting services
- possible downstream services

### 5. Infer journeys
Using routes, page names, endpoint names, and service semantics:
- infer likely journey names
- group screens and systems by journey

Examples:
- RM updates onboarding details
- User uploads supporting documents
- RM reviews advisory profile

Output:
- journey candidates
- primary and supporting systems by journey

### 6. Infer domains
Using journeys, module names, and service capabilities:
- group systems into domains

Examples:
- Client Onboarding
- Client Profile Maintenance
- Document Management
- Audit / Traceability

Output:
- domain candidates
- mapped systems by domain

### 7. Build repo-to-system mappings
For each discovered repo or module:
- map repo to normalized system name
- classify as mfe, microservice, supporting service, shared module, or unknown
- capture evidence

Output:
- repo-to-system draft

### 8. Generate draft architecture files
Generate these draft files:
- playbooks/architecture/mfe-catalog.md
- playbooks/architecture/service-catalog.md
- playbooks/architecture/domain-to-system-map.md
- playbooks/architecture/journey-to-system-map.md
- playbooks/architecture/repo-to-system-map.md

### 9. Summarize uncertainty
Clearly state:
- what is confirmed
- what is inferred
- what needs human review
- what could not be resolved from code

## Output format

### Summary
Short summary of what was discovered.

### Confirmed Mappings
List high-confidence MFE/service mappings.

### Inferred Mappings
List medium/low-confidence mappings.

### Draft Files Generated
List the file names and what each contains.

### Open Questions
List unresolved areas needing human review.

## Constraints
- do not invent unsupported ownership
- separate confirmed from inferred mappings
- do not skip evidence
- do not treat every imported utility as a system
- normalize names where possible