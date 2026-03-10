# Architecture Decision Template

## Purpose
Provide a standard decision record for introducing a new microservice, new MFE, or new architectural boundary.

---

# Architecture Decision

## 1. Title
Short, outcome-focused title.

Example:
Introduce suitability-decision-service and rm-suitability-review-mfe

## 2. Status
- Proposed
- Approved
- Rejected
- Superseded

## 3. Date
YYYY-MM-DD

## 4. Related Artifacts
- Jira story:
- PRD link:
- Impact analysis link:
- Related Jira items:
- Related documents:

## 5. Context
Describe:
- the business/problem context
- why the change is needed
- why this is not a simple enhancement to an existing system

## 6. Decision Summary
State clearly:
- create new microservice: yes/no
- create new MFE: yes/no
- create supporting shared module only: yes/no

## 7. Proposed Systems

### New Microservice
- Name:
- Purpose:
- Team owner:
- Primary domain:
- Why this boundary exists:

### New MFE
- Name:
- Purpose:
- Team owner:
- Primary route/journey:
- Why this boundary exists:

## 8. Ownership Boundaries
Define:

### In Scope Ownership
- what this system owns
- what APIs/routes/events it owns
- what business rules it owns
- what data it owns

### Out of Scope
- what remains with existing systems
- what this system must not absorb

## 9. Integration Boundaries
List:
- upstream callers
- downstream services
- events produced
- events consumed
- shared modules/platform dependencies
- shell integration points for MFE

## 10. API / UI Contract Boundary

### Microservice Contracts
- exposed endpoints:
- request/response responsibility:
- error model:
- versioning/compatibility note:

### MFE Contracts
- routes/screens:
- shell registration needs:
- backend client dependencies:
- entitlement/guard expectations:

## 11. Data Ownership and Persistence
- source of truth:
- schema/storage ownership:
- migration need:
- coexistence with old model:
- retention/compliance notes:

## 12. Security / Entitlement Considerations
- roles affected:
- authorization model:
- privileged actions:
- approval implications:
- sensitive data handling notes:

## 13. Audit / Compliance Considerations
- audit events required:
- before/after capture required:
- actor/context capture:
- operational/compliance reporting notes:

## 14. Operational Considerations
- logging expectations:
- metrics:
- tracing:
- deployment/runtime expectations:
- support model:
- post-release watchpoints:

## 15. Rollout / Adoption Strategy
- initial release scope:
- migration path:
- coexistence plan:
- feature flag/staged rollout:
- communication/dependency plan:

## 16. Rollback / Fallback Strategy
- rollback possible: yes/no/conditional
- rollback constraints:
- fallback behavior:
- data/schema rollback note:

## 17. Alternatives Considered

### Option 1: Extend Existing System
- summary:
- pros:
- cons:
- why not chosen:

### Option 2: Add Bounded Module in Existing Repo
- summary:
- pros:
- cons:
- why not chosen:

### Option 3: Create New System
- summary:
- pros:
- cons:
- why chosen:

## 18. Consequences
State expected consequences:
- delivery complexity
- operational overhead
- ownership clarity
- future extensibility
- dependency impact

## 19. Risks and Mitigations
For each major risk:
- risk:
- impact:
- mitigation:

## 20. Recommendation
Final recommendation in one paragraph.

## 21. Approval
- Product owner:
- Engineering owner:
- Architecture reviewer:
- Security/compliance reviewer if needed: