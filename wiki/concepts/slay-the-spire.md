---
type: concept
title: "Slay the Spire (as an AI domain)"
status: developing
source_count: 1
updated: 2026-07-22
tags: [domain, game, roguelike]
---

# Slay the Spire (as an AI domain)

Slay the Spire is a single-player deck-building roguelike: climb a spire floor by
floor, fighting enemies with a deck of cards, managing HP/energy/relics, and making
path and reward choices between fights. It's the environment this project's agent plays
via [[sts-lightspeed]].

**Why it's a hard, interesting domain for an LLM agent:**
- **Long horizon.** A full run is **1000+ decisions** — which is exactly what makes
  [[state-encoding|context pressure]] constant and [[stage-8-rl-fine-tuning|RL rollout
  cost]] brutal.
- **Sparse win signal.** You only *win* at the very end, motivating the
  [[sparse-vs-shaped-reward]] debate ([[reward-design]]).
- **Combinatorial actions.** Card plays, targets, and non-combat choices form a large,
  state-dependent legal-action set the [[env-action-parser|parser]] must map onto.
- **Hidden information & RNG.** Card draws, enemy intents, and map events add variance,
  which is why [[evaluation-statistics|seed control]] matters when measuring.

**Prior art to position against** (Stage 10): [[spirecomm]], [[sts-battle-ai]],
[[decapitate-the-spire]] — currently redlinks; survey near [[stage-10-writeup]].

**Used in:** [[stage-0-environment-orientation]] · [[overview]]. **Source:**
[[2026-07-22-project-pipeline]].
