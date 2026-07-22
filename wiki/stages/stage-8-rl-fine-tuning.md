---
type: stage
stage: 8
title: "Stage 8 — RL fine-tuning"
status: planned
goal: "Improve play through reinforcement learning on game outcomes."
success_check: "Performance improves over the SFT baseline, shown as a curve over training steps."
builds: [[[training-rl]]]
tags: [rl, grpo, training, high-leverage]
updated: 2026-07-22
---

# Stage 8 — RL fine-tuning ★

**Goal.** [[training-rl|training/rl.py]]: the model plays games, gets
[[reward-design|reward]], and updates — via [[trl]]'s `GRPOTrainer`
([[reinforcement-learning-grpo]], [[use-grpo-over-ppo|chosen over PPO]]), with
[[lora-peft|PEFT]], optional [[vllm]] for faster rollouts, and [[weights-and-biases]].
**The hard stage — budget the most time and patience.**

**Setup rules.** Connect [[training-reward|reward.py]] as the trainer's reward signal.
Keep **KL regularization** so the model doesn't drift into degeneracy. **Start from the
[[stage-6-sft|SFT]] checkpoint, not the base model.**

**The learning gaps (struggle productively).**
- **The central wiring puzzle:** GRPO wants a reward over a *generated output*, but your
  output is a *whole multi-step game* → [[grpo-reward-over-a-whole-game]]. Working this
  out is most of the stage's intellectual content.
- **Rollout cost is brutal** (each step = full games) → efficiency matters ([[vllm]]).
- **Failure modes** — silent non-learning, [[reward-hacking]], mode collapse,
  instability — diagnosed by staring at curves and transcripts.

**Critical fallback.** If RL won't converge after honest effort, SFT + an analysis of
*why* is a shippable project. Decide the give-up threshold **in advance** →
[[when-to-abandon-rl]].

**Success check.** Improvement over the SFT baseline, shown as a curve over steps.

**Builds:** [[training-rl]]. **Follows:** [[stage-7-reward-design]].
**Leads to:** [[stage-9-experiments]].
