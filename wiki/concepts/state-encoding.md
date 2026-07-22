---
type: concept
title: "State encoding (game → text)"
status: developing
source_count: 1
updated: 2026-07-22
tags: [encoding, prompt, high-leverage]
---

# State encoding (game → text) ★

Turning a structured game state into a **text description** the model reasons over. One
of the two highest-leverage design surfaces in the project (the other is action
parsing). Built in [[stage-2-state-encoding]] as [[env-state-encoder]].

**The governing principle.** *The model can only reason about what the text tells it* —
so encoding quality largely **caps** achievable play quality. The stated success bar:
**a knowledgeable human should be able to play from the text alone.**

**The central tension.** Detail vs. context budget → [[encoding-detail-vs-context-budget]].
More detail aids reasoning but costs context length, and with 1000+ decisions per run
([[slay-the-spire]]) that pressure never lets up.

**Open sub-questions.**
- Include full card descriptions every turn, or assume them known?
- Represent the deck fully, or summarized?
- How to make enemy **intents** legible?

**Method.** Treat v1 as a draft. Iterate empirically: design an encoding → watch where
the model gets confused → trace the confusion back to the encoding → revise.

**Feeds:** [[stage-4-agent-loop-and-prompts]] (prompt), [[reasoning-in-sft-data]].
**Source:** [[2026-07-22-project-pipeline]].
