---
type: decision
title: "Use an LLM as the policy (text in / text out), not a from-scratch RL net"
status: accepted
decided: 2026-07-22
alternatives: ["Train a network from scratch on raw game features (e.g. CNN/MLP + PPO)"]
resolves: []
tags: [architecture, foundational]
updated: 2026-07-22
---

# Decision — LLM as the policy

**Decision.** The agent *is* a pretrained language model ([[qwen]]): the game state is
rendered to **text** ([[state-encoding]]), the model emits **text**, and that text is
parsed into an action ([[env-action-parser]]). Improvement comes from
[[supervised-fine-tuning|SFT]] then [[reinforcement-learning-grpo|RL]] on that model.

**Status.** Accepted — it's the project's premise (this is what makes it interesting as
a portfolio piece vs. yet another game-playing net).

**Why.** Leverages the model's prior world/knowledge and reasoning; makes
[[chain-of-thought-reasoning|reasoning]] a first-class, studiable variable
([[does-cot-survive-rl]]).

**Consequence — what this decision *creates*.** The two text boundaries become the
load-bearing design surfaces: [[state-encoding]] (Stage 2) and action parsing (Stage 3).
Everything in [[overview]] follows from this choice.

**Alternative not taken.** A from-scratch RL network over raw features — more standard,
but sidesteps the reasoning question this project is built to explore.

**Source:** [[2026-07-22-project-pipeline]].
