---
name: evolution-fit-assessment
description: Decide whether an AI agent workflow should self-evolve, be constrained, be blocked, or require human review.
---

# Evolution Fit Assessment

Use this skill when a user asks whether an agent, workflow, memory, prompt,
skill, or automation loop should improve itself over time.

## Inputs

- Target workflow.
- Recurrence evidence.
- Current feedback signals.
- Current memory and skills.
- Permission boundary.
- Risk level.
- Desired change.

## Steps

1. Describe the workflow in one sentence.
2. Rate recurrence: low, medium, or high.
3. Rate feedback quality: self-only, weak external, strong external.
4. Identify the smallest allowed change surface.
5. Check memory ownership: global, project, account, site, repo, or role.
6. Check rollback and holdout evaluation.
7. Check hard blockers: high-stakes risk, cross-tenant leakage, permission
   expansion, no evaluator, no rollback.
8. Return one verdict: `EVOLVE`, `CONSTRAIN`, `DO_NOT_EVOLVE`, or
   `HUMAN_REVIEW`.

## Output Contract

```text
Verdict:
Reason:
Allowed scope:
Blocked scope:
Evaluator:
Memory boundary:
Rollback:
Next action:
```

## Default Judgment

If the workflow is broad, mixed-domain, or evaluated only by the agent's own
reflection, return `DO_NOT_EVOLVE` or `CONSTRAIN`.
