# Agent Hierarchy

This repo uses visible roles so teams can implement the Evolution Governor
without hiding authority inside one prompt.

```text
00 System Chair
  -> 10 Evolution Governor
      -> 20 Target Agent
      -> 30 Evaluator
      -> 40 Memory Curator
```

Lower numbers set mission, policy, and permission boundaries. Higher numbers
produce evidence, execute bounded work, or manage memory artifacts.

## Roles

- [00-system-chair](00-system-chair/agent.md): owns mission, permission, and
  final escalation policy.
- [10-evolution-governor](10-evolution-governor/agent.md): decides whether and
  how evolution is allowed.
- [20-target-agent](20-target-agent/agent.md): performs the recurring workflow
  under review.
- [30-evaluator](30-evaluator/agent.md): provides external feedback and holdout
  checks.
- [40-memory-curator](40-memory-curator/agent.md): manages scoped memory,
  expiry, contradiction, and deletion.
