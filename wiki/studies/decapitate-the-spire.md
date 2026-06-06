---
type: study
title: "decapitate-the-spire"
authors: [jahabrewer]
year: 
venue: "open-source tool (GitHub: jahabrewer/decapitate-the-spire)"
methodology: "headless Python reimplementation of Slay the Spire for fast, graphics-free RL training"
sample: 
key_finding: "Provides a fast headless environment so RL training isn't bottlenecked by the real game's human-speed graphical play."
tags: [slay-the-spire, tooling, environment]
---

# decapitate-the-spire

A **headless Python clone** of [[slay-the-spire]] built by [[toypiper-jahabrewer]] and
described in [[2021-08-15-creating-an-ai-for-slay-the-spire]]. Created in response to
*Attempt 0*, where training against the real game via [[spirecomm]] at human speed was
far too slow.

## Purpose
- A **fast, graphics-free** environment so the agent can play the game many times —
  essential for sample-inefficient [[model-free-reinforcement-learning]].

## Related
[[slay-the-spire]] · [[spirecomm]] · [[model-free-reinforcement-learning]]
