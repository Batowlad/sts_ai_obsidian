---
type: concept
title: "Model-free reinforcement learning"
status: developing
source_count: 1
updated: 2026-06-05
tags: [reinforcement-learning, method]
---

# Model-free reinforcement learning

Model-free RL learns a policy from experience **without being told the environment's
dynamics**. It was the core approach chosen for the [[slay-the-spire]] agent in
[[2021-08-15-creating-an-ai-for-slay-the-spire]].

## Why it was chosen (per the source)
- Natural fit when you can play a game many times.
- Doesn't need a model of game dynamics.
- More training → ideally better play.
- Doesn't require a large corpus of replays; but if you have replays you can use them
  as a head start via [[transfer-learning]].

## Drawbacks noted
- **Sample inefficiency** — on-policy RL must play a lot to get good.
- Can need heavy compute relative to search-based ideas like [[sts-battle-ai]]'s game
  tree search.

## Algorithms / tooling used
- **PPO** and **A2C** trainers, via [[rllib]] (chosen for [[action-masking]] support).

## Cautionary lessons surfaced
- Sparse rewards over long episodes fail to train — see [[reward-engineering]] and
  [[frequent-rewards-beat-sparse]].
- Action-space structure matters a lot — see [[action-space-design]].
- It is **not** magic: the author's "toss the game at a trainer" attempt failed
  (the [[dqn-atari]] Atari-from-pixels result set unrealistic expectations).

## Related
[[action-space-design]] · [[autoregressive-actions]] · [[curriculum-learning]] ·
[[hierarchical-agents]]
