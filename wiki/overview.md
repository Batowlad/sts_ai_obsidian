---
type: overview
title: "Project overview & vision"
current_stage: 0
updated: 2026-07-22
tags: [meta, vision]
---

# Overview — LLM plays Slay the Spire

**The project.** Train a small open LLM (a [[qwen]] instruct model) to play
[[slay-the-spire]] well, by wrapping the [[sts-lightspeed]] simulator, encoding game
states as text, letting the model choose actions, and then improving it with
**supervised fine-tuning** ([[supervised-fine-tuning]]) followed by **reinforcement
learning** ([[reinforcement-learning-grpo]]). The deliverable is a rigorous
experiment + writeup, not a demo.

**Why this shape.** The core bet is to use a language model *as the policy*
([[llm-as-policy]]) instead of training a network from scratch on raw game features.
That makes the two text boundaries — *game → text* ([[state-encoding]]) and *text →
action* ([[env-action-parser|action parsing]]) — the load-bearing design surfaces.

## Current state

- **Stage:** 0 — [[stage-0-environment-orientation|environment & orientation]] (not started).
- **Nothing built yet.** Component and code pages are `planned` until their stage begins.

## The pipeline (map)

| # | Stage | Produces | Status |
|---|-------|----------|--------|
| 0 | [[stage-0-environment-orientation]] | random-agent smoke test | planned |
| 1 | [[stage-1-game-interface]] | [[env-game-interface\|env/game_interface.py]] | planned |
| 2 | [[stage-2-state-encoding]] ★ | [[env-state-encoder\|env/state_encoder.py]] | planned |
| 3 | [[stage-3-action-parsing]] | `env/action_parser.py` | planned |
| 4 | [[stage-4-agent-loop-and-prompts]] | `agent/policy.py`, `agent/prompts.py` | planned |
| 5 | [[stage-5-baseline-evaluation]] | `eval/evaluate.py`, `eval/metrics.py` | planned |
| 6 | [[stage-6-sft]] | `data/collect_rollouts.py`, `training/sft.py` | planned |
| 7 | [[stage-7-reward-design]] ★ | `training/reward.py` | planned |
| 8 | [[stage-8-rl-fine-tuning]] ★ | `training/rl.py` | planned |
| 9 | [[stage-9-experiments]] | plots + analysis | planned |
| 10 | [[stage-10-writeup]] | repo + blog post | planned |

★ = where the real intellectual content lives (see thesis below).

## Thesis — where the real learning concentrates

Three stages are worth struggling through rather than routing around; the rest are
good engineering but more mechanical:

1. **[[state-encoding|State encoding]] (Stage 2)** — the model can only reason about
   what the text tells it. Detail vs. context budget is a live tension
   ([[encoding-detail-vs-context-budget]]); a full run is 1000+ decisions.
2. **[[reward-design|Reward design]] (Stage 7)** — sparse vs. shaped
   ([[sparse-vs-shaped-reward]]), with [[reward-hacking]] as the trap.
3. **[[reinforcement-learning-grpo|RL wiring]] (Stage 8)** — reconciling "GRPO rewards
   a generation" with "my reward comes from a whole multi-step game"
   ([[grpo-reward-over-a-whole-game]]) is the central puzzle.

**Guardrail (from the roadmap):** resist copying a complete example for Stages 2, 7,
8 — working those out is most of what the project teaches.

**Explicit fallback:** if RL won't converge after honest effort, the SFT result plus
an analysis of *why* RL failed is a legitimate, shippable project. Decide the
give-up threshold in advance — see [[when-to-abandon-rl]].

## Foundational decisions already implied

- [[llm-as-policy]] — use an LLM as the policy (accepted-by-premise).
- [[use-grpo-over-ppo]] — GRPO for RL (proposed).
- [[lora-over-full-finetuning]] — LoRA/PEFT, not full fine-tuning (proposed).

## Biggest open questions

[[encoding-detail-vs-context-budget]] · [[how-to-handle-invalid-model-output]] ·
[[cot-vs-direct-action]] · [[sparse-vs-shaped-reward]] ·
[[grpo-reward-over-a-whole-game]] · [[how-many-games-to-trust-a-win-rate]] ·
[[when-to-abandon-rl]]

---

_Source: [[2026-07-22-project-pipeline]]. This page is the living vision — I revise it
as the project moves stages._
