---
type: concept
title: "Evaluation statistics (win rate, uncertainty, seeds)"
status: developing
source_count: 1
updated: 2026-07-22
tags: [evaluation, statistics, rigor]
---

# Evaluation statistics

The empirical-rigor backbone of the project: because **win rate is a proportion**, a
bare number ("6% win rate") is meaningless without an **uncertainty interval** and a
sample size. Lives across [[stage-5-baseline-evaluation]] (build the harness) and
[[stage-9-experiments]] (compare conditions).

**Core ideas to apply.**
- **Confidence interval on a proportion** — how many games until a win-rate estimate is
  trustworthy? → [[how-many-games-to-trust-a-win-rate]].
- **Seed variance control** — Slay the Spire is RNG-heavy ([[slay-the-spire]]); compare
  conditions on matched seed sets so you're measuring the model, not luck.
- **Multiple seeds per condition** — [[reinforcement-learning-grpo|RL]] is noisy; **one
  run is not evidence**. Report error bars.

**Why it's load-bearing.** Every later claim (SFT beats baseline, RL beats SFT, CoT
helps) is only as credible as this harness — and it's the transferable skill the
writeup ([[stage-10-writeup]]) is judged on.

**Source:** [[2026-07-22-project-pipeline]].
