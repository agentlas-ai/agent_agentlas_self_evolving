---
name: evolution-decision-record
description: Write a concise, reviewable record for an approved, constrained, rejected, or escalated self-evolution change.
---

# Evolution Decision Record

Use this skill after an Evolution Governor verdict.

## Inputs

- Verdict.
- Target workflow.
- Evidence.
- Allowed and blocked scope.
- Evaluator.
- Holdout checks.
- Rollback plan.
- Owner.

## Steps

1. Copy the structure from `templates/evolution-decision-record.md`.
2. Fill only evidence-backed fields.
3. Keep the record understandable without reading the full transcript.
4. Include a rollback trigger.
5. Include an invalidation or review date for memory changes.
6. Link to evaluation evidence when available.

## Output Contract

```text
Decision ID:
Verdict:
Target workflow:
Allowed scope:
Blocked scope:
Evidence:
Evaluation:
Rollback:
Owner:
Reason:
```

## Rule

No decision record, no promotion.
