# Evaluation

The Evolution Governor is evaluated by whether it promotes useful evolution and
blocks noisy or unsafe evolution.

## Primary Metrics

| Metric | Question |
|---|---|
| Verdict accuracy | Did the governor choose the same verdict an expert reviewer would choose? |
| Promotion precision | Of promoted changes, how many improved holdout performance? |
| Regression rate | Did evolved behavior harm previously working tasks? |
| Memory contamination rate | Did unrelated domain memory influence the workflow? |
| Rollback success | Can the prior behavior be restored quickly and fully? |
| User correction rate | Did user corrections decrease after evolution? |
| Evidence density | Does each decision record cite concrete feedback rather than vibes? |

## Minimal Experiment

1. Select one recurring workflow, such as a browser operator for one website.
2. Collect baseline task outcomes across 20 runs.
3. Split failures into an improvement set and a holdout set.
4. Let the governor propose one bounded evolution target.
5. Promote only if the improvement target passes the promotion gate.
6. Re-run the holdout set and compare against baseline.
7. Record regressions, latency, permission changes, and user corrections.

## Negative-Control Experiment

Run the same process on a broad mixed-domain assistant that performed unrelated
tasks. The expected verdict is `DO_NOT_EVOLVE` or `CONSTRAIN`, not `EVOLVE`.

This test matters because the governor should resist the tempting but harmful
move of turning scattered user interactions into one self-evolving identity.

## Promotion Gate

Promotion requires:

- stronger or equal holdout performance;
- no new privacy or permission exposure;
- clear rollback;
- a dated decision record;
- a named owner;
- an invalidation condition.

## Failure Review

If an evolved change causes a regression, write a failure review:

- What changed?
- Which signal authorized the change?
- Which holdout task failed?
- Was the evaluator too weak, too narrow, or gameable?
- Was the memory boundary wrong?
- Should the rule be reverted, narrowed, expired, or escalated?

## Trading-Specific Evaluation

Trading agents need stricter evaluation because backtests are easy to overfit.
Use these gates before any trading evolution is promoted:

| Gate | Purpose |
|---|---|
| Net-of-cost test | Include fees, spread, slippage, borrow/funding, and market impact. |
| Walk-forward split | Prevent the agent from selecting parameters on the same period it reports. |
| Holdout markets | Test related but unseen symbols, sectors, or regimes. |
| Random-walk null | Compare against shuffled returns or synthetic random-walk series. |
| Deflated Sharpe / multiple-testing penalty | Account for the number of strategies or agents searched. |
| Drawdown and ruin test | Penalize strategies that maximize return by hiding tail risk. |
| Abstention score | Reward the agent for not trading when no edge is present. |
| Paper-trading quarantine | Require forward results before live-capital promotion. |

The expected negative-control result is important: in a true random-walk
environment, a large population should not discover a durable edge. If it does,
assume leakage, overfitting, or a flawed simulator until proven otherwise.

## Threads/SNS-Specific Evaluation

Threads-style social agents should evaluate both content quality and operational
safety.

| Gate | Purpose |
|---|---|
| Voice holdout | Check new drafts against older approved examples that were not used for learning. |
| Brand drift score | Detect when the agent becomes too promotional, too generic, or off-voice. |
| Runtime replay | Test browser recipes against harmless navigation or draft-only flows before live use. |
| Failure recovery | Verify that popups, login expiry, empty states, and network errors produce safe stops. |
| Rate/cadence guard | Prevent the hourly operator from becoming spammy or repetitive. |
| Human approval sample | Keep a review sample of posts, replies, and skill updates before promotion. |
| Policy boundary review | Block credential capture, anti-abuse bypass, deceptive engagement, and cross-account leakage. |

The healthy result is not maximum posting volume. The healthy result is stable
voice, low correction rate, safe browser operation, and a willingness to skip an
hour when the queue has no good post.
