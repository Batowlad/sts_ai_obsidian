---
type: component
title: "env/state_encoder.py"
stage: 2
status: planned
responsibility: "Render a game state into the text prompt the model reasons over."
depends_on: [[[env-game-interface]]]
tags: [encoding, prompt, high-leverage]
updated: 2026-07-22
---

# env/state_encoder.py

**Responsibility.** Take a state from [[env-game-interface|get_state()]] and produce a
clear textual description (HP, energy, hand + card effects, enemies + intents, relics,
the decision asked). Pure Python, no ML. Implements the [[state-encoding]] concept.

**Status:** planned — built in [[stage-2-state-encoding]]. Expect **many** revisions;
v1 is a draft.

**The bar:** a knowledgeable human can play from the text alone.
**The tension it must manage:** [[encoding-detail-vs-context-budget]].

**Consumers.** [[agent-prompts]] / [[agent-policy]] embed its output;
[[data-collect-rollouts]] uses it to build SFT examples.

_Stub — record the encoding schema + iteration notes here as it evolves._
**Source:** [[2026-07-22-project-pipeline]].
