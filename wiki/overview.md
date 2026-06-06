---
type: overview
title: "Overview"
status: developing
updated: 2026-06-05
tags: [meta, slay-the-spire, reinforcement-learning]
---

# Overview

The front door to this wiki: the **living thesis** and a **map** of what's inside.
I revise this whenever a new source strengthens, weakens, or shifts the picture.

**Topic (emerging):** building an AI to play **[[slay-the-spire]]** — methods,
prior work, and what makes the game hard.

## Thesis (v0.1 — from 1 source)
Building a strong Slay the Spire AI is hard because its roguelite traits (randomness,
procedural maps, long/ sparse reward horizons, rare synergies) resist a single learned
policy. Early evidence (from one practitioner's [[model-free-reinforcement-learning|RL]]
retrospective) suggests the decisive factors are **engineering choices around the
learning problem**, not raw algorithm power:
- **[[action-space-design]]** — direct, identity-keyed, [[autoregressive-actions|autoregressive]]
  actions beat flat/indirect/overloaded ones.
- **[[reward-engineering]]** — dense feedback is needed, but naive shaping invites
  reward hacking.
- **[[curriculum-learning]]** — decompose into measurable milestones and toy
  environments you can verify by hand.

A parallel finding: a non-learned **search** agent ([[sts-battle-ai]]) outplays RL in
combat — but only by exploiting hidden RNG, so the comparison is unfair. Whether
**[[hierarchical-agents|composite agents]]** beat a single full-game agent is open.

> Caveat: this thesis rests on a **single source** ([[toypiper-jahabrewer]]'s
> retrospective). Treat as a hypothesis to test against more sources (academic RL,
> other STS agents, deckbuilding-game AI work).

## Research questions
_The questions driving this deep-dive. Tell me which to prioritize._
- What action-space and reward designs work best for deckbuilding-roguelite RL?
- Can a fair (non-RNG-cheating) agent match search-based combat play?
- Single full-game agent vs. hierarchical/per-encounter agents — which wins, and why?
- How feasible is [[transfer-learning]] from expert human play given no replay system?
- Could an **assist tool** (HP-loss prediction, map annotation) help humans without
  exploiting hidden internals? → [[hp-loss-model]]

## Map of the wiki
- **Concepts** — [[index#Concepts]] (RL method, action spaces, rewards, curriculum,
  hierarchy)
- **People & organizations** — [[index#People & organizations]]
- **Studies / prior work** — [[index#Studies]] (spirecomm, STS Battle AI,
  decapitate-the-spire; DQN-Atari, SC2LE)
- **Claims** — [[index#Claims]]
- **Sources** — [[index#Sources]]

## Open tensions & contradictions
- **Dense rewards vs. reward hacking:** "[[frequent-rewards-beat-sparse|reward
  frequently]]" pulls toward dense shaping, while the die-fast anecdote shows naive
  dense shaping backfires. Not a contradiction, but a live design tension.
- **"Hardcoded won't scale" vs. search plays great:** [[hardcoded-ai-wont-scale]] is
  an unproven opinion; meanwhile non-learned [[sts-battle-ai]] is strong — flag for
  more evidence on heuristic vs. search vs. learned.

---
_See [[index]] for the full catalog and [[log]] for the timeline._
