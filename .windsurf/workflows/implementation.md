---
title: Implementation
description: Implement a requirement using existing project patterns and safe delivery practices.
---

# Implementation Workflow

## Goal
Implement the requested change with minimum risk and maximum alignment to existing standards.

## Inputs expected
- approved story or requirement
- relevant impacted files
- design note if available
- applicable AGENTS.md instructions
- testing expectations

## Steps
1. Restate the requirement and implementation scope.
2. Identify the smallest set of files that should change.
3. Reuse existing patterns before creating anything new.
4. Implement the change.
5. Update or add tests.
6. Review the change for:
   - correctness
   - error handling
   - validation
   - logging
   - backward compatibility
   - performance
7. Summarize changed files and assumptions.
8. Note rollout or config impact if relevant.

## Output format
### Scope implemented
### Files changed
### Key design decisions
### Tests added or updated
### Risks / follow-up items

## Constraints
- Do not make unrelated refactors.
- Do not change public contracts unless required.
- Do not skip tests without explicitly stating why.