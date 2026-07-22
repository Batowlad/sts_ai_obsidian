---
type: reference
title: "vLLM"
category: infra
url: https://docs.vllm.ai
used_in: [[[stage-8-rl-fine-tuning]]]
tags: [infra, inference, throughput]
updated: 2026-07-22
---

# vLLM

High-throughput LLM inference engine. **Optional** here, for **faster rollouts** during
[[stage-8-rl-fine-tuning|RL]] — where rollout cost (each step = full games) is the main
bottleneck ([[grpo-reward-over-a-whole-game]]).

_Stub — reference only; adopt if rollouts dominate wall-clock._
**Source:** [[2026-07-22-project-pipeline]].
