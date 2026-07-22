---
type: reference
title: "sts_lightspeed"
category: simulator
url: https://github.com/gamerpuppy/sts_lightspeed
used_in: [[[stage-0-environment-orientation]], [[stage-1-game-interface]]]
tags: [simulator, cpp, bindings]
updated: 2026-07-22
---

# sts_lightspeed

A fast C++ reimplementation/simulator of [[slay-the-spire]], with **Python bindings** —
the environment the agent plays. The whole project sits on top of it.

**How it's used here.**
- **Stage 0:** build it, get bindings working, drive random games, learn its data model
  (state representation, legal-action enumeration, stepping, game-over).
- **Stage 1:** wrapped behind [[env-game-interface]] so nothing else imports it directly.

**Caveat (from the roadmap).** No tutorial for its API — expect to read source and
examples. The three primitives to nail: how state is represented, how legal actions are
enumerated, how you step. Open question about the boundary: [[what-to-expose-in-the-interface]].

_URL is a best-guess for the known project; verify before relying on it._
**Source:** [[2026-07-22-project-pipeline]].
