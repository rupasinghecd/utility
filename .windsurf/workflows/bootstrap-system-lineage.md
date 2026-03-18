---
title: Bootstrap System Lineage
description: Discover recursive architecture lineage from an MFE, microservice, API, Kafka topic, DB table, or shared library.
---

# Bootstrap System Lineage

## Goal
Starting from a supplied entrypoint, discover end-to-end lineage across MFE, APIs, services, Kafka, databases, tables, shared libraries, and downstream integrations.

## Inputs expected
- entry type
- entry reference
- optional recursion depth
- playbooks/architecture/system-lineage-discovery-policy.md

## Supported entry types
- mfe
- microservice
- api-endpoint
- kafka-topic
- db-table
- shared-library

## Step 1: Resolve the entry node
Identify the starting node clearly.

Examples:
- mfe: rm-onboarding-mfe
- mfe route: /onboarding/review
- microservice: onboarding-service
- api-endpoint: POST /onboarding/update
- kafka-topic: onboarding.updated
- db-table: onboarding_db.onboarding_case
- shared-library: audit-lib

Return:
- normalized entry node
- entry type
- confidence
- initial evidence

## Step 2: Discover direct lineage
Based on entry type, discover the nearest architectural relationships.

### If entry type is mfe
Discover:
- routes/screens
- entry components
- api clients
- backend endpoints called
- frontend shared libs
- guards/entitlement hooks

### If entry type is microservice
Discover:
- controllers/endpoints
- downstream rest clients
- kafka topics produced/consumed
- db/entities/tables
- shared libraries
- security/audit integrations

### If entry type is api-endpoint
Discover:
- owning client if visible
- owning controller/service
- upstream callers if inferable
- request/response model
- downstream service/data/event effects

### If entry type is kafka-topic
Discover:
- producers
- consumers
- payload types if visible
- upstream business systems
- downstream business systems

### If entry type is db-table
Discover:
- owning service/repo/entity
- migrations
- read/write usage
- upstream APIs/services affecting it

### If entry type is shared-library
Discover:
- consuming services/MFEs
- runtime role
- spring autoconfiguration/runtime hooks if applicable
- impacted architectural layers

## Step 3: Expand recursively
Walk the lineage outward up to configured depth.

At each node, inspect:
- rest dependencies
- kafka dependencies
- db dependencies
- library dependencies
- integration dependencies

For each discovered node:
- normalize name
- classify relationship
- record confidence
- record evidence
- avoid duplicate nodes

## Step 4: Build layered lineage view
Group discovered lineage into layers:

### Layer 1: MFE / UI
### Layer 2: API
### Layer 3: Service
### Layer 4: Kafka / Messaging
### Layer 5: Database / Tables
### Layer 6: Shared Libraries
### Layer 7: External / Integration Dependencies

## Step 5: Build edge list
For each relationship, create a lineage edge with:
- source
- relationship type
- target
- confidence
- evidence
- direct/indirect flag

## Step 6: Mark uncertainty
Clearly separate:
- confirmed lineage
- possible lineage
- unresolved lineage

## Step 7: Generate outputs
Generate:
- lineage summary
- layered lineage view
- edge list
- key dependency hotspots
- open questions

Optional generated artifacts:
- playbooks/architecture/repo-to-system-map.md updates
- architecture/system-lineage/<entry>.md
- graph-engine ingest payload

## Output format

### Entry Node
- type
- name
- reason

### Lineage Summary
Short summary of direct and indirect lineage discovered.

### Layered Lineage
#### MFE / UI
#### API
#### Service
#### Kafka / Messaging
#### Database / Tables
#### Shared Libraries
#### External / Integration

### Lineage Edges
For each edge:
- source
- relationship
- target
- confidence
- evidence

### Dependency Hotspots
Highlight:
- shared libraries with broad impact
- shared tables/topics
- cross-system chains
- high-risk integration points

### Risks / Uncertainty
List weak or unresolved areas.

## Constraints
- do not guess unsupported lineage
- do not treat every internal helper as an architectural node
- keep direct and indirect lineage separate
- keep evidence visible
- limit recursion to useful depth unless explicitly asked