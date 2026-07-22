---
type: question
title: "How long to fight RL before falling back to SFT?"
status: open
stage: 8
tags: [rl, project-management, research-skill]
updated: 2026-07-22
---

# How long to fight RL before falling back to SFT?

**Crux.** [[reinforcement-learning-grpo|RL]] may not converge. The roadmap is explicit:
**SFT + an honest analysis of why RL failed is a legitimate, shippable project.** So set
the **give-up threshold in advance** — knowing when to stop is a research skill, and
deciding it *before* you're emotionally invested keeps it honest.

**To decide (a pre-commitment).**
- A concrete budget: wall-clock / GPU-hours / number of honest configurations tried.
- The signals that count as "honest effort exhausted" vs. "one more knob."
- What the fallback deliverable looks like (which [[stage-9-experiments|experiment]]
  becomes SFT-only, what the post-mortem must contain).

**Bites at** [[stage-8-rl-fine-tuning]]; shapes [[stage-10-writeup]]. **Status:** open —
**should be answered before Stage 8 starts, not during.**
