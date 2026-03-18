# System Lineage Discovery Policy

## Purpose
Define how architecture lineage is discovered from an entrypoint such as an MFE, microservice, API, Kafka topic, DB table, or shared library.

## Why This Exists
A simple list of impacted systems is not enough for impact analysis, task creation, release readiness, or architecture understanding.

Lineage discovery exists to show:
- what calls what
- what depends on what
- what data is read or written
- what events are produced or consumed
- what shared libraries influence runtime behavior

## Supported Entry Types
The discovery workflow must support these starting points:
- mfe
- microservice
- api-endpoint
- kafka-topic
- db-table
- shared-library

## Discovery Objectives
The workflow should build a practical lineage map covering:

### 1. UI / MFE Layer
- route ownership
- entry components
- api clients
- state/guard dependencies
- frontend shared libraries

### 2. API Layer
- http method
- endpoint path
- request/response models
- gateway or bff mapping if present

### 3. Service Layer
- service ownership
- controller mapping
- validation/business layer
- downstream rest clients
- security/audit hooks

### 4. Messaging Layer
- kafka topics produced
- kafka topics consumed
- event relationships

### 5. Data Layer
- databases
- schemas
- tables/entities
- read/write relationships
- migration ownership

### 6. Shared Library Layer
- internal reusable libraries
- spring boot starters
- common clients
- audit/security/logging libraries

### 7. Integration Layer
- external APIs
- internal downstream services
- storage/document systems
- cache/redis usage

## Discovery Rules

### Rule 1: Start from evidence
Do not infer a dependency unless code, config, metadata, or historical evidence suggests it.

### Rule 2: Separate direct vs indirect lineage
Mark whether the relationship is:
- direct
- indirect
- inferred

### Rule 3: Separate confirmed vs possible
Every discovered item must be marked:
- confirmed
- possible
- unknown owner

### Rule 4: Record evidence
For each lineage edge, record:
- evidence source
- file/module/config reference
- confidence

### Rule 5: Recurse with depth control
The workflow should support recursive discovery with configurable depth.

Suggested defaults:
- depth 1: direct dependencies only
- depth 2: one downstream hop
- depth 3: broader lineage
- beyond 3: only by explicit request

### Rule 6: Normalize names
Use normalized names for:
- services
- MFEs
- topics
- tables
- libraries

### Rule 7: Avoid noise
Do not treat every helper or utility class as an architectural dependency.
Focus on meaningful lineage items:
- deployable systems
- owned data stores
- shared libraries with platform/runtime effect
- actual integration boundaries

## Required Outputs

### A. Lineage Summary
Short summary of what was discovered.

### B. Entry Node
The node the discovery started from.

### C. Upstream Lineage
Who calls or uses the entry node, where inferable.

### D. Downstream Lineage
What the entry node calls, publishes to, writes to, or depends on.

### E. Layered View
Organize findings by:
- MFE
- API
- Service
- Kafka
- DB
- Library
- Integration

### F. Lineage Edges
Each edge should state:
- source node
- relationship type
- target node
- confidence
- evidence

### G. Risks / Uncertainty
State weak or inferred mappings clearly.

## Relationship Types
Use normalized relationship types such as:
- calls-rest
- handled-by
- publishes-topic
- consumes-topic
- reads-table
- writes-table
- uses-library
- registered-in-shell
- guarded-by
- depends-on-config
- integrates-with

## Confidence Levels

### High
Direct code/config evidence exists.

### Medium
Strong structural inference exists, but not fully proven.

### Low
Weak or secondary inference exists.

## Anti-patterns
Avoid:
- listing systems without showing relationships
- guessing DB or topic ownership from names alone
- flattening all lineage into one unreadable block
- recursing too deeply without value
- treating every transitive library as important

## Definition of Completion
Lineage discovery is complete when:
- the starting node is clear
- major direct dependencies are visible
- key downstream and data/event dependencies are visible
- confidence and evidence are recorded
- the output is usable for impact analysis and task creation