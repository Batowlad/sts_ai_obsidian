---
type: question
title: "Should SFT examples carry reasoning or just the action?"
status: open
stage: 6
tags: [sft, data, reasoning]
updated: 2026-07-22
---

# Should SFT examples carry reasoning or just the action?

**Crux.** [[supervised-fine-tuning|SFT]] examples can be `state→action` or
`state→reasoning→action`. Which — and it must stay **consistent** with the Stage 4
[[cot-vs-direct-action]] mode, or training and inference formats diverge.

**Tension.** Reasoning traces teach *how* to think and may transfer better, but (a)
where do trusted reasoning traces come from — the base model's own? a stronger model? —
and (b) they inflate token counts ([[encoding-detail-vs-context-budget]]).

**Bites at** [[stage-6-sft]]. Feeds the [[does-cot-survive-rl]] experiment.
**Status:** open.
