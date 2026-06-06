---
type: study
title: "Playing Atari with Deep Reinforcement Learning (DQN)"
authors: [Mnih, et al. (DeepMind)]
year: 2013
venue: "DeepMind (NIPS Deep Learning Workshop 2013; Nature 2015)"
methodology: "Deep Q-Network learning Atari games from raw pixels"
sample: "Atari 2600 games (ALE)"
key_finding: "An agent can learn to play Atari games directly from raw pixels via model-free RL."
tags: [reinforcement-learning, external-reference, deepmind]
---

# Playing Atari with Deep RL (DQN)

External reference in [[2021-08-15-creating-an-ai-for-slay-the-spire]]. DeepMind's
result that an agent can learn Atari games **from raw pixels** with
[[model-free-reinforcement-learning|model-free RL]].

## Role in the source
- It **set the author's expectations too high** ("RL is magic, right?"): the
  assumption that you could toss any game at a trainer and get a good agent. For Slay
  the Spire that failed — the lesson being that **action-space and reward design still
  matter** ([[action-space-design]], [[reward-engineering]]).

## Related
[[sc2le-pysc2]] · [[model-free-reinforcement-learning]] · _link: [[deepmind]]_
