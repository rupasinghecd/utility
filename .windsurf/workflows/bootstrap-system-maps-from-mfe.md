---
title: Bootstrap System Maps From MFE
description: Build architecture maps starting from an MFE entrypoint when no service catalog exists.
---

# Bootstrap System Maps From MFE

## Goal
Generate initial architecture mapping files from a UI entrypoint.

## Inputs expected
- MFE entrypoint repo/module/path/route/component
- playbooks/architecture/system-map-extraction-policy.md

## Steps
1. Identify the MFE boundary:
   - route
   - page/component
   - API clients
   - state/store
2. Extract outbound dependencies:
   - REST/GraphQL calls
   - gateway paths
   - config-based service targets
3. Identify candidate backend services.
4. Inspect each backend service for:
   - controllers
   - DTOs
   - downstream clients
   - events
   - repositories
   - audit/security integrations
5. Group results into:
   - MFEs
   - services
   - journeys
   - domains
   - repo-to-system mappings
6. For every mapping, record:
   - confidence
   - evidence
7. Generate draft files:
   - playbooks/architecture/mfe-catalog.md
   - playbooks/architecture/service-catalog.md
   - playbooks/architecture/domain-to-system-map.md
   - playbooks/architecture/journey-to-system-map.md
   - playbooks/architecture/repo-to-system-map.md
8. Summarize unknowns and areas needing human review.

## Output format
### Summary
### Confirmed mappings
### Inferred mappings
### Draft files generated
### Open questions