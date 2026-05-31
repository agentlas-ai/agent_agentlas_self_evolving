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
