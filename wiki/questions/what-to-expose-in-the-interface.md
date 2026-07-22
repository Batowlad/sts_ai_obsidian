---
type: question
title: "What should the game interface expose vs. hide?"
status: open
stage: 1
tags: [interface, architecture]
updated: 2026-07-22
---

# What should the game interface expose vs. hide?

**Crux.** [[env-game-interface|env/game_interface.py]] is the abstraction boundary
around [[sts-lightspeed]]. What belongs in the public surface (`reset`, `get_state`,
`get_legal_actions`, `step`, `is_terminal`, `get_result`) and what stays hidden?

**Considerations.**
- Follow [[gymnasium]]'s `reset`/`step`/`spaces` shape for familiarity — but not bound
  to it (no SB3).
- `get_state()` returns *what*? Raw sim object, or a project-owned state struct the
  [[env-state-encoder|encoder]] consumes? The latter decouples encoding from sim
  internals.
- Too thin a boundary leaks simulator details into `agent/` and `training/`; too thick
  hides things later stages need.

**Bites at** [[stage-1-game-interface]]. **Status:** open — resolved by building it.
