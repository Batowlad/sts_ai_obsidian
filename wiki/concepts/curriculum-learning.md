---
type: concept
title: "Curriculum learning & problem decomposition"
status: developing
source_count: 1
updated: 2026-06-05
tags: [reinforcement-learning, methodology, evaluation]
---

# Curriculum learning & problem decomposition

Making a hard learning problem tractable (and **measurable**) by breaking it into
achievable milestones and simplified environments. A central lesson of
[[2021-08-15-creating-an-ai-for-slay-the-spire]].

## Core lessons
- **Break the problem into achievable milestones.** Without a known-good foundation,
  you can't tell whether the agent is progressing or how long it must train.
- **Simplify until *you* know the optimal policy**, then check whether the agent finds
  it too.

## The toy-environment ladder the author built
1. Empty observation, two actions: action 1 rewards + ends; action 2 punishes + ends.
   → baseline for how much training the optimal policy needs.
2. Add a boolean observation that flips which action rewards → shows the agent can act
   **on observation**.
3. Add a random-noise feature → shows the agent can **ignore useless information**.
4. ...and so on, adding one capability at a time.

## Applied to the game
Reduced full-game training to a **single combat instance**, and ultimately to a
**combat-only** agent (current focus) because progress is easier to measure. Relates
to the proposed **per-encounter** agents and the [[evaluation-gauntlet]].

## Related
[[reward-engineering]] · [[model-free-reinforcement-learning]] · [[evaluation-gauntlet]]
