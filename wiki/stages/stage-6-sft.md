---
type: stage
stage: 6
title: "Stage 6 — Supervised fine-tuning (SFT)"
status: planned
goal: "Improve play by training on good gameplay examples."
success_check: "The SFT model beats the Stage 5 baseline on the same metrics, measured the same way."
builds: [[[data-collect-rollouts]], [[training-sft]]]
tags: [sft, training, data]
updated: 2026-07-22
---

# Stage 6 — Supervised fine-tuning (SFT)

**Goal.** Collect demonstration data and [[supervised-fine-tuning|SFT]] the model with
[[lora-peft|LoRA]]. Built from [[data-collect-rollouts|data/collect_rollouts.py]] +
[[training-sft|training/sft.py]], using [[trl]] (`SFTTrainer`), [[lora-peft|PEFT]],
`datasets`, and `bitsandbytes`.

**What you do.** Gather strong/winning games — from the base model's better runs and/or
a heuristic/MCTS agent if the sim offers one — format as `state→action` or
`state→reasoning→action` examples, and train with LoRA.

**The learning gaps (several).**
- **Data quality** — you define what counts as "good"; garbage in, garbage out. How to
  filter? How much is enough?
- **Format** — does each example carry reasoning or just the action? This interacts with
  the Stage 4 [[cot-vs-direct-action]] choice → [[reasoning-in-sft-data]].
- **LoRA config** — rank, target modules, learning rate; tune from PEFT/TRL docs.
- Mapping game data into the `SFTTrainer` dataset format is the part you work out.

**Success check.** Beats the [[stage-5-baseline-evaluation|baseline]] on the same
metrics. The SFT checkpoint becomes the *starting point* for [[stage-8-rl-fine-tuning]].

**Builds:** [[data-collect-rollouts]], [[training-sft]]. **Follows:** [[stage-5-baseline-evaluation]].
**Leads to:** [[stage-7-reward-design]].
