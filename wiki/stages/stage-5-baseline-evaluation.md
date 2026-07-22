---
type: stage
stage: 5
title: "Stage 5 — Baseline evaluation"
status: planned
goal: "Measure how well the un-fine-tuned model plays, with metrics reused everywhere."
success_check: "A documented baseline with numbers and uncertainty, e.g. 'base + CoT: 4% win over 200 games, avg floor 6'."
builds: [[[eval-evaluate]], [[eval-metrics]]]
tags: [evaluation, metrics, rigor]
updated: 2026-07-22
---

# Stage 5 — Baseline evaluation

**Goal.** [[eval-evaluate|eval/evaluate.py]] + [[eval-metrics|eval/metrics.py]] run many
games over varied seeds and compute **win rate, average floors climbed, average score**,
logged to [[weights-and-biases]]. This harness underpins *every later claim* — build it
carefully. Test prompt variations here (does [[chain-of-thought-reasoning|CoT]] help the
base model? few-shot?) and record each.

**The learning gap.** Statistical thinking → [[evaluation-statistics]]. Win rate is a
proportion, so quantify uncertainty with a confidence interval; control for seed variance
so comparisons are fair → [[how-many-games-to-trust-a-win-rate]]. Don't shortcut this —
it's the empirical-rigor skill the whole project rests on.

**Success check.** A documented baseline *with uncertainty* — the number is meaningless
without its interval.

**Builds:** [[eval-evaluate]], [[eval-metrics]]. **Follows:** [[stage-4-agent-loop-and-prompts]].
**Leads to:** [[stage-6-sft]], and reused in [[stage-8-rl-fine-tuning]] & [[stage-9-experiments]].
