---
type: stage
stage: 4
title: "Stage 4 — The agent loop and prompt design"
status: planned
goal: "Wire encoder → model → parser → game into a loop that plays full games (no training)."
success_check: "The base model plays full games end to end (quality will be poor — that's fine)."
builds: [[[agent-policy]], [[agent-prompts]]]
tags: [agent, prompt, loop]
updated: 2026-07-22
---

# Stage 4 — The agent loop and prompt design

**Goal.** Assemble the play loop in [[agent-policy|agent/policy.py]] +
[[agent-prompts|agent/prompts.py]]: [[state-encoding|encode]] → generate with
[[hugging-face-transformers]] → [[env-action-parser|parse]] → [[env-game-interface|step]].
No training yet.

**What you do.** Design the system prompt (who the model is, the game, the response
format). Decide the [[chain-of-thought-reasoning|chain-of-thought]] question now — reason
before answering, or force a direct action? **Make it configurable**; it's one of the
best research variables for [[stage-9-experiments]] → [[cot-vs-direct-action]].

**The learning gap.** Prompt design is empirical and underspecified — small wording
changes shift play quality. If you allow reasoning, you must design an output format
that separates reasoning from the final action so the [[env-action-parser|parser]] can
find it. That format design is a real puzzle.

**Success check.** The base model plays full games end to end. Poor quality is expected;
the loop working is the milestone.

**Builds:** [[agent-policy]], [[agent-prompts]]. **Follows:** [[stage-3-action-parsing]].
**Leads to:** [[stage-5-baseline-evaluation]].
