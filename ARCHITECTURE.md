# Agentlas Self Evolving Architecture

## Purpose

This repo defines an Evolution Governor: a public-safe agent contract for
deciding whether another AI agent or workflow should self-evolve.

The governor exists because self-evolution is not a universal upgrade. It is a
control loop that can improve stable workflows and damage mixed, noisy,
high-risk, or poorly evaluated workflows.

## Core Architecture

```text
Workflow under review
  -> Evidence intake
  -> Fit assessment
  -> Memory boundary audit
  -> Evaluation plan
  -> Safety and rollback review
  -> Decision record
  -> Verdict
```

The verdict is one of:

| Verdict | Meaning |
|---|---|
| `EVOLVE` | Promote a bounded, evaluated change. |
| `CONSTRAIN` | Evolution may help, but the scope or memory boundary is too broad. |
| `DO_NOT_EVOLVE` | Self-evolution is more likely to add noise or risk than value. |
| `HUMAN_REVIEW` | The decision has permission, safety, or high-impact consequences. |

## Roles

```text
System Chair
  -> Evolution Governor
      -> Target Agent
      -> Evaluator
      -> Memory Curator
```

### System Chair

Owns the mission boundary, permission boundary, and final approval policy. The
chair decides whether the governor is allowed to promote changes automatically
or only recommend them.

### Evolution Governor

Classifies the workflow, defines the allowed evolution target, requires external
feedback, writes the decision record, and blocks unsafe scope expansion.

### Target Agent

The agent or workflow being reviewed. It may be a browser operator, presentation
agent, social account operator, codebase maintainer, support agent, or another
repeated system.

### Evaluator

Provides feedback that is harder to fake than self-reflection. Examples include
tests, screenshots, task success metrics, human corrections, production logs,
lint/type checks, benchmark tasks, and rubric-based review.

### Memory Curator

Owns what gets remembered, what gets expired, what gets separated by domain, and
what must never be stored.

## Evolution Targets

Prefer small, inspectable targets:

- skill instructions
- memory schema
- retrieval tags
- prompt fragments
- routing policy
- evaluator rubric
- retry policy
- test cases
- runbook entries

Avoid broad targets by default:

- global personality
- unrestricted tool access
- model weights
- all-user memory
- cross-tenant memory
- hidden policy changes

## Decision Flow

1. Define the target workflow.
2. Identify recurrence: how often does the same class of task return?
3. Inspect feedback: what external signal proves improvement?
4. Bound the change: what is the smallest artifact that may evolve?
5. Audit memory: who owns it, where does it live, and when does it expire?
6. Design holdout checks: what tasks were not used to generate the change?
7. Classify risk: privacy, permission, financial, legal, medical, reputational.
8. Write the decision record.
9. Promote, constrain, block, or escalate.

## Promotion Gate

A change can be promoted only when:

- it improves the target metric on evaluation tasks;
- it does not regress holdout tasks;
- it stays inside the approved memory and permission boundary;
- rollback is possible;
- the decision record is understandable without reading a full transcript.

## Why Broad Agents Should Not Globally Evolve

A person may ask one assistant to do many unrelated things: inspect a website,
draft a legal letter, research stocks, polish a slide deck, plan family travel,
and debug code. If the assistant stores all feedback as one self-evolving
identity, it can merge incompatible preferences and policies.

The safer architecture is project/domain scoping:

```text
global assistant
  -> project memory: deck style
  -> site memory: browser automation
  -> account memory: SNS operations
  -> repo memory: codebase conventions
  -> no memory: one-off brainstorming
```

Self-evolution belongs where the loop is stable enough to learn.
