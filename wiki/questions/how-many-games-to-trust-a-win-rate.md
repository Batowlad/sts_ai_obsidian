---
type: question
title: "How many games until a win-rate number is trustworthy?"
status: open
stage: 5
tags: [evaluation, statistics, rigor]
updated: 2026-07-22
---

# How many games until a win-rate number is trustworthy?

**Crux.** Win rate is a **proportion**, so its estimate has a confidence interval that
shrinks with sample size. At low win rates (the baseline may be ~a few %), you need
*more* games to distinguish, say, 4% from 7%. How many is enough? See
[[evaluation-statistics]].

**To work out.**
- A target CI width (e.g. ±2%) → implied N via a proportion CI (Wilson interval).
- **Seed control:** compare conditions on matched seed sets to cancel
  [[slay-the-spire|RNG]] variance.
- Budget: games aren't free (each is a full playthrough) — trade N against compute.

**Bites at** [[stage-5-baseline-evaluation]] and every comparison in
[[stage-9-experiments]]. **Status:** open.
