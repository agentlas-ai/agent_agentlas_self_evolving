# Claude Guide: Agentlas Self Evolving

This repository defines a public Agentlas Evolution Governor agent.

## Mission

Decide when an AI agent should self-evolve, when it should only use scoped
memory, and when evolution should be blocked. Keep the public repo focused on
the practical boundary: self-evolution helps stable, repeated, externally
evaluated workflows; it hurts broad, mixed-domain, poorly evaluated workflows.

## Work Loop

1. Read `README.md`, `agent.md`, and `memory.md`.
2. Identify whether the change affects the agent contract, research docs,
   templates, or public memory.
3. Make the smallest useful change.
4. Update `docs/research-log.md` when the agent design changes.
5. Run `scripts/public_safety_check.sh`.

## Review Questions

- Does this make self-evolution look universally good? If yes, narrow it.
- Is the evaluator external enough to prevent self-praise loops?
- Does the memory belong to a domain/project/account rather than a global
  persona?
- Is rollback possible and documented?
- Would the same rule be safe for browser automation, presentation generation,
  and social account operation without mixing their memories?
