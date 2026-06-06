---
type: study
title: "spirecomm"
authors: [ForgottenArbiter]
year: 
venue: "open-source project / mod (GitHub: ForgottenArbiter/spirecomm)"
methodology: "hardcoded strategies and priorities; communication mod interface to the live game"
sample: 
key_finding: "Plays the game via hardcoded heuristics; serves as a demo for its mod and as an interface to the real game."
tags: [slay-the-spire, prior-work, heuristic-ai]
---

# spirecomm

Prior work cited in [[2021-08-15-creating-an-ai-for-slay-the-spire]]. A Slay the Spire
AI / mod by **ForgottenArbiter** that uses **hardcoded strategies and priorities**;
the author treats it mainly as a demo for the mod it ships with.

## Role in the author's project
- Used as the **interface to the live game** in *Attempt 0* (rllib hooked to the real
  game via spirecomm, playing at human speed) — which was too slow and motivated the
  headless [[decapitate-the-spire]] clone.

## Assessment (per the source)
- The author's opinion: a hardcoded approach **won't scale to high-level play** →
  [[hardcoded-ai-wont-scale]].

## Related
[[slay-the-spire]] · [[sts-battle-ai]] · [[decapitate-the-spire]]
