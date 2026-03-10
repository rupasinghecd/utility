---
title: Generate PRD
description: Generate a PRD from a Jira story and linked context, following the team PRD template.
---

# Generate PRD Workflow

## Goal
Create a structured PRD draft from Jira and related context.

## Inputs expected
- Jira story key
- story details
- epic details if available
- linked documents/comments if available
- playbooks/prd-template.md

## Steps
1. read the story and related context.
2. extract:
   - problem statement
   - business goal
   - scope
   - stakeholders
   - functional requirements
   - risks
   - dependencies
3. populate the PRD template.
4. mark assumptions and open questions explicitly.
5. keep unconfirmed details separate from confirmed requirements.
6. produce a PRD draft suitable for publishing into Confluence and linking back into Jira.

## Output format
Return a complete PRD using the template structure.

## Constraints
- do not invent unsupported business requirements
- if information is missing, fill the section with explicit placeholders or open questions
- avoid deep implementation design unless already confirmed