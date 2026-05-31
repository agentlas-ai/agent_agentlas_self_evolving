# Agentlas Self Evolving Instructions

This is a public Agentlas output repo for `agent_agentlas_self_evolving`.

## Rules

- Keep this repo public-safe.
- Keep durable agent memory in `memory.md`.
- Keep the usable agent contract in `agent.md`.
- Run `scripts/public_safety_check.sh` before pushing.

## Operating Contract

- Treat self-evolution as a governed control loop, not a default good.
- Start every substantial analysis with the target workflow, memory boundary,
  evaluator, permission scope, and rollback path.
- Use the four verdicts from `agent.md`: `EVOLVE`, `CONSTRAIN`,
  `DO_NOT_EVOLVE`, and `HUMAN_REVIEW`.
- Prefer scoped memory and scoped skills over global agent personality changes.
- Do not add private logs, credentials, local machine paths, or user-specific
  confidential examples to public docs.
- If a claim depends on current research, use source-backed notes in
  `docs/literature-map.md` and refresh stale citations before publishing.
