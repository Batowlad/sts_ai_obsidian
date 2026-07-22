---
type: decision
title: "Use LoRA/PEFT rather than full fine-tuning"
status: proposed
decided: 2026-07-22
alternatives: ["Full-parameter fine-tuning"]
resolves: []
tags: [lora, peft, training, efficiency]
updated: 2026-07-22
---

# Decision — LoRA/PEFT over full fine-tuning

**Decision (roadmap default).** Fine-tune with **LoRA adapters** via PEFT (+
`bitsandbytes` quantization) for both [[supervised-fine-tuning|SFT]] and
[[reinforcement-learning-grpo|RL]], keeping the base model frozen. See [[lora-peft]].

**Status.** **Proposed** — the standard efficient default; adopt once SFT runs.

**Why.** Fits training on a single accessible GPU; small adapters are cheap to store,
swap, and compare across [[stage-9-experiments|experiments]] (e.g. one adapter per
condition).

**Alternative not taken.** Full fine-tuning — more expressive but far heavier on memory
and compute; unjustified at this model scale.

**Source:** [[2026-07-22-project-pipeline]].
