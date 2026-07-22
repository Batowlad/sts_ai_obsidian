---
type: concept
title: "Supervised fine-tuning (SFT)"
status: developing
source_count: 1
updated: 2026-07-22
tags: [sft, training]
---

# Supervised fine-tuning (SFT)

Training the model on **demonstration examples** — `state→action` or
`state→reasoning→action` pairs from strong games — so it imitates good play. Built in
[[stage-6-sft]] as [[training-sft]], using [[trl]] `SFTTrainer` + [[lora-peft|LoRA]].
It's the cheaper, more stable improvement step that precedes (and seeds)
[[reinforcement-learning-grpo|RL]].

**The judgment calls.**
- **Data quality** — what counts as a "good" example, and how to filter it. Garbage in,
  garbage out. Sources: the base model's better runs and/or a heuristic/MCTS agent.
- **Example format** — reasoning included or action-only? This must stay consistent with
  the Stage 4 [[cot-vs-direct-action]] choice → [[reasoning-in-sft-data]].
- **How much data** is enough.

**Role in the pipeline.** Its checkpoint is the **starting point** for
[[stage-8-rl-fine-tuning|Stage 8]] — and, if RL fails, SFT alone is the shippable
result ([[when-to-abandon-rl]]).

**Success bar:** beats the [[stage-5-baseline-evaluation|baseline]] on the same metrics.

**Source:** [[2026-07-22-project-pipeline]].
