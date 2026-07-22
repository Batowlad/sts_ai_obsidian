---
type: concept
title: "LoRA / PEFT"
status: developing
source_count: 1
updated: 2026-07-22
tags: [lora, peft, training, efficiency]
---

# LoRA / PEFT

**Parameter-efficient fine-tuning**: instead of updating all model weights, train small
low-rank adapter matrices (**LoRA**) and leave the base frozen. Cheap enough to fit on a
single accessible GPU, which is why the project uses it for both
[[supervised-fine-tuning|SFT]] and [[reinforcement-learning-grpo|RL]]. Implemented with
the **PEFT** library (Hugging Face), alongside `bitsandbytes` quantization to shrink
memory further.

**Knobs to tune** (from PEFT/TRL docs): rank `r`, `lora_alpha`, target modules
(which projections get adapters), dropout, learning rate.

**Decision:** LoRA over full fine-tuning → [[lora-over-full-finetuning]].

**Used in:** [[stage-6-sft]], [[stage-8-rl-fine-tuning]]. **Related tool:** [[trl]].
**Source:** [[2026-07-22-project-pipeline]].
