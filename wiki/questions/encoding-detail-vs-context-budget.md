---
type: question
title: "How much state detail to encode vs. context budget?"
status: open
stage: 2
tags: [encoding, context, high-leverage]
updated: 2026-07-22
---

# How much state detail to encode vs. context budget?

**Crux.** More detail in the [[state-encoding|encoding]] helps the model reason, but
costs context length — and a full [[slay-the-spire|run]] is **1000+ decisions**, so the
pressure is constant. Where's the line?

**Sub-decisions.**
- Card descriptions **every turn**, or assume known after first mention?
- Deck represented **fully**, or summarized (counts by card)?
- How to make **enemy intents** legible without bloat?

**How it'll be resolved.** Empirically — iterate the encoding, watch the model fail,
trace failures back to the text, revise. Bites at [[stage-2-state-encoding]]; interacts
with [[reasoning-in-sft-data]] (reasoning traces also eat context).

**Status:** open. One of the project's highest-leverage questions ([[overview]]).
