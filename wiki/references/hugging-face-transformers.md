---
type: reference
title: "Hugging Face Transformers"
category: library
url: https://huggingface.co/docs/transformers
used_in: [[[stage-0-environment-orientation]], [[stage-4-agent-loop-and-prompts]]]
tags: [library, inference, model-loading]
updated: 2026-07-22
---

# Hugging Face Transformers

The library for loading and generating from the [[qwen]] model.

**How it's used here.**
- **Stage 0:** load the model, generate from a trivial prompt.
- **Stage 4:** generation inside the [[agent-policy|agent loop]].
- Fine-tuning builds on top via [[trl]] + [[lora-peft|PEFT]].

At [[stage-8-rl-fine-tuning|RL]] time, generation may be swapped to [[vllm]] for
throughput. **Source:** [[2026-07-22-project-pipeline]].
