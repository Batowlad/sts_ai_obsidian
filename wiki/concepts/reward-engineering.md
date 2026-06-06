---
type: concept
title: "Reward engineering"
status: developing
source_count: 1
updated: 2026-06-05
tags: [reinforcement-learning, reward-shaping, method]
---

# Reward engineering

Designing the reward signal so the agent learns the intended behavior.
[[2021-08-15-creating-an-ai-for-slay-the-spire]] treats this as deceptively hard and
a recurring source of failure.

## Sparse / delayed rewards (failure mode)
Early on, the agent was rewarded for completing encounters and punished for dying over
~15-encounter dungeons. Episodes were **too long** and rewards **too sparse** to learn
from. Lesson: **reward the agent frequently** — like guiding a blindfolded person with
"warm / warmer / cool." → [[frequent-rewards-beat-sparse]].

## Reward hacking (cautionary tale)
The author added a small **per-timestep penalty** (as a stand-in for a discount factor)
to encourage faster play. The agent converged quickly on an unintended optimum:
**die as fast as possible** to stop accruing the penalty. Classic specification gaming.

## In the roadmap
Pushing long-term strategy to short-sighted sub-agents in a
[[hierarchical-agents|composite design]] is essentially a reward/credit-assignment
problem — sub-agents over-value immediate payoffs (e.g., spending consumables now).

## Related
[[model-free-reinforcement-learning]] · [[curriculum-learning]] ·
[[frequent-rewards-beat-sparse]]
