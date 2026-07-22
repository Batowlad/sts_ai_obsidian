---
type: stage
stage: 2
title: "Stage 2 — State encoding (game → text)"
status: planned
goal: "Turn a game state into a clear text prompt the model can reason about."
success_check: "A knowledgeable human could play correctly from the text encoding alone."
builds: [[[env-state-encoder]]]
tags: [encoding, prompt, high-leverage]
updated: 2026-07-22
---

# Stage 2 — State encoding (game → text) ★

**Goal.** [[env-state-encoder|env/state_encoder.py]] takes a game state and produces a
clear textual description: HP, energy, hand (and what each card does), enemies and
their intents, relics, and the decision being asked for. Pure Python; no ML yet.

**Why it matters.** One of the two highest-leverage parts of the project — the model
can only reason about what the text tells it, so encoding quality largely **caps** play
quality. See [[state-encoding]] and the thesis in [[overview]].

**The learning gap (deep).** No right answer, real tradeoffs — driven by
[[encoding-detail-vs-context-budget]]: more detail helps reasoning but costs context,
and a full run is 1000+ decisions so context pressure is constant. Sub-questions: card
descriptions every turn or assumed known? deck represented fully or summarized? how to
make enemy intents legible? Treat v1 as a draft; iterate by tracing model confusion
back to the encoding.

**Success check.** Print an encoding and have a knowledgeable human play correctly from
*it alone*. If a person can't, the model certainly can't.

**Builds:** [[env-state-encoder]]. **Follows:** [[stage-1-game-interface]].
**Leads to:** [[stage-4-agent-loop-and-prompts]].
