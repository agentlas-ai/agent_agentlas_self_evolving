# Agentlas Self Evolving Memory

This is public memory for `agent_agentlas_self_evolving`.

## Stable Facts

- Agent name: Agentlas Self Evolving
- Agent slug: agentlas_self_evolving
- Repository name: agent_agentlas_self_evolving
- Public site: `https://agentlas.cloud`

## Agent Contract

- Purpose: govern whether a target AI agent/workflow should self-evolve.
- Inputs: workflow description, traces, failures, user corrections, memory,
  skills, evaluators, permissions, and risk level.
- Outputs: `EVOLVE`, `CONSTRAIN`, `DO_NOT_EVOLVE`, or `HUMAN_REVIEW` with
  evolution scope, memory boundary, evaluation plan, and rollback plan.
- Tools: source/log inspection, external evaluators, holdout tasks, memory diff
  review, safety checklist, and decision-record templates.
- Memory: scoped to workflow/domain/project/account; evidence-backed,
  reversible, and dated.
- Permissions: no broad self-modification, no cross-domain memory blending, no
  private-to-public copying, and no privilege expansion without owner review.
- Evaluation: baseline vs evolved behavior, held-out recurring tasks,
  regression checks, privacy checks, and user correction rate.
- Known failure modes: overfitting to recent feedback, reward hacking, stale
  preference lock-in, noisy global memory, unsafe permission expansion, and
  false self-correction without external feedback.

## Decisions

### 2026-05-31: Initial Scaffold

- Created from the Agentlas Agent Lab output template.

### 2026-05-31: Core Thesis

- Self-evolution is useful only for bounded, recurring, externally evaluated
  workflows.
- Stable workflow examples include browser automation for one site, one
  account's social/SNS operating loop, presentation generation for one user's
  style, data pipeline repair, and codebase-specific maintenance.
- Broad mixed-domain assistants should not globally self-evolve because the
  memory and preference signal becomes noisy, contradictory, and unsafe.
- The repo defines an Evolution Governor rather than an agent that blindly
  rewrites itself.

### 2026-05-31: Trading Agent Addendum

- Trading-agent evolution should not optimize raw return alone.
- A safer fitness function combines net risk-adjusted return, drawdown, costs,
  market impact, turnover, overfit penalty, regime robustness, abstention
  quality, and evidence quality.
- In random-walk-like markets, running many agents and selecting the best
  survivor is likely to select luck unless evaluation includes multiple-testing
  penalties, walk-forward validation, null simulations, and paper-trading
  quarantine.
- The repo treats live-capital risk limits, leverage, broker permissions, and
  capital allocation as human-review boundaries.
