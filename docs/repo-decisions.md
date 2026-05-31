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
