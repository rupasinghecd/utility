# Implementation Plan Template

## Purpose
Provide a standard template for converting a Jira story or PRD into a practical engineering implementation plan.

---

# Implementation Plan

## 1. Title
Clear name of the implementation change.

## 2. Source Artifacts
List:
- Jira story key
- PRD link
- related Jira items
- related Confluence/docs

## 3. Requirement Summary
Restate the requirement in engineering-friendly language.

## 4. Scope of Implementation
List what must be implemented.

## 5. Out of Scope
List what is intentionally excluded.

## 6. Impacted Components
Identify likely impact across:
- backend services
- frontend apps / MFEs
- APIs
- DB / schema
- events / queues
- integrations
- config
- auth / entitlement
- audit/logging
- observability

## 7. Proposed Approach
Describe the preferred implementation path.
Keep it low-risk and aligned to existing patterns.

## 8. Design Considerations
Capture:
- backward compatibility
- validation rules
- error handling
- idempotency if relevant
- concurrency/order concerns if relevant
- data consistency
- performance concerns

## 9. Test Strategy
List:
- unit tests
- integration tests
- contract tests
- UI tests if needed
- negative-path validation
- regression checks

## 10. Release Strategy
List:
- feature flag or not
- migration sequencing
- config dependencies
- environment rollout order
- fallback approach

## 11. Risks and Mitigations
For each major risk:
- risk
- impact
- mitigation

## 12. Assumptions
List current assumptions.

## 13. Open Questions
List unresolved items requiring clarification.

## 14. Recommended Task Breakdown
List proposed tasks grouped by stream:
- backend
- frontend
- integration
- testing
- release
- documentation

## 15. Definition of Done for This Change
State what must be true before the work is considered complete.

---

## Plan Generation Rules
When Windsurf generates an implementation plan:
- prefer extending existing patterns
- avoid overdesign
- state assumptions clearly
- identify likely impacted files/modules if enough evidence exists
- separate confirmed impact from possible impact