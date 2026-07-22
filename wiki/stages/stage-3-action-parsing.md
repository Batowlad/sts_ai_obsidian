---
type: stage
stage: 3
title: "Stage 3 — Action parsing (text → game)"
status: planned
goal: "Turn the model's text output into a legal game action, handling imperfect text."
success_check: "Given varied (and deliberately broken) model outputs, the parser extracts the right action or fails gracefully by design."
builds: [[[env-action-parser]]]
tags: [parsing, robustness]
updated: 2026-07-22
---

# Stage 3 — Action parsing (text → game)

**Goal.** [[env-action-parser|env/action_parser.py]] parses model output into an action
the [[env-game-interface|interface]] accepts, and handles the messy reality of
imperfect text: malformed output, references to things that don't exist, and
illegal-but-well-formed actions (e.g. playing a card you can't afford).

**The learning gap.** *How to handle invalid output* → [[how-to-handle-invalid-model-output]].
Options: re-prompt for a retry, constrain generation to only-legal outputs
([[constrained-decoding]]), or assign a default/penalty. Each has consequences for both
play quality and training — penalties become part of the [[reward-design|reward signal]]
later. Decide which failures are "free retries" vs. which should cost the agent. Plus a
parsing-robustness craft: too strict throws out good decisions on formatting; too loose
misreads intent.

**Success check.** Feed varied outputs (including deliberately broken ones) and confirm
the parser either extracts the right action or fails gracefully in the way you designed.

**Builds:** [[env-action-parser]]. **Follows:** [[stage-2-state-encoding]].
**Leads to:** [[stage-4-agent-loop-and-prompts]].
