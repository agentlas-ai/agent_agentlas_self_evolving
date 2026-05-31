# Threads Agent Blueprint

## Hierarchy

```text
Appbridge Threads Agent (CEO)
  -> Threads Voice & Copy Skill
      -> Learned Voice
  -> Threads Browser Runtime Skill
      -> Learned Runtime
  -> Threads Hourly Operator Skill
  -> Threads Skill Evolver Skill
```

## CEO Boundary

- Account:
- Owner:
- Posting authority:
- Reply authority:
- Review cadence:
- Stop conditions:
- Locked permissions:

## Threads Voice & Copy Skill

- Voice principles:
- Approved examples:
- Rejected examples:
- Claim rules:
- Sensitive-topic rules:
- CTA rules:
- Holdout test:

## Learned Voice

- Scope:
- Date learned:
- Evidence:
- Memory entry:
- Confidence:
- Invalidation rule:

## Threads Browser Runtime Skill

- Browser target:
- Draft-only flow:
- Safe-stop rules:
- Evidence capture:
- Known UI states:
- Runtime holdout test:

## Learned Runtime

- Scope:
- UI state:
- Selector or navigation note:
- Failure recovery:
- Evidence:
- Invalidation rule:

## Threads Hourly Operator Skill

- Run frequency:
- Queue source:
- Draft/post/reply/observe rules:
- Skip rules:
- Evidence bundle:
- Escalation rule:

## Threads Skill Evolver Skill

- Input artifacts:
- Allowed diffs:
- Blocked diffs:
- Holdout tests:
- Approval gate:
- Rollback:

## Fitness

```text
threads_fitness =
```

- Voice match:
- Draft acceptance:
- Useful reply:
- Browser success:
- Safe skip:
- Evidence quality:
- Brand drift penalty:
- Repetition penalty:
- Correction penalty:
- Runtime failure penalty:
- Policy risk penalty:
