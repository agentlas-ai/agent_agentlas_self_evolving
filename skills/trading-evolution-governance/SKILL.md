---
name: trading-evolution-governance
description: Review whether a trading agent should self-evolve, what variables may change, and how to prevent overfit, leverage abuse, and false discovery.
---

# Trading Evolution Governance

Use this skill when the target workflow is a trading, portfolio, market
research, signal-generation, or execution agent.

This skill is for agent architecture and research governance. It is not
investment advice.

## Inputs

- Market and instrument universe.
- Trading horizon.
- Whether the workflow is backtest, paper trading, or live capital.
- Current objective function.
- Candidate evolvable variables.
- Cost, slippage, borrow/funding, and market-impact assumptions.
- Number of variants or agents searched.
- Risk limits and permission boundary.

## Steps

1. Reject raw return as the sole objective.
2. Build a survival fitness function: net risk-adjusted return, drawdown, tail
   loss, costs, turnover, leverage, concentration, overfit penalty, robustness,
   and abstention quality.
3. Classify variables as safe-to-evolve, review-required, or locked.
4. Require random-walk, shuffled-return, walk-forward, and holdout tests.
5. Require paper-trading quarantine before live promotion.
6. Treat live leverage, broker permissions, kill switches, and capital
   allocation as human-review or locked boundaries.
7. Return `EVOLVE`, `CONSTRAIN`, `DO_NOT_EVOLVE`, or `HUMAN_REVIEW`.

## Safe-To-Evolve Candidates

- Research prompts.
- Hypothesis templates.
- Falsification checklist.
- Abstention policy.
- Data-quality checks.
- Feature candidates in paper mode.
- Position-sizing proposals within fixed caps.
- Execution heuristics in simulation.

## Locked Or Human-Review Candidates

- Live capital allocation.
- Leverage limits.
- Broker credentials and permissions.
- Kill switches.
- Compliance policy.
- Objective function weights.
- Risk-budget expansion.

## Output Contract

```text
Verdict:
Trading mode:
Objective assessment:
Allowed evolution:
Locked variables:
Required tests:
Random-walk/null result:
Promotion rule:
Rollback/kill switch:
Reason:
```

## Rule

In random-walk-like markets, a large agent population should mostly learn to
abstain. If it keeps finding highly profitable survivors, suspect overfitting,
data leakage, or an unrealistic simulator before assuming alpha.
