---
type: question
title: "Does chain-of-thought help, and does it survive RL?"
status: open
stage: 9
tags: [experiment, reasoning, research-question]
updated: 2026-07-22
---

# Does chain-of-thought help, and does it survive RL?

**The leading Stage 9 research question** — the thing that makes this *research*, not a
demo. Best fit for the project's setup.

**Design.** Train with and without [[chain-of-thought-reasoning|reasoning]]; measure
play quality; then check whether [[reinforcement-learning-grpo|RL]] **preserves or
erodes** the reasoning (does the model keep reasoning usefully, or collapse to terse
actions that score the same reward?).

**Rigor requirements** ([[evaluation-statistics]]): multiple seeds per condition,
matched controls, error bars — one run is not evidence.

**Alternatives** if this doesn't pan out: scaling with model size (0.5B/1.5B/3B), or
isolating the SFT-vs-RL contribution.

**Depends on:** [[cot-vs-direct-action]] (configurable flag) + [[reasoning-in-sft-data]].
**Bites at** [[stage-9-experiments]]. **Status:** open (candidate primary result).
