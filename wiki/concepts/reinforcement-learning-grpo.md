---
type: concept
title: "Reinforcement learning with GRPO"
status: developing
source_count: 1
updated: 2026-07-22
tags: [rl, grpo, training, high-leverage]
---

# Reinforcement learning with GRPO ★

Improving the policy by having it play, scoring outcomes with a
[[reward-design|reward]], and updating toward higher reward. This project uses **GRPO**
(Group Relative Policy Optimization) via [[trl]]'s `GRPOTrainer`, chosen over PPO in
[[use-grpo-over-ppo]] (no separate critic → lighter on the GPU). Built in
[[stage-8-rl-fine-tuning]] as [[training-rl]].

**Key mechanics for this project.**
- **Start from the [[stage-6-sft|SFT]] checkpoint**, not the base model.
- Keep **KL regularization** to a reference model so the policy doesn't drift into
  degeneracy (mode collapse, gibberish).
- GRPO scores a *group* of sampled generations relative to each other — no value
  network needed.

**The central wiring puzzle.** GRPO expects a reward over a **generated output**, but
here the "output" is a **whole multi-step game** → [[grpo-reward-over-a-whole-game]].
Reconciling these is most of the stage's intellectual content.

**Known failure modes to diagnose:** silent non-learning, [[reward-hacking]], mode
collapse, instability — read curves + transcripts. Rollout cost is the practical
bottleneck ([[vllm]] optional to speed it up).

**Fallback:** if it won't converge, ship SFT + a post-mortem → [[when-to-abandon-rl]].

**Source:** [[2026-07-22-project-pipeline]].
