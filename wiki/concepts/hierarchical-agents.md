---
type: concept
title: "Hierarchical / composite agents"
status: stub
source_count: 1
updated: 2026-06-05
tags: [reinforcement-learning, architecture, future-work]
---

# Hierarchical / composite agents

A proposed (not yet built) architecture in
[[2021-08-15-creating-an-ai-for-slay-the-spire]]: instead of one agent playing all of
[[slay-the-spire]], use **multiple specialist agents** coordinated by an orchestrator.

## The idea
- Specialist sub-agents for **combat**, **card drafting**, **shop purchasing**, **events**.
- An **orchestrator** makes **map/path selections** and delegates each node to the
  relevant sub-agent.

## Open problems (per the author)
- **Training scheme unclear** — one idea is to freeze all agents but one, train it on
  the full game for a while, then rotate.
- **Pushing long-term strategy down** to sub-agents, which tend to be short-sighted
  (e.g., over-using consumables now). A proposed mechanism: the orchestrator passes a
  distilled signal, e.g. a number in [0,1] for "how much trouble before using a
  consumable," informed by what's coming (e.g., a Bronze Automaton boss ahead).
- The author is genuinely **uncertain** this beats training a single full-game agent.

## Related
[[reward-engineering]] (credit assignment to sub-agents) ·
[[model-free-reinforcement-learning]] · [[slay-the-spire]]
