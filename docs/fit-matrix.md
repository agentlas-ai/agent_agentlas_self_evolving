# Self-Evolution Fit Matrix

Use this matrix to decide whether self-evolution is likely to help.

## Fit Dimensions

| Dimension | High fit | Low fit |
|---|---|---|
| Recurrence | Same workflow repeats weekly or daily | One-off or rare task |
| Feedback | External tests, logs, screenshots, user corrections | Agent self-review only |
| Scope | One skill, memory, prompt, policy, or evaluator | Whole identity or broad tool access |
| Ownership | Project, account, site, repo, or domain memory | Global mixed personal memory |
| Reversibility | Decision record and rollback snapshot | Silent overwrite |
| Risk | Low-to-medium and monitorable | High-stakes, regulated, cross-tenant |
| Transfer | Similar future tasks expected | Future tasks unrelated |

## Example Verdicts

| Workflow | Verdict | Why |
|---|---|---|
| Browser agent repeatedly operating one SaaS dashboard | `EVOLVE` | Stable UI, observable failures, reusable selectors, bounded account scope |
| Presentation agent learning one user's deck style | `EVOLVE` | Strong recurring preference signal and inspectable outputs |
| SNS operator for one brand account | `CONSTRAIN` | Useful repeated loop, but must preserve account, policy, and platform boundaries |
| Generic assistant across all user tasks | `DO_NOT_EVOLVE` | Mixed domains create memory conflict and false continuity |
| Medical triage agent changing its own advice policy | `HUMAN_REVIEW` | High-stakes and regulated; evolution may help only under strict oversight |
| One-off market thesis brainstorm | `DO_NOT_EVOLVE` | No stable loop and high risk of canonizing speculation |
| Codebase maintenance agent with tests | `EVOLVE` | Repo conventions and test failures create reusable feedback |
| Legal drafting agent across many clients | `HUMAN_REVIEW` | Cross-client confidentiality and legal risk require owner review |
| Trading research agent in paper mode | `CONSTRAIN` | Recurring loop and measurable outcomes, but severe overfit and data-snooping risk |
| Live-capital trading agent changing its own risk limits | `HUMAN_REVIEW` | Financial harm, leverage, permissions, and compliance require explicit owner approval |

## Hard Blockers

Return `DO_NOT_EVOLVE` or `HUMAN_REVIEW` if any blocker is present:

- No external feedback signal.
- No rollback mechanism.
- Scope includes multiple unrelated domains.
- Memory may cross tenant, client, account, or project boundaries.
- The proposed change expands permissions.
- The workflow is high-stakes and lacks human review.
- The evaluator is the same agent trying to prove that it improved.
- For trading: the evaluation omits transaction costs, slippage, market impact,
  drawdown, turnover, and number-of-trials accounting.

## Narrowing Moves

If the instinct is "this might help, but it feels messy," try `CONSTRAIN`:

- Change global memory into project memory.
- Change personality evolution into style-guide evolution.
- Change automatic promotion into review-only proposal.
- Change one benchmark into held-out plus regression checks.
- Change broad tool access into per-workflow permission.
- Change raw trace storage into summarized, redacted lessons.
