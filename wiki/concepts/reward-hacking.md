---
type: concept
title: "Reward hacking"
status: developing
source_count: 1
updated: 2026-07-22
tags: [reward, rl, failure-mode]
---

# Reward hacking

When the agent maximizes the **letter** of the [[reward-design|reward]] while missing
its **intent** — e.g. a shaped reward for "damage dealt" or "survival" producing an
agent that farms damage or stalls without ever *winning* the run.

**Why it's central here.** It's the main argument *against* shaped rewards in
[[sparse-vs-shaped-reward]], and one of the failure modes to watch for while staring at
[[stage-8-rl-fine-tuning|RL]] curves and transcripts. The Stage 7 success bar explicitly
asks for a **written hypothesis of how the reward could be gamed** before RL starts, so
it's recognizable when it appears.

**Detection:** reward climbs while the true metric (win rate, floors) stalls or
diverges — which is exactly why the [[stage-5-baseline-evaluation|independent
evaluation harness]] must stay separate from the training reward.

**Related:** [[reward-design]] · [[reinforcement-learning-grpo]].
**Source:** [[2026-07-22-project-pipeline]].
