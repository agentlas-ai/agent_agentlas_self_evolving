---
name: threads-agent-evolution
description: Govern a Threads/SNS account operator whose voice, browser runtime, hourly cadence, and skill-evolver loop improve through scoped references.
---

# Threads Agent Evolution

Use this skill when the target workflow is a Threads, SNS, social account, or
browser-operated posting agent.

## Inputs

- Account boundary and owner.
- Current voice/copy skill.
- Learned voice reference, if present.
- Browser runtime skill.
- Learned runtime reference, if present.
- Hourly operator cadence.
- Skill-evolver promotion rules.
- User corrections, draft approvals, browser failures, and post/reply evidence.

## Steps

1. Confirm the workflow is for an owned or approved account.
2. Separate skills from learned references.
3. Classify evolution targets:
   - voice/copy;
   - browser runtime;
   - hourly cadence;
   - skill-promotion rules.
4. Lock credentials, account permissions, anti-abuse boundaries, disclosure
   policy, and live posting authority.
5. Require holdout tests for learned voice and safe browser-runtime replay.
6. Return `EVOLVE`, `CONSTRAIN`, `DO_NOT_EVOLVE`, or `HUMAN_REVIEW`.

## Safe-To-Evolve Candidates

- Approved and rejected voice examples.
- Hook and line-break patterns.
- Topic framing.
- Reply tone.
- Selector fallback map.
- Draft-only browser smoke flow.
- Popup and empty-state handling.
- Hourly skip logic.
- Promotion record format.

## Locked Or Human-Review Candidates

- Credentials and session tokens.
- Anti-abuse or rate-limit bypass.
- Cross-account memory.
- Deceptive engagement.
- Posting outside the approved account boundary.
- Sensitive replies.
- Live posting permission changes.

## Output Contract

```text
Verdict:
Account boundary:
Allowed evolution:
Learned voice update:
Learned runtime update:
Cadence update:
Locked variables:
Required holdout tests:
Approval gate:
Rollback:
Reason:
```

## Rule

Learn references first. Promote live behavior later. A Threads agent should get
better at drafting, remembering voice, and stopping safely before it gets more
authority to post.
