---
type: concept
title: "Chain-of-thought reasoning"
status: developing
source_count: 1
updated: 2026-07-22
tags: [prompt, reasoning, research-variable]
---

# Chain-of-thought reasoning

Letting the model **reason in text before committing to an action**, versus forcing a
direct action. In this project it's deliberately made a **configurable flag** (decided
at [[stage-4-agent-loop-and-prompts]]) because it's one of the best research variables
for [[stage-9-experiments]].

**Two design consequences.**
1. **Output format.** If reasoning is allowed, the output must cleanly separate the
   reasoning from the final action so the [[env-action-parser|parser]] can extract it →
   ties into [[how-to-handle-invalid-model-output]].
2. **Training consistency.** Whether SFT examples carry reasoning must match this choice
   → [[reasoning-in-sft-data]].

**The research question it powers.** Does CoT help, and does it **survive** RL
fine-tuning? → [[does-cot-survive-rl]] (the leading Stage 9 experiment). Open design
question: [[cot-vs-direct-action]].

**Source:** [[2026-07-22-project-pipeline]].
