# PRD Template

## Purpose
Provide a standard product requirement document template that Windsurf can generate, update, and link back to Jira.

## Usage
Use for:
- medium/large features
- cross-team changes
- changes with multiple impacted systems
- changes with compliance, security, data, or rollout implications

---

# Product Requirement Document

## 1. Title
Clear feature or change title.

## 2. Problem Statement
What problem are we solving?
What pain point, gap, inefficiency, or risk exists today?

## 3. Background / Context
Why now?
What changed in business, regulation, user expectation, architecture, or operations?

## 4. Business Goal
What business outcome is expected?
Examples:
- reduce manual steps
- improve turnaround time
- improve validation quality
- reduce operational risk

## 5. Stakeholders
List:
- product owner
- engineering owner
- business team
- downstream consumers
- risk/compliance/security stakeholders if relevant

## 6. Users / Actors
Who interacts with this change?
Examples:
- RM
- operations staff
- end customer
- internal service
- downstream system

## 7. In Scope
List what is included.

## 8. Out of Scope
List what is explicitly excluded.

## 9. Functional Requirements
Describe expected behavior clearly.
Prefer numbered requirements.

Example:
1. System must validate X before Y.
2. System must display Z when status is invalid.
3. System must persist audit context for field changes.

## 10. Non-Functional Requirements
Capture items such as:
- performance
- reliability
- auditability
- observability
- backward compatibility
- resiliency
- scalability

## 11. User Journey / Flow
Describe the main interaction flow.
Where useful, include:
- happy path
- exception path
- validation path

## 12. Data / API / Integration Impact
Document:
- API request/response changes
- DB or schema implications
- event changes
- upstream/downstream impact
- migration or compatibility implications

## 13. Security / Compliance / Audit Considerations
Capture:
- entitlement impact
- sensitive data handling
- audit requirements
- document/file handling concerns
- regulatory or compliance implications

## 14. Dependencies
List:
- systems
- teams
- approvals
- external services
- data readiness
- release dependencies

## 15. Assumptions
List assumptions currently being made.

## 16. Open Questions
List unanswered items that could affect implementation.

## 17. Acceptance Criteria
List testable business acceptance criteria.

## 18. Delivery Streams
Identify likely workstreams:
- backend
- frontend
- integration
- testing
- release/config
- documentation
- migration

## 19. Risks
Document:
- delivery risk
- technical risk
- operational risk
- dependency risk
- release risk

## 20. Rollout / Rollback Considerations
Document:
- phased rollout or toggle needs
- release sequencing
- fallback or rollback expectations
- production validation expectations

## 21. Success Metrics
How will success be measured?
Examples:
- defect reduction
- SLA improvement
- fewer manual corrections
- faster completion time
- increased validation coverage

## 22. Linked Jira Items
List:
- epic
- story
- task references
- related bug tickets

## 23. Appendix
Optional:
- examples
- mockups
- sample payloads
- reference screenshots
- linked documents

---

## PRD Generation Rules
When Windsurf generates a PRD:
- do not invent unsupported business rules
- separate confirmed facts from assumptions
- mark missing information explicitly
- keep language clear and enterprise-friendly
- avoid implementation-level design unless required