---
title: PR Review
description: Review a change set against team standards, risk, and requirement intent.
---

# PR Review Workflow

## Goal
Provide a disciplined engineering review before merge.

## Inputs expected
- diff or changed files
- original story or requirement
- relevant playbooks
- test updates if available

## Steps
1. Compare the diff against the requirement.
2. Check correctness of business logic.
3. Check for scope creep or unrelated changes.
4. Review:
   - security issues
   - data handling concerns
   - error handling gaps
   - backward compatibility risks
   - performance concerns
   - observability gaps
   - missing tests
5. Highlight what is good as well as what needs correction.
6. Prioritize findings by severity.
7. Suggest concrete fixes.

## Output format
### Summary
### What looks good
### Findings
#### High severity
#### Medium severity
#### Low severity
### Missing tests / validation
### Merge recommendation

## Constraints
- Be specific and evidence-based.
- Do not produce vague comments.
- Prefer a few high-quality findings over many weak ones.