# Story Quality Policy

## Purpose
Define how Jira stories are assessed for quality, readiness, risk visibility, and implementation fitness before engineering starts.

## Scope
Applies to:
- user stories
- feature tasks
- change requests
- bugs with implementation impact
- technical stories where product or engineering requirements must be clarified

## Objectives
A high-quality story should:
- clearly state the business goal
- define expected behavior
- be implementable without major guesswork
- be testable
- expose major risks and dependencies
- be traceable through design, build, review, and release

## Assessment Dimensions

### 1. Business Clarity
Check whether the story explains:
- what problem is being solved
- who benefits or who is affected
- expected outcome
- why the change is needed

Score guidance:
- 0 = no business context
- 1 = vague statement only
- 3 = understandable but incomplete
- 5 = clear, direct, outcome-oriented

### 2. Scope Clarity
Check whether the story clearly defines:
- in scope
- out of scope
- boundaries of the requested change
- whether multiple unrelated deliverables are bundled together

Score guidance:
- 0 = unclear or mixed scope
- 3 = partially bounded
- 5 = focused and well-bounded

### 3. Acceptance Criteria Quality
Check whether the story includes:
- explicit acceptance criteria
- observable expected behavior
- edge cases where relevant
- negative path or validation expectations where relevant

Score guidance:
- 0 = no acceptance criteria
- 3 = generic acceptance criteria
- 5 = concrete, testable, implementation-supportive criteria

### 4. Engineering Implementability
Check whether engineering can infer:
- impacted systems or modules
- API or integration implications
- data or DB implications if applicable
- backward compatibility concerns
- feasibility without major clarification

Score guidance:
- 0 = engineering cannot start safely
- 3 = implementation possible with assumptions
- 5 = implementation path is reasonably inferable

### 5. Risk and Compliance Readiness
Check whether the story surfaces:
- security or entitlement impact
- audit/compliance impact
- data sensitivity
- file/document handling implications
- operational or release risk

Score guidance:
- 0 = risky change with no risk visibility
- 3 = some risk called out
- 5 = major risk areas visible

### 6. Testability and Release Readiness
Check whether the story supports:
- test design
- validation planning
- rollout planning if needed
- rollback considerations for risky changes

Score guidance:
- 0 = cannot define validation safely
- 3 = partial testability
- 5 = clear validation and release thinking possible

## Scoring Model
Each dimension is scored from 0 to 5.

Total maximum = 30.

### Classification
- 26–30 = Ready
- 21–25 = Ready with warnings
- 15–20 = Needs clarification
- 0–14 = Not ready

## Blocker Conditions
A story is automatically not ready if any of the following apply:
- no meaningful business objective
- no acceptance criteria
- no owner
- multiple unrelated deliverables bundled together
- sensitive/risky change with no security/risk note
- story is too vague to identify likely impacted areas

## Required Story Content
The following should exist directly in Jira fields or linked artifacts:

- Summary
- Business Objective
- Acceptance Criteria
- Owner / Assignee or owning team
- Dependencies or explicit “none known”
- Impacted Systems or modules if known
- Risk Notes for sensitive work
- PRD link or equivalent for larger work
- Design Note link for non-trivial work

## Recommended Additional Content
- In Scope
- Out of Scope
- Test Notes
- Rollout / Rollback Notes
- Linked Confluence or design docs
- Sample request/response or UI references
- NFR notes

## Story Types and Adjustments

### Small Change
Expect lightweight content, but still require:
- clear goal
- acceptance criteria
- owner
- bounded scope

### Medium/Large Feature
Require:
- PRD or equivalent
- impacted systems
- dependencies
- rollout thinking
- testing considerations

### Bug
May allow simpler structure, but still require:
- observed issue
- expected behavior
- reproducibility or evidence
- fix scope

### Technical Story
Must state:
- technical problem
- business/operational justification
- success outcome
- impact if not done

## Output of Assessment
The story-quality workflow should return:

### Story Quality Summary
- overall score
- readiness classification

### Dimension Scores
- business clarity
- scope clarity
- acceptance criteria quality
- engineering implementability
- risk/compliance readiness
- testability/release readiness

### Missing Information
List specific missing items.

### Risks
List major delivery or operational risks.

### Recommendation
One of:
- ready
- ready with warnings
- revise
- split into multiple stories
- escalate for clarification

## Review Cadence
Review this policy monthly during pilot and quarterly after stabilization.