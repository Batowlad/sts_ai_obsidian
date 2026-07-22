---
type: decision
title: "Use GRPO rather than PPO for RL fine-tuning"
status: proposed
decided: 2026-07-22
alternatives: ["PPO (actor-critic with a separate value network)"]
resolves: []
tags: [rl, grpo, training]
updated: 2026-07-22
---

# Decision — GRPO over PPO

**Decision (roadmap recommendation).** Use [[trl]]'s `GRPOTrainer` for
[[stage-8-rl-fine-tuning|Stage 8]] rather than PPO.

**Status.** **Proposed** — recommended by the roadmap but not yet exercised; confirm
once RL is actually wired ([[grpo-reward-over-a-whole-game]]).

**Why.** GRPO uses **group-relative** advantages and needs **no separate critic/value
network** — lighter on a single accessible GPU, and one fewer moving part to stabilize.

**Alternative not taken (yet).** PPO — well-trodden, but the extra critic costs memory
and adds tuning surface.

**Related:** [[reinforcement-learning-grpo]] · [[lora-over-full-finetuning]].
**Source:** [[2026-07-22-project-pipeline]].
