<p align="center">
  <img src="assets/agentlas-agent-lab-banner.svg" alt="Agentlas Agent Lab banner">
</p>

<h1 align="center">Agentlas Self Evolving</h1>

<p align="center">
  <a href="https://github.com/jeongmk522-netizen/Agentlas_public_repo">Lab Hub</a>
  |
  <a href="https://agentlas.cloud">agentlas.cloud</a>
  |
  <a href="https://github.com/jeongmk522-netizen/agent_agentlas_self_evolving">agent_agentlas_self_evolving</a>
</p>

<p align="center">
  A research repo and agent contract for deciding when an AI agent should evolve
  itself, when it should only remember scoped preferences, and when evolution
  should be blocked.
</p>

## Abstract

Self-evolution is not automatically good. It is useful when an agent repeatedly
operates in the same domain, receives trustworthy feedback, and can improve a
bounded skill, memory, prompt, policy, or evaluator without corrupting unrelated
work. It becomes harmful when the agent serves many unrelated goals, has weak or
gameable feedback, mixes private contexts, or turns every user interaction into
global memory.

This repository argues for a fitness boundary. Self-evolution should be treated
as a governed control loop, not as a personality trait. A browser automation
agent that repeatedly operates the same web app can safely learn selectors,
account preferences, retry policies, and failure patterns. A presentation agent
can learn a user's slide style, title density, visual rhythm, source citation
rules, and revision preferences. A generic assistant that jumps from investing
to legal drafting to creative brainstorming to family logistics should not blend
all of those histories into one evolving identity. That is not wisdom; it is
context pollution with confidence.

The proposed agent is an Evolution Governor. It does not blindly improve itself.
It audits a target agent or workflow and returns one of four verdicts:
`EVOLVE`, `CONSTRAIN`, `DO_NOT_EVOLVE`, or `HUMAN_REVIEW`. The verdict depends
on task recurrence, feedback quality, memory ownership, reversibility, safety
risk, and evaluation coverage.

## Research Question

When does self-evolution make an agent better, and when does it add noise,
conflict, or unsafe optimization pressure?

## Thesis

An agent should self-evolve only when all five conditions hold:

1. The workflow recurs often enough for learned behavior to pay rent.
2. The environment has external feedback that is harder to fake than text
   self-approval.
3. The improvement target is bounded: a skill, memory schema, prompt, routing
   rule, test, or evaluator.
4. Every change is logged, reversible, and evaluated against holdout tasks.
5. The memory belongs to a domain, project, account, or agent role rather than
   to an unbounded global persona.

If those conditions do not hold, the right pattern is not self-evolution. It is
either scoped memory, a one-off research note, a human decision, or no durable
update at all.

## Where Self-Evolution Helps

| Workflow | Why it fits | Evolution target |
|---|---|---|
| Playwright-style browser operator for one site | Stable selectors, repeated flows, observable failures | selectors, retries, navigation recipes, account preferences |
| Social/SNS operations for one account and campaign type | Repeated platform patterns and measurable post outcomes | posting checklist, tone memory, compliance guardrails, timing heuristics |
| Presentation agent for one user's style | Strong recurring preference signal and inspectable output | layout rules, citation style, title density, visual constraints |
| Data pipeline repair agent | Deterministic logs, tests, schema drift, run history | runbook skills, alert triage, schema checks |
| Codebase-specific maintenance agent | Stable repo conventions and executable tests | local conventions, patch templates, validation matrix |
| Trading research agent in paper/live-sim mode | Repeated market decision loop with measurable outcomes, but high overfit risk | hypothesis discipline, risk constraints, abstention rules, evaluation protocol |

## Where Self-Evolution Hurts

| Workflow | Failure mode | Safer pattern |
|---|---|---|
| General assistant across unrelated life/work domains | Context blending, stale preferences, false continuity | per-project memory with explicit boundaries |
| One-off strategy or creative exploration | Premature canonization of guesses | dated notes, no automatic memory write |
| High-stakes legal, medical, financial decisions | Reward hacking, privacy risk, stale policy | human review and source-grounded checklists |
| Tasks with no reliable evaluator | Self-praise loop and drift | external verifier first, then consider evolution |
| Cross-client or cross-account operations | Confidentiality leakage | tenant-scoped memory and permission isolation |
| Live-capital trading agent changing its own leverage or broker permissions | Ruin risk and objective gaming | governance lock, paper trading, human approval |

## Trading-Agent Addendum

A stock-trading agent is a special case because the obvious objective function,
"make more money," is too easy to game. Raw return rewards leverage, hidden tail
risk, excessive turnover, and lucky backtests. A trading agent's fitness should
therefore treat profit as the final ecological signal, not the only training
objective. This section is agent-governance research, not investment advice.

Trading evolution should optimize a governed survival bundle:

```text
fitness =
  net risk-adjusted return
- drawdown and ruin risk
- turnover, fees, slippage, and market impact
- overfit and data-snooping penalty
- leverage and concentration penalty
+ regime robustness
+ abstention quality
+ evidence quality
```

The most promising target may not be a numeric parameter. In random-walk-like
markets, evolving more moving-average windows or more entry thresholds mainly
selects historical luck. A more useful evolution target is the agent's research
and survival phenotype: how it forms hypotheses, rejects weak edges, abstains
when no edge exists, sizes risk, handles regime shifts, and refuses to promote a
strategy without out-of-sample evidence.

See [docs/trading-agent-evolution.md](docs/trading-agent-evolution.md) for the
full research note.

## Agent Contract

- Purpose: decide whether a target agent/workflow should self-evolve, and design
  the smallest safe evolution loop if it should.
- Inputs: workflow description, task traces, failure cases, user feedback,
  current memory, available tests/evaluators, permission boundary, risk level.
- Outputs: fit verdict, evolution scope, memory boundary, evaluator plan,
  rollback plan, and an evolution decision record.
- Tools: source/log inspection, benchmark or holdout task runner, memory diff
  review, policy checklist, safety review.
- Memory: scoped, evidence-backed, reversible; no private logs, secrets, or
  unrelated project history.
- Permissions: no unreviewed broadening of access, no private-to-public copying,
  no self-modification outside the approved scope.
- Evaluation: compare baseline vs evolved behavior on recurring tasks and
  holdout tasks; track regressions, latency, privacy, and user correction rate.
- Known failure modes: overfitting to recent feedback, evaluator gaming,
  cross-domain memory contamination, silent skill drift, and irreversible
  preference lock-in.

## System Model

```text
Target workflow
  -> Evolution Governor
      -> Fit assessment
      -> Memory boundary audit
      -> Evaluation plan
      -> Decision record
          -> EVOLVE / CONSTRAIN / DO_NOT_EVOLVE / HUMAN_REVIEW
```

If the verdict is `EVOLVE`, the governor promotes only a bounded change:

```text
failure trace
  -> proposed skill or memory edit
  -> held-out validation
  -> rollback snapshot
  -> logged promotion
```

## Research Anchors

The design borrows from several adjacent lines of work:

- [Reflexion](https://arxiv.org/abs/2303.11366): language agents can improve
  across trials by storing verbal reflections in episodic memory, especially
  when feedback is available.
- [Voyager](https://arxiv.org/abs/2305.16291): open-ended agents can benefit
  from an automatic curriculum, executable skill library, environment feedback,
  and self-verification in a stable domain.
- [EvoSkill](https://arxiv.org/abs/2603.02766): failure traces can be converted
  into reusable skills, but promotion should depend on held-out validation.
- [EvoMemBench](https://arxiv.org/abs/2605.18421): memory is not universally
  helpful; the best memory form depends on task structure and context limits.
- [AlphaEvolve](https://arxiv.org/abs/2506.13131): evaluator-driven evolution is
  powerful when the objective can be measured and verified.
- [LLMs Cannot Self-Correct Reasoning Yet](https://arxiv.org/abs/2310.01798):
  self-correction without external feedback can degrade reasoning.
- [Concrete Problems in AI Safety](https://arxiv.org/abs/1606.06565): reward
  hacking, scalable supervision, safe exploration, and distribution shift are
  core risks for any optimizing loop.

## Repository Map

- [agent.md](agent.md): reusable Evolution Governor agent contract.
- [ARCHITECTURE.md](ARCHITECTURE.md): system architecture and decision flow.
- [AGENTS.md](AGENTS.md): Codex operating rules for this repo.
- [CLAUDE.md](CLAUDE.md): Claude Code guide for this repo.
- [memory.md](memory.md): public, scoped agent memory.
- [docs/literature-map.md](docs/literature-map.md): source-backed research map.
- [docs/fit-matrix.md](docs/fit-matrix.md): practical domain fit matrix.
- [docs/evaluation.md](docs/evaluation.md): metrics and experiment design.
- [docs/trading-agent-evolution.md](docs/trading-agent-evolution.md): trading
  agent addendum on profit, random walks, natural selection, and overfitting.
- [docs/research-log.md](docs/research-log.md): dated research notes.
- [templates/evolution-decision-record.md](templates/evolution-decision-record.md):
  promotion/blocking record template.
- [agents/](agents/): visible role hierarchy for implementation teams.
- [skills/](skills/): reusable operating skills for the governor.
