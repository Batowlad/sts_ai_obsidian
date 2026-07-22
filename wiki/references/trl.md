---
type: reference
title: "TRL (Transformer Reinforcement Learning)"
category: library
url: https://huggingface.co/docs/trl
used_in: [[[stage-6-sft]], [[stage-8-rl-fine-tuning]]]
tags: [library, training, sft, rl]
updated: 2026-07-22
---

# TRL (Transformer Reinforcement Learning)

Hugging Face's fine-tuning library. Supplies both training entry points this project
uses:
- **`SFTTrainer`** → [[stage-6-sft]] ([[supervised-fine-tuning]]). The quickstart shows
  the skeleton; mapping game data into its dataset format is the builder's work.
- **`GRPOTrainer`** → [[stage-8-rl-fine-tuning]] ([[reinforcement-learning-grpo]]),
  chosen over PPO ([[use-grpo-over-ppo]]).

Composes with [[lora-peft|PEFT]] (LoRA adapters) and `datasets`/`bitsandbytes`.

**Open wiring question** for GRPO: [[grpo-reward-over-a-whole-game]].
**Source:** [[2026-07-22-project-pipeline]].
