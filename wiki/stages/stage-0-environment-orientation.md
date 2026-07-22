---
type: stage
stage: 0
title: "Stage 0 — Environment and orientation"
status: planned
goal: "Get the simulator and model both running, separately, before connecting anything."
success_check: "A random agent plays complete games and you can print the outcome (won/lost, floor reached)."
builds: []
tags: [setup, simulator, environment]
updated: 2026-07-22
---

# Stage 0 — Environment and orientation

**Goal.** Get [[sts-lightspeed]] and a [[qwen]] model each running on their own,
before wiring anything together.

**What you do.**
- Build the simulator and get its **Python bindings** working.
- Write a throwaway script that plays a full game with **random legal actions**.
- Separately, load the model via [[hugging-face-transformers]] and generate from a
  trivial prompt. Needs a GPU.
- Read the simulator's API surface: what a state object contains, what an action
  looks like, how to enumerate legal actions, how to detect game-over.

**The learning gap.** There's no tutorial for the sim's API — read its source and
examples. Work out the three primitives that everything downstream depends on: how
game state is *represented*, how legal actions are *enumerated* at a decision point,
and how you *step* the game forward. This understanding is the foundation for
[[stage-1-game-interface]].

**Success check.** A random agent drives complete games start to finish from Python,
and you can print the outcome (won/lost, floor reached).

**Leads to:** [[stage-1-game-interface]].
**See also:** [[overview]] · [[slay-the-spire]] · source [[2026-07-22-project-pipeline]].
