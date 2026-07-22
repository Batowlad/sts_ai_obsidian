---
type: stage
stage: 1
title: "Stage 1 — The game interface layer"
status: planned
goal: "A clean Python wrapper around the simulator that the rest of the code talks to."
success_check: "You can play a random game using only the interface class, never importing the simulator elsewhere."
builds: [[[env-game-interface]]]
tags: [interface, architecture]
updated: 2026-07-22
---

# Stage 1 — The game interface layer

**Goal.** A clean wrapper — [[env-game-interface|env/game_interface.py]] — that is the
**abstraction boundary** around [[sts-lightspeed]]. Nothing in `training/` or `agent/`
touches the simulator directly; they only talk to this class.

**What you do.** Design a class exposing roughly `reset()`, `get_state()`,
`get_legal_actions()`, `step(action)`, `is_terminal()`, `get_result()`. Look at
[[gymnasium]]'s `reset`/`step`/`spaces` for inspiration — but you're not bound to it
(no SB3 here).

**The learning gap.** The design question is yours: *what to expose vs. hide.* Getting
this boundary right is what makes the later stages tractable → open question
[[what-to-expose-in-the-interface]].

**Success check.** Play a random game using only this interface class, with no import
of the simulator anywhere else.

**Builds:** [[env-game-interface]]. **Follows:** [[stage-0-environment-orientation]].
**Leads to:** [[stage-2-state-encoding]], [[stage-3-action-parsing]].
