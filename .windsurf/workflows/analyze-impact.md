---
title: Analyze Impact
description: Analyze the blast radius of a Jira story or PRD and identify impacted areas, risks, delivery streams, and planning inputs.
---

# Analyze Impact Workflow

## Goal
Create a structured impact analysis before implementation planning starts.

## Inputs expected
- Jira story key
- Jira issue content
- PRD if available
- linked comments or artifacts if available
- playbooks/sdlc/impact-analysis-policy.md
- relevant architecture or service context if available

## Steps

### 1. Understand the requested change
Summarize:
- business goal
- expected behavior change
- scope boundaries
- assumptions still present

### 2. Identify confirmed impacted areas
List areas directly evidenced by the story, PRD, or known architecture context.

Consider:
- user flow
- service/component
- API
- DB
- events/integrations
- security/entitlement
- audit/compliance
- testing
- release/operations

### 3. Identify possible impacted areas
List likely but unconfirmed impact areas.

Mark clearly as:
- possible impact
- needs confirmation

### 4. Assess compatibility impact
Check:
- request/response compatibility
- consumer impact
- event compatibility
- schema coexistence risk
- rollout order concerns

### 5. Assess banking/enterprise risk areas
Check explicitly:
- entitlement/security impact
- audit/compliance impact
- sensitive data handling
- operational/release risk

### 6. Assess testing impact
Determine likely:
- unit test needs
- integration test needs
- contract/regression test needs
- negative path needs

### 7. Identify delivery streams
Recommend workstreams likely required:
- backend-api
- validation
- frontend
- integration
- migration
- entitlement/security
- audit
- testing
- release
- documentation

### 8. Produce planning hints
For each major impact item, suggest:
- what implementation area will likely need planning
- what category of task will likely be needed later

## Output format

### Requirement Summary
Short technical restatement.

### Confirmed Impacted Areas
List confirmed items only.

### Possible Impacted Areas
List possible items that need confirmation.

### Compatibility Impact
State backward compatibility and consumer risk.

### Security / Entitlement Impact
State confirmed and possible security/access implications.

### Audit / Compliance Impact
State confirmed and possible audit implications.

### Data / DB Impact
State schema/storage/migration implications.

### Integration / Event Impact
State downstream/upstream/event implications.

### Testing Impact
State likely validation and regression scope.

### Release / Operational Impact
State rollout, rollback, config, and support implications.

### Delivery Streams
List likely workstreams.

### Risks
Group by High / Medium / Low.

### Planning and Task Creation Hints
For each major impact item, include:
- impact item id
- short description
- likely implementation stream
- likely task types

## Constraints
- do not invent facts not supported by the story, PRD, or known architecture context
- separate confirmed impact from possible impact
- do not jump into detailed implementation design
- do not create Jira tasks in this workflow
- make the output actionable for the next workflow

## Correlation rule
The next workflow, generate-implementation-plan, must consume this output.
The task-creation workflow must trace created tasks back to these impact items where practical.