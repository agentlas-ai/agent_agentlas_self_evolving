# Repository Decisions

## 2026-05-31: Use Agentlas Agent Lab Scaffold

The repo was created with the lab script:

```bash
scripts/new_output_agent_repo.sh agentlas_self_evolving "Agentlas Self Evolving"
```

The lab convention prefixes output repos with `agent_`, so the public output
path and remote name are `agent_agentlas_self_evolving`.

## 2026-05-31: Define An Evolution Governor

The seed question asked whether self-evolution is always good. The repo answers
by defining a governor rather than a self-mutating agent.

Reason: a self-mutating agent would assume the conclusion. A governor can say
yes, no, constrain, or escalate.

## 2026-05-31: Keep Examples Public And Generic

The repo uses public-safe examples such as browser automation, presentation
generation, SNS operations, data pipeline repair, and codebase maintenance. It
does not include private project logs, local file paths, credentials, or account
details.

## 2026-05-31: Add Trading-Agent Research Without Trading Advice

The trading section is framed as agent-governance research, not investment
advice. It does not name tickers, recommend strategies, or provide live-trading
instructions.

Reason: trading-agent self-evolution is a useful stress case for the repo's
core thesis, but live financial decisions are high-stakes and can be harmed by
reward hacking, overfitting, and permission expansion.

## 2026-05-31: Add Threads Agent Example

The repo now includes a concrete Threads/SNS example because it demonstrates a
good self-evolution boundary: copy voice and browser runtime can learn through
separate reference memories while account permissions, safety rules, and live
posting authority stay locked.

Reason: the user's hierarchy is a strong example of modular evolution. The
evolver does not rewrite the whole agent; it proposes scoped updates to voice,
runtime, cadence, or promotion rules.

## 2026-05-31: Promote The Work Into A Paper Artifact

The repo now treats `PAPER.md` as the canonical research artifact. Existing
README, docs, skills, and templates support the paper rather than replacing it.

Reason: the project is meant to be shared as a public research repo, so the
argument needs a single paper-shaped entry point before being posted publicly.
