---
type: component
title: "env/game_interface.py"
stage: 1
status: planned
responsibility: "The single abstraction boundary around the simulator; the only module that imports sts_lightspeed."
depends_on: [[[sts-lightspeed]]]
tags: [interface, architecture]
updated: 2026-07-22
---

# env/game_interface.py

**Responsibility.** Wrap [[sts-lightspeed]] behind a clean class so `agent/` and
`training/` never touch simulator internals. Planned surface: `reset()`, `get_state()`,
`get_legal_actions()`, `step(action)`, `is_terminal()`, `get_result()`.

**Status:** planned — built in [[stage-1-game-interface]].

**Consumers.** [[env-state-encoder]] (reads `get_state()`), [[env-action-parser]]
(targets `get_legal_actions()` / `step()`), [[agent-policy]] (drives the loop).

**Key design question:** [[what-to-expose-in-the-interface]] — including what
`get_state()` returns (raw sim object vs. a project-owned struct). Inspiration:
[[gymnasium]].

_Stub — flesh out with the actual API once written._ **Source:** [[2026-07-22-project-pipeline]].
