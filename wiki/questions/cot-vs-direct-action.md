---
type: question
title: "Chain-of-thought reasoning vs. direct action?"
status: open
stage: 4
tags: [prompt, reasoning, research-variable]
updated: 2026-07-22
---

# Chain-of-thought reasoning vs. direct action?

**Crux.** Should the model [[chain-of-thought-reasoning|reason]] before answering, or
emit a direct action? **Resolution: make it a configurable flag** (not a one-way door)
— it's a prime research variable for [[stage-9-experiments]].

**Consequences to design around.**
- **Output format** must separate reasoning from the final action so the
  [[env-action-parser|parser]] finds it → links to [[how-to-handle-invalid-model-output]].
- **Latency / context** — reasoning traces cost tokens on every one of 1000+ decisions
  ([[encoding-detail-vs-context-budget]]).
- **SFT data** must match the chosen mode → [[reasoning-in-sft-data]].

**Downstream experiment:** [[does-cot-survive-rl]]. **Bites at**
[[stage-4-agent-loop-and-prompts]]. **Status:** open (leaning "configurable").
