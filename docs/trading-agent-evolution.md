# Trading Agent Evolution

This note extends the Evolution Governor to stock-trading agents. It is agent
architecture research, not investment advice.

## Question

If a trading agent self-evolves, is the objective function simply profit?

The short answer is no. Profit is the final ecological signal, but raw return is
a dangerous training target. Raw return rewards leverage, hidden tail risk,
overtrading, luck, and backtest overfitting. A self-evolving trading agent needs
a survival objective, not a scoreboard objective.

## Profit Is Not Enough

A naive objective looks like this:

```text
maximize total_return
```

That objective is incomplete because it does not know whether the return came
from durable edge, leverage, one lucky regime, survivorship bias, low liquidity,
ignored transaction costs, or a single crash-prone bet.

A safer fitness function is multi-objective:

```text
trading_fitness =
  net_risk_adjusted_return
- max_drawdown_penalty
- tail_loss_penalty
- turnover_penalty
- transaction_cost_penalty
- market_impact_penalty
- leverage_penalty
- concentration_penalty
- backtest_overfit_penalty
+ regime_robustness
+ abstention_quality
+ evidence_quality
```

This still does not guarantee alpha. It only prevents the evolution loop from
mistaking a fragile winner for a robust survivor.

## What Evolves?

Trading evolution can happen at several layers.

| Layer | Evolvable variables | Governance rule |
|---|---|---|
| Signal hypothesis | features, horizon, market regime, entry logic | Must survive holdout and null tests. |
| Risk policy | position sizing, stop conditions, gross/net exposure | Live risk caps require human review. |
| Execution policy | order type, participation rate, limit aggression | Must include slippage and market impact. |
| Research policy | data filters, universe construction, trial budget | Must record number of trials searched. |
| Memory policy | known failed edges, regime notes, broker constraints | Must be scoped by market, account, and horizon. |
| Philosophy phenotype | patience, abstention, falsification, humility | Can evolve as a prompt/skill, not as unchecked trading authority. |

The interesting part is the final row. In noisy markets, evolving one more
indicator parameter is often less valuable than evolving a better research
temperament: the agent's willingness to reject a pretty backtest, wait for a
real edge, and reduce risk when evidence weakens.

## Random-Walk Stress Test

If returns are close to a random walk, then a large population of agents will
still produce winners. That does not mean those winners learned a market edge.
It may only mean the selection process found the luckiest histories.

The more agents you generate, the more severe the multiple-testing problem
becomes. Natural selection over a noisy historical backtest can become a
false-positive amplifier.

For that reason, every trading-evolution loop should include a null environment:

- shuffled returns;
- synthetic random walks with matching volatility;
- block bootstrap samples;
- unseen time periods;
- unseen related markets;
- transaction-cost stress;
- regime stress.

In a true null environment, the expected result is no durable edge. If the
system finds many durable winners in random data, the evaluation harness is
probably leaking information or rewarding overfit.

## Survivorship Bias Is Not Natural Selection

Trading research often mistakes survivorship bias for evolution. They are not
the same thing.

Survivorship bias says: "I only looked at the winners that remained." Natural
selection says: "I defined a population, environment, mutation process, survival
test, and reproduction rule before seeing the winners."

The distinction matters. If an agent creates 10,000 variants, backtests all of
them, hides the 9,999 failures, and reports the champion, that is not
intelligent evolution. It is data snooping. A legitimate evolutionary trading
system must publish the graveyard:

- how many variants existed;
- what mutation space was allowed;
- which variants died and why;
- whether survivors beat random-walk and shuffled-return controls;
- whether survivor behavior worked forward, not only historically;
- whether the promoted lesson is general behavior rather than a memorized trade
  sequence.

## Natural Selection With Many Similar Agents

The user's proposed design is powerful: run many agents with the same mission
and method contract, then let selection decide which behaviors survive.

This can work, but only if selection happens on forward evidence rather than the
same history that generated the variants.

```text
agent population
  -> shared constitution
  -> independent hypotheses
  -> paper-trading or walk-forward trial
  -> survival score
  -> promote behavior, not raw trade sequence
```

The survival unit should be a behavior class, such as "cuts exposure when
signal decay appears" or "abstains when cost-adjusted edge is below threshold."
It should not be a memorized list of trades.

## Philosophical Evolution

Trading agents may benefit from abstract evolution more than parameter
evolution. The evolved object can be a disciplined worldview:

- Prefer no trade over low-conviction trade.
- Treat backtests as suspects until proven forward.
- Penalize complexity unless it improves holdout performance.
- Preserve capital as the first survival condition.
- Separate "being right" from "being paid after costs."
- Search for regime-specific edges, not universal laws.
- Promote falsification rules faster than entry rules.
- Retire a strategy when its reason for existing disappears.

This is philosophical only in language. Operationally, each principle becomes a
policy, evaluator, or memory rule.

## Verdict Pattern

| Scenario | Verdict |
|---|---|
| Paper-trading research population with strict null tests | `CONSTRAIN` moving toward `EVOLVE` |
| Live-capital agent changing strategy parameters within fixed risk caps | `HUMAN_REVIEW` |
| Live-capital agent changing leverage, capital, broker permissions, or kill switches | `DO_NOT_EVOLVE` unless explicitly authorized by a separate owner |
| Agent optimizing raw backtest return over many variants | `DO_NOT_EVOLVE` |
| Agent evolving abstention, falsification, and research discipline | `CONSTRAIN` or `EVOLVE` if externally evaluated |

## Minimum Constitution

A trading-agent population should share a constitution before evolution starts:

```text
1. Capital preservation outranks return maximization.
2. No live-capital promotion from in-sample backtests.
3. Every fitness report must include costs, slippage, drawdown, turnover, and
   number of trials searched.
4. Abstention is a valid action.
5. Risk limits, leverage, broker permissions, and capital allocation are locked
   outside the agent population.
6. Strategies must survive null, walk-forward, and paper-trading quarantine.
7. Selection promotes general behavior, not a memorized trade list.
```

## Practical Research Program

1. Create 100 to 10,000 agents with the same constitution.
2. Give each agent only a bounded hypothesis language.
3. Evaluate on a training period, but do not promote from it.
4. Filter with random-walk and shuffled-return null tests.
5. Run walk-forward validation.
6. Run paper trading with realistic costs.
7. Promote only behavior rules that improve survival across regimes.
8. Retire rules quickly when the edge decays.

The point is not to prove that markets are predictable. The point is to make the
evolution loop honest enough to discover when no edge exists.
