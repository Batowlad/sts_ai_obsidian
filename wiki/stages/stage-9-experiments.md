---
type: stage
stage: 9
title: "Stage 9 — Experiments"
status: planned
goal: "Answer one specific research question rigorously — the thing that makes this research."
success_check: "Plots that answer the question with quantified uncertainty, plus an explanation of why."
builds: []
tags: [experiments, research, rigor]
updated: 2026-07-22
---

# Stage 9 — Experiments

**Goal.** Pick **one** question and answer it rigorously, reusing everything above as
controlled comparisons, [[eval-evaluate|eval/]] for measurement, and notebooks for plots.
This is the stage that makes the project *research*, not a demo.

**The leading question (best fit for this setup).** Does
[[chain-of-thought-reasoning|chain-of-thought]] help, and does it **survive** RL
fine-tuning? Train with and without reasoning; measure; check whether
[[stage-8-rl-fine-tuning|RL]] preserves or erodes the reasoning →
[[does-cot-survive-rl]]. Alternatives: scaling with model size (0.5B/1.5B/3B), or
SFT-vs-RL contribution.

**The learning gap.** Experimental design: multiple seeds per condition (RL is noisy —
one run is not evidence), proper controls, honest reporting with error bars. See
[[evaluation-statistics]]. This is the **single most important stage for portfolio
signal** — rigor is the point, not an afterthought.

**Success check.** Plots answering the question with quantified uncertainty, and an
explanation of *why* you see what you see.

**Follows:** [[stage-8-rl-fine-tuning]]. **Leads to:** [[stage-10-writeup]].
