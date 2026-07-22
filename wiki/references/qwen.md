---
type: reference
title: "Qwen (instruct models)"
category: model
url: https://huggingface.co/Qwen
used_in: [[[stage-0-environment-orientation]], [[stage-4-agent-loop-and-prompts]], [[stage-6-sft]], [[stage-8-rl-fine-tuning]]]
tags: [model, llm, instruct]
updated: 2026-07-22
---

# Qwen (instruct models)

The small open **instruct** LLM family used as the agent's policy ([[llm-as-policy]]),
loaded via [[hugging-face-transformers]]. "Small" is deliberate — it has to fit training
+ rollouts on an accessible GPU.

**How it's used here.**
- **Stage 0:** load it, generate from a trivial prompt (smoke test).
- **Stage 4:** it's the policy inside the [[agent-policy|agent loop]].
- **Stages 6/8:** fine-tuned with [[lora-peft|LoRA]] (SFT then RL).

**Sizes as a research variable.** 0.5B / 1.5B / 3B is a candidate scaling experiment in
[[stage-9-experiments]].

**Source:** [[2026-07-22-project-pipeline]].
