---
type: reference
title: "Weights & Biases (W&B)"
category: infra
url: https://wandb.ai
used_in: [[[stage-5-baseline-evaluation]], [[stage-8-rl-fine-tuning]]]
tags: [infra, logging, experiment-tracking]
updated: 2026-07-22
---

# Weights & Biases (W&B)

Experiment tracking / logging.

**How it's used here.**
- **Stage 5:** log baseline eval metrics (win rate, floors, score) across seeds and
  prompt variants — the record every later claim is checked against
  ([[evaluation-statistics]]).
- **Stage 8:** log [[reinforcement-learning-grpo|RL]] training curves; watching these
  curves is how [[reward-hacking]] and non-convergence get caught.
- **Stage 9:** the plots that back the [[stage-9-experiments|experiment]] come from here.

**Source:** [[2026-07-22-project-pipeline]].
