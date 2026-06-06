---
type: study
title: "STS Battle AI"
authors: []
year: 
venue: "open-source project / mod"
methodology: "A* search over the in-combat decision tree, using a purpose-built mod"
sample: 
key_finding: "Combat-only; plays better than any RL agent the author trained, but exploits hidden game internals (RNG seed) to effectively see the future."
tags: [slay-the-spire, prior-work, search, combat]
---

# STS Battle AI

Prior work cited in [[2021-08-15-creating-an-ai-for-slay-the-spire]]. A **combat-only**
Slay the Spire AI that runs **A\* search over the combat decision tree** as the game
is played, via a purpose-built mod.

## Strengths & caveat
- Plays **far better** than any agent the author trained with
  [[model-free-reinforcement-learning|RL]].
- **But** its "save scum" approach exploits **hidden game internals (the RNG seed)** —
  it can effectively **see the future**. → [[tree-search-outplays-rl-but-cheats]].

## Significance
- A reference point for how costly RL is vs. tree search (see drawbacks in
  [[model-free-reinforcement-learning]]).
- Motivates the author's interest in **assist tools** that *don't* need to exploit
  hidden internals to be useful.

## Related
[[slay-the-spire]] · [[spirecomm]] · [[model-free-reinforcement-learning]]
