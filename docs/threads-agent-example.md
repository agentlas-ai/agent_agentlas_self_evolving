# Threads Agent Example

This example turns a Threads/SNS operator into a concrete self-evolution pattern.
It is designed for an owned account and approved posting workflow. It does not
justify credential capture, anti-abuse bypass, deceptive engagement, or
cross-account memory sharing.

## Hierarchy

```text
Appbridge Threads Agent (CEO)
  -> Threads Voice & Copy Skill
      -> Learned Voice (reference memory)
  -> Threads Browser Runtime Skill
      -> Learned Runtime (reference memory)
  -> Threads Hourly Operator Skill
  -> Threads Skill Evolver Skill
```

The important design choice is that `Learned Voice` and `Learned Runtime` are
reference artifacts, not free-roaming agents. They help their parent skills
improve while staying scoped, reviewable, and reversible.

## Why This Fits Self-Evolution

Threads-style account operation is a high-fit case because the work repeats:
draft posts, review voice, operate a known browser surface, observe responses,
and update the next run. The environment gives external feedback through user
corrections, post quality review, failed browser actions, reply outcomes, and
operator logs.

It is still not an unrestricted `EVOLVE` case. The right default is
`CONSTRAIN` moving toward `EVOLVE` for learned references, while account
permissions and live posting authority remain CEO or human-review boundaries.

## Role Contracts

| Node | Role | Evolves | Locked boundary |
|---|---|---|---|
| Appbridge Threads Agent | CEO, account owner, final policy | mission brief, approved cadence, escalation rules | credentials, account ownership, safety policy |
| Threads Voice & Copy Skill | Draft posts and replies in the account voice | hooks, rhythm, phrase bank, topic framing, revision rules | false claims, disclosure policy, private data |
| Learned Voice | Reference memory for the voice skill | approved examples, rejected examples, tone tags | raw private conversations, unrelated brand voices |
| Threads Browser Runtime Skill | Operate the web surface safely | selectors, navigation recipes, modal handling, safe-stop rules | anti-abuse bypass, rate-limit evasion, credential storage |
| Learned Runtime | Reference memory for browser operation | selector map, UI-state notes, failure recoveries | secrets, session tokens, cross-account paths |
| Threads Hourly Operator Skill | Run the cadence loop | queue order, skip logic, review checklist | posting when queue is weak, spam cadence |
| Threads Skill Evolver Skill | Propose bounded improvements | voice/rule/runtime diffs, tests, promotion records | direct live promotion without review |

## Evolution Targets

### Voice & Copy

Can evolve:

- opening hooks;
- sentence length and line-break rhythm;
- recurring phrases to use or avoid;
- reply tone;
- topic-to-angle mapping;
- CTA restraint;
- examples of approved and rejected drafts.

Must not evolve automatically:

- claims that require current factual verification;
- legal, financial, medical, or safety claims;
- identity, disclosure, or sponsorship rules;
- private user or customer details.

### Browser Runtime

Can evolve:

- selector fallback map;
- navigation recipe;
- draft-only smoke flow;
- popup and empty-state handling;
- safe-stop behavior when login expires;
- screenshot/evidence capture checklist.

Must not evolve automatically:

- credentials;
- session tokens;
- bypasses for anti-abuse controls;
- rate-limit evasion;
- cross-account automation.

### Hourly Operator

Can evolve:

- when to draft, post, reply, observe, or skip;
- queue prioritization;
- stale-topic detection;
- review checklist;
- evidence bundle for the next skill-evolver run.

Must not evolve automatically:

- posting outside the approved cadence;
- responding to sensitive replies without review;
- widening account scope;
- optimizing only for volume.

### Skill Evolver

Can evolve:

- proposed changes to skill text;
- learned voice entries;
- learned runtime entries;
- holdout tests;
- rollback records.

Must not evolve automatically:

- live account permissions;
- browser credentials;
- safety policy;
- final CEO approval rules.

## Fitness Function

The objective should reward useful operation, not raw engagement:

```text
threads_fitness =
  voice_match
+ draft_acceptance_rate
+ useful_reply_rate
+ browser_success_rate
+ safe_skip_quality
+ evidence_quality
- brand_drift
- repetition
- correction_rate
- failed_runtime_actions
- policy_risk
- spam_risk
```

High posting volume is not a success metric by itself. A good hourly operator
should sometimes decide not to post.

## Evolution Loop

```text
hourly run
  -> draft or observe
  -> browser/runtime evidence
  -> user corrections and approval notes
  -> skill evolver proposal
  -> holdout voice/runtime tests
  -> CEO or human approval
  -> learned reference update
```

## Decision Record Example

```yaml
decision_id: threads_voice_001
verdict: CONSTRAIN
target_skill: Threads Voice & Copy Skill
allowed_change:
  - add three approved hook patterns
  - add two rejected over-promotional patterns
blocked_change:
  - no live posting permission change
  - no claims about product metrics without source check
evidence:
  - "User accepted 8 of 10 drafts using short first-line hooks."
  - "User rejected 3 drafts for sounding too generic."
holdout:
  - "Generate 5 drafts on unseen topics and compare against learned voice."
rollback:
  - "Remove learned_voice entries added by threads_voice_001."
```

## Verdict

This pattern is a strong self-evolution candidate when:

- the account boundary is clear;
- the browser runtime is draft-safe before live actions;
- `Learned Voice` and `Learned Runtime` are scoped references;
- the skill evolver proposes diffs rather than silently mutating behavior;
- live posting and account permissions remain review-gated.

Verdict: `CONSTRAIN` moving toward `EVOLVE` for learned references, with
`HUMAN_REVIEW` for live posting authority and permission changes.
