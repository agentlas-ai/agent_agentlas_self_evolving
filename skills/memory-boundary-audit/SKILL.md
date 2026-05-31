---
name: memory-boundary-audit
description: Audit whether a proposed memory entry or self-evolution rule belongs in a scoped memory store or should be rejected.
---

# Memory Boundary Audit

Use this skill before promoting memory into an evolving agent.

## Inputs

- Proposed memory text.
- Source evidence.
- Target workflow.
- Storage location.
- Expiry or review policy.
- Privacy and account boundary.

## Steps

1. Identify the memory owner: project, account, site, repo, user, or role.
2. Check whether the memory came from repeated evidence or a one-off correction.
3. Remove raw logs, secrets, local paths, and private examples.
4. Add provenance, confidence, date, owner, and invalidation rule.
5. Check for domain contamination.
6. Return `PROMOTE`, `REVISE`, `REJECT`, or `HUMAN_REVIEW`.

## Output Contract

```text
Decision:
Scope:
Memory text:
Evidence:
Confidence:
Invalidation rule:
Reason:
```

## Rule

When in doubt, narrow the memory scope. A correct memory in the wrong scope is a
future bug.
