# System Map Extraction Policy

## Purpose
Define how architecture maps are extracted from code when no service catalog, domain map, or journey map exists yet.

## Why This Exists
Teams often know the UI entrypoint but do not have reliable documentation showing:
- which backend microservices support that UI
- which MFEs exist and what they own
- which downstream services are involved
- which journeys and domains map to which systems

This policy standardizes how those maps are generated from code and then promoted into reusable playbooks.

## Scope
Use this policy when:
- there is no existing architecture catalog
- an MFE or UI entrypoint is known
- a route, screen, page, or entry component is known
- a repo/module is known but ownership mapping is missing
- impact analysis needs a system map but none exists yet

## Inputs
The bootstrap process should accept one or more of the following:
- MFE repo name
- MFE module path
- route path
- entry component path
- screen name
- API client file
- shell registration entry if using microfrontends

## Extraction Objectives
The extraction process should produce draft versions of:
- MFE catalog
- service catalog
- domain-to-system map
- journey-to-system map
- repo-to-system map

## Extraction Principles
- start from evidence, not assumptions
- separate confirmed mappings from inferred mappings
- prefer route, client, controller, and config evidence over naming guesses
- show uncertainty explicitly
- optimize for usefulness, not theoretical perfection
- make outputs reviewable and versionable

## Evidence Sources

### MFE Evidence
Use:
- route definitions
- page/component structure
- microfrontend registration
- API client modules
- state/store slices
- entitlement/feature-guard logic
- screen names and menu entries

### Backend Evidence
Use:
- controller/request mappings
- DTO names
- service names
- integration client classes
- repository names
- event producers/consumers
- migration files
- audit/security integration points

### Configuration Evidence
Use:
- environment variables
- base URLs
- gateway prefixes
- ingress/proxy config
- API config files
- shell/mfe manifest config

### Historical Evidence
Use when available:
- similar Jira issues
- past commits
- PR titles and descriptions
- repo activity tied to related stories

## Extraction Order

### Step 1: Identify the UI Boundary
Determine:
- route(s)
- page/component entrypoint
- MFE/module name
- shell registration if present

### Step 2: Identify Outbound Calls
Determine:
- REST/GraphQL calls
- SDK/client wrappers
- gateway or BFF paths
- event requests
- document service usage
- entitlement checks

### Step 3: Resolve Backend Owners
Map outbound calls to likely backend systems using:
- base URL / gateway path
- controller mappings
- repo names
- package/module naming
- API specs if present

### Step 4: Expand to Secondary Dependencies
For each identified backend service, inspect:
- downstream clients
- event producers/consumers
- cache usage
- audit usage
- security/entitlement integrations
- persistence and migrations

### Step 5: Infer Domains and Journeys
Group findings by:
- business capability
- route/journey
- primary owner system
- supporting systems

### Step 6: Generate Draft Artifacts
Create the draft architecture map files.

### Step 7: Flag Uncertainty
For each generated mapping, record:
- confidence
- evidence
- whether human review is needed

## Confidence Levels

### High
Use when:
- directly supported by route/client/controller/config evidence
- clearly owned by repo/module structure
- directly referenced in code path from the UI

### Medium
Use when:
- strongly inferred from naming and usage
- secondary service likely but not fully traversed
- historical evidence supports it but code path is indirect

### Low
Use when:
- possible downstream dependency only
- likely supporting system but not explicitly proven
- limited evidence exists

## Required Outputs

## A. MFE Catalog
Each MFE entry should include:
- name
- routes/screens
- entry components
- backend dependencies
- supporting dependencies
- evidence
- confidence

## B. Service Catalog
Each service entry should include:
- name
- owned capability
- common clues
- upstream callers if known
- downstream dependencies if known
- evidence
- confidence

## C. Domain-to-System Map
Each domain entry should include:
- domain name
- business keywords
- candidate backend systems
- candidate MFEs
- supporting systems
- common impact patterns

## D. Journey-to-System Map
Each journey entry should include:
- journey name
- primary MFE
- primary services
- supporting services
- common secondary impact

## E. Repo-to-System Map
Each repo entry should include:
- repo name
- mapped system name
- system type
- evidence
- confidence

## Output Quality Rules
Generated outputs must:
- be understandable by humans
- contain enough evidence to be reviewed
- avoid claiming unsupported certainty
- use normalized naming where possible
- be useful for later impact analysis and task creation

## Naming Guidance
Prefer stable business/technical names such as:
- onboarding-service
- rm-onboarding-mfe
- audit-service

Avoid unstable names like:
- final-onboarding-module
- temp-profile-service-v2

## Anti-patterns
Avoid:
- guessing service ownership only from folder names
- treating all downstream dependencies as confirmed
- generating maps without evidence sections
- over-modeling tiny internal utilities as separate systems
- skipping human review of the first draft

## Human Review Requirement
The first generated draft must be reviewed by a tech lead, architect, or system owner before it becomes the reference map.

## Definition of Completion
Extraction is complete when:
- primary MFE ownership is visible
- primary backend services are identified
- major supporting systems are visible
- domains and journeys are reasonably grouped
- repo ownership mapping exists
- confidence and evidence are captured