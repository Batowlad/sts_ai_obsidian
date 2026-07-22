---
type: question
title: "How to reward a whole multi-step game under GRPO?"
status: open
stage: 8
tags: [rl, grpo, wiring, high-leverage]
updated: 2026-07-22
---

# How to reward a whole multi-step game under GRPO?

**Crux — the central wiring puzzle of Stage 8.** [[reinforcement-learning-grpo|GRPO]]
expects a reward function over a **generated output**, but the project's "output" is a
**whole game of 1000+ decisions**, not a single response. How do you present the game to
the trainer?

**Angles to work through (unresolved).**
- Is a "generation" one *decision* (state→action), with game outcome credited back to
  each? Or the *whole trajectory* as one long sequence?
- How is credit assigned across a long game from a sparse-ish outcome
  ([[sparse-vs-shaped-reward]])?
- How does group-relative scoring (GRPO samples a *group* per prompt) map onto game
  states?
- Rollout cost is brutal (each step = full games) → efficiency + [[vllm]].

**Why it matters.** The roadmap says working this out *is* most of the intellectual
content of the stage — resist copying a complete example ([[overview]] guardrail).

**Bites at** [[stage-8-rl-fine-tuning]]. **Status:** open — the key unknown to resolve
before RL can run. Good candidate to file back as a **synthesis** once explored.
