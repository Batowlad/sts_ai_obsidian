---
type: claim
title: "A* combat tree-search outplays trained RL agents but exploits the hidden RNG seed"
status: supported
confidence: medium
supported_by: [[[2021-08-15-creating-an-ai-for-slay-the-spire]]]
contradicted_by: []
updated: 2026-06-05
tags: [slay-the-spire, search, combat]
---

# Claim: tree-search outplays RL — but by seeing the future

[[sts-battle-ai]] runs **A\* search over the combat decision tree** and, per
[[2021-08-15-creating-an-ai-for-slay-the-spire]], plays **far better** than any agent
the author trained with [[model-free-reinforcement-learning|RL]]. **However**, its
"save scum" method exploits **hidden game internals (the RNG seed)** — it can
effectively **see the future**, so the comparison isn't apples-to-apples.

## Evidence
- **For:** author's direct experience comparing the two.
- **Caveat:** the advantage depends on RNG-seed access that a fair agent wouldn't have;
  strength under hidden information is unestablished.

## Implication
RL is comparatively expensive/sample-inefficient (see [[model-free-reinforcement-learning]]),
but a fair RL agent and a cheating search agent aren't directly comparable.

## Related
[[sts-battle-ai]] · [[model-free-reinforcement-learning]]
