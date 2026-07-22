---
type: question
title: "How to handle invalid model output?"
status: open
stage: 3
tags: [parsing, training, reward]
updated: 2026-07-22
---

# How to handle invalid model output?

**Crux.** The [[env-action-parser|parser]] will receive malformed text, references to
things that don't exist, and illegal-but-well-formed actions. What's the policy?

**Options (each with training consequences).**
1. **Re-prompt** — free retry; costs latency/rollout time, hides the error from
   learning.
2. **Constrain generation** to only-legal outputs → [[constrained-decoding]]; guarantees
   validity, couples to the interface.
3. **Default / penalty** — pick a fallback action or penalize; the penalty becomes part
   of the [[reward-design|reward signal]], affecting [[stage-8-rl-fine-tuning|RL]].

**Key judgment.** Which failures are "free retries" vs. which should *cost* the agent?
And how forgiving should parsing be — too strict discards good decisions on formatting,
too loose misreads intent.

**Bites at** [[stage-3-action-parsing]]; couples to [[cot-vs-direct-action]] (output
format) and [[reward-design]]. **Status:** open.
