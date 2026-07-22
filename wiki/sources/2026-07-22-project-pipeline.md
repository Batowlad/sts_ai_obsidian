---
type: source
title: "Project pipeline — LLM plays Slay the Spire (SFT + RL)"
source_type: roadmap
created: 2026-07-22
ingested: 2026-07-22
raw: raw/project-pipeline.md
tags: [roadmap, rl, sft, llm, slay-the-spire]
status: ingested
---

# Source — Project pipeline (10-stage roadmap)

Raw: [[project-pipeline|raw/project-pipeline.md]] · the
project's founding document. It lays out a staged plan to train a small LLM to play
Slay the Spire, and — importantly — annotates each stage with its *learning gap* (the
judgment call that is the builder's to make) and a concrete *success check*.

## Summary

Build up from a working [[sts-lightspeed|simulator]] + [[qwen|model]], wrap the sim
behind a clean [[env-game-interface|interface]], make the two text boundaries
(state→text [[state-encoding]], text→action parsing), assemble a play loop, measure a
baseline, then improve with [[supervised-fine-tuning|SFT]] and
[[reinforcement-learning-grpo|RL/GRPO]], and finish with a controlled experiment and
writeup. Each stage gates the next via a success check.

## Key points

- **Two text boundaries are load-bearing:** [[state-encoding]] (Stage 2) and action
  parsing (Stage 3) sit between the game and the model; encoding quality largely caps
  play quality.
- **Design gaps are the curriculum.** The roadmap deliberately leaves judgment calls
  open — interface shape, invalid-output policy, CoT vs. direct action, reward shape,
  RL wiring — and flags [[state-encoding|encoding]], [[reward-design|reward]], and
  [[reinforcement-learning-grpo|RL]] as the three where the real learning is.
- **Rigor is the point at Stage 5+.** Win rate is a proportion → needs confidence
  intervals ([[evaluation-statistics]]); RL is noisy → multiple seeds per condition.
- **Explicit fallback:** SFT + an honest RL post-mortem is a shippable outcome
  ([[when-to-abandon-rl]]).

## Notable specifics (with locations in the raw file)

- "A full run is 1000+ decisions, so context pressure is constant" — Stage 2. Motivates
  [[encoding-detail-vs-context-budget]].
- "GRPOTrainer recommended over PPO — no separate critic, lighter on your GPU" —
  Stage 8 → [[use-grpo-over-ppo]].
- "Start from your SFT checkpoint, not the base model" — Stage 8.
- "GRPO expects a reward function over generated outputs — but your output is a whole
  game" — Stage 8 → [[grpo-reward-over-a-whole-game]].
- "If a person can't play from your text, the model certainly can't" — Stage 2 success bar.

## Connections

- Stages: [[stage-0-environment-orientation]] · [[stage-1-game-interface]] ·
  [[stage-2-state-encoding]] · [[stage-3-action-parsing]] ·
  [[stage-4-agent-loop-and-prompts]] · [[stage-5-baseline-evaluation]] ·
  [[stage-6-sft]] · [[stage-7-reward-design]] · [[stage-8-rl-fine-tuning]] ·
  [[stage-9-experiments]] · [[stage-10-writeup]]
- Concepts: [[state-encoding]] · [[reward-design]] ·
  [[reinforcement-learning-grpo]] · [[supervised-fine-tuning]] · [[lora-peft]] ·
  [[chain-of-thought-reasoning]] · [[reward-hacking]] · [[evaluation-statistics]]
- Decisions: [[llm-as-policy]] · [[use-grpo-over-ppo]] · [[lora-over-full-finetuning]]
- References: [[sts-lightspeed]] · [[hugging-face-transformers]] · [[qwen]] · [[trl]] ·
  [[weights-and-biases]]
- Vision: [[overview]]
