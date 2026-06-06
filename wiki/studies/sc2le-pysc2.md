---
type: study
title: "StarCraft II: A New Challenge for Reinforcement Learning (SC2LE / PySC2)"
authors: [Vinyals, et al. (DeepMind)]
year: 2017
venue: "DeepMind (arXiv)"
methodology: "RL environment + baseline agents for StarCraft II; introduces structured/autoregressive action spaces"
sample: "StarCraft II"
key_finding: "Source of the autoregressive action-space idea adopted for the Slay the Spire agent."
tags: [reinforcement-learning, external-reference, deepmind, action-space]
---

# SC2LE / PySC2

External reference in [[2021-08-15-creating-an-ai-for-slay-the-spire]]. DeepMind's
StarCraft II learning environment paper, from which the author learned about
**[[autoregressive-actions]]**.

## Role in the source
- Provided the key technique that fixed the author's broken
  [[action-space-design|action space]]: choosing complex actions in dependent stages,
  each conditioned on the partial action chosen so far.

## Related
[[autoregressive-actions]] · [[action-space-design]] · [[dqn-atari]] · _link: [[deepmind]]_
