# Literature Map

This map records the public research anchors behind the Agentlas Self Evolving
agent contract. It is not a full survey. It highlights the claims that shape the
repo's practical boundary.

## Self-Reflection And Episodic Memory

[Reflexion: Language Agents with Verbal Reinforcement Learning](https://arxiv.org/abs/2303.11366)
shows that language agents can improve across trials by turning task feedback
into verbal reflection stored in episodic memory. The important design lesson is
that reflection is useful when it is connected to feedback. Reflection without a
credible signal can become self-justification.

## Skill Libraries In Stable Environments

[Voyager: An Open-Ended Embodied Agent with Large Language Models](https://arxiv.org/abs/2305.16291)
uses an automatic curriculum, executable skill library, environment feedback,
and self-verification in Minecraft. This supports the repository's claim that
self-evolution works best when the environment is stable enough for skills to be
reused and tested.

## Failure-To-Skill Loops

[EvoSkill: Automated Skill Discovery for Multi-Agent Systems](https://arxiv.org/abs/2603.02766)
turns execution failures into reusable structured skill folders and uses held-
out validation to decide what survives. This is close to the practical pattern
recommended here: do not promote every reflection; promote only bounded changes
that improve validation performance.

## Memory Is Not Universal

[EvoMemBench: Benchmarking Agent Memory from a Self-Evolving Perspective](https://arxiv.org/abs/2605.18421)
finds that current memory systems are not a general solution. Memory helps most
when context is insufficient or tasks are difficult, and no single memory form
works consistently across all settings. This is the main empirical caution
behind the repo's "do not globally evolve broad assistants" rule.

[Memory for Autonomous LLM Agents](https://arxiv.org/abs/2603.07670) frames
agent memory as a write-manage-read loop and identifies write-path filtering,
contradiction handling, latency budgets, and privacy governance as engineering
realities. This supports treating memory as managed infrastructure rather than
as a transcript dump.

## Multi-Agent Memory Boundaries

[Self-Evolving Multi-Agent Systems via Decentralized Memory](https://arxiv.org/abs/2605.22721)
argues that centralized memory can create coordination overhead, privacy
concerns, and loss of agent diversity. The repo uses the same practical caution:
memory should be scoped by role, project, account, or domain when possible.

## Evaluator-Driven Evolution

[AlphaEvolve](https://arxiv.org/abs/2506.13131) demonstrates the strength of an
evolutionary coding loop when a system can repeatedly modify candidate programs
and score them with evaluators. The useful transfer is not "everything should
self-evolve." It is "evolution is powerful when evaluation is explicit."

## Reflection Plus Memory Optimization

[SAGE: Self-evolving Agents with Reflective and Memory-augmented Abilities](https://www.sciencedirect.com/science/article/pii/S0925231225011427)
combines iterative feedback, reflection, and memory optimization. It reinforces
the idea that self-evolving agents need memory filtering and checker-like roles,
not just more accumulated context.

## Self-Correction Limitations

[Large Language Models Cannot Self-Correct Reasoning Yet](https://arxiv.org/abs/2310.01798)
reports that intrinsic self-correction without external feedback can degrade
reasoning. This is why the Evolution Governor treats external feedback as a hard
requirement for promotion.

## Continual Learning Failure Modes

[Continual learning: A systematic literature review](https://www.sciencedirect.com/science/article/pii/S0893608025011074)
frames catastrophic forgetting as a central challenge when systems learn from
changing data streams.

[Loss of Plasticity in Deep Continual Learning](https://www.nature.com/articles/s41586-024-07711-7)
shows that standard deep learning systems can lose the ability to learn over
many tasks. The analogy for agent design is simple: more evolution is not
automatically more adaptability; learning loops need mechanisms that preserve
diversity, rollback, and stability.

## Safety And Optimization Pressure

[Concrete Problems in AI Safety](https://arxiv.org/abs/1606.06565) identifies
reward hacking, scalable supervision, safe exploration, and distribution shift
as practical accident-risk categories. Self-evolution introduces optimization
pressure, so these risks should be reviewed before promotion.

## Trading, Random Walks, And Evolution

[The Adaptive Markets Hypothesis](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=602222)
applies competition, adaptation, and natural selection to financial
interactions. It is the strongest research anchor for thinking about trading
agents as ecological competitors rather than isolated predictors.

[Data-Snooping, Technical Trading Rule Performance, and the Bootstrap](https://ideas.repec.org/a/bla/jfinan/v54y1999i5p1647-1691.html)
uses White's Reality Check to evaluate technical trading rules while accounting
for the universe of rules searched. This supports the repo's warning that a
large population of trading agents can manufacture false discoveries unless the
search process itself is included in evaluation.

[The Deflated Sharpe Ratio](https://www.davidhbailey.com/dhbpapers/deflated-sharpe.pdf)
argues that selection bias under multiple testing and non-normal returns inflate
strategy performance. Trading-agent evolution should therefore record how many
variants were tried, not only the best Sharpe that survived.

[Using Genetic Algorithms to Find Technical Trading Rules](https://www.sciencedirect.com/science/article/pii/S0304405X9800052X)
found that GA-learned S&P 500 technical rules did not earn consistent excess
returns over buy-and-hold after transaction costs in out-of-sample periods. This
is a caution against treating genetic search as an alpha machine.

[Deep Reinforcement Learning in Quantitative Algorithmic Trading: A Review](https://arxiv.org/abs/2106.00123)
notes that many DRL trading studies remain proof-of-concept, often unrealistic,
and lack real-time trading validation. This supports `CONSTRAIN` rather than
unrestricted `EVOLVE` for trading agents.

[Realistic Market Impact Modeling for Reinforcement Learning Trading Environments](https://arxiv.org/abs/2603.29086)
shows that transaction-cost and market-impact assumptions can materially change
algorithm ranking and trading behavior. This makes cost modeling part of the
evolution boundary, not an implementation detail.

[No Free Lunch Theorems for Optimization](https://www.cs.ubc.ca/~hutter/earg/papers07/00585893.pdf)
formalizes limits of general-purpose black-box optimization. In this repo's
terms: natural selection over many agents helps only if the market environment
has exploitable structure and the selection test measures that structure rather
than historical luck.
