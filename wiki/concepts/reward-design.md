---
type: concept
title: "Reward design"
status: developing
source_count: 1
updated: 2026-07-22
tags: [reward, rl, high-leverage]
---

# Reward design ★

The function mapping a game outcome to the scalar signal [[reinforcement-learning-grpo|RL]]
optimizes. Built in [[stage-7-reward-design]] as [[training-reward]]. One of the three
stages where the real intellectual content lives ([[overview]]).

**The core axis.** Sparse vs. shaped → [[sparse-vs-shaped-reward]]:
- **Sparse** (win/loss, floor reached): honest, but gives the agent little to learn from.
- **Shaped** (incremental: damage, survival, progress): more signal, faster learning —
  but invites [[reward-hacking]].

**The deep lesson.** You get the behavior you *specify*, not the behavior you *want*. A
shaped reward that rewards "damage dealt" may produce an agent that farms damage without
winning. Expect to start shaped, watch for hacking, and adjust.

**Discipline (success bar).** Ship a reward you can *defend* **and** a written
hypothesis of how it could be gamed — so [[stage-8-rl-fine-tuning|Stage 8]] knows what
to watch for. Note that Stage 3's invalid-output penalties
([[how-to-handle-invalid-model-output]]) also become part of this signal.

**Source:** [[2026-07-22-project-pipeline]].
