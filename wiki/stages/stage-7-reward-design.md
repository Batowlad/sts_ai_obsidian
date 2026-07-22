---
type: stage
stage: 7
title: "Stage 7 — Reward design"
status: planned
goal: "Define the signal the RL stage optimizes."
success_check: "A reward function you can defend, plus a hypothesis about how it might be gamed."
builds: [[[training-reward]]]
tags: [reward, rl, high-leverage]
updated: 2026-07-22
---

# Stage 7 — Reward design ★

**Goal.** [[training-reward|training/reward.py]] maps game outcomes to a reward number
for [[stage-8-rl-fine-tuning|RL]]. See concept [[reward-design]].

**The choice.** Sparse (win/loss, floors) vs. shaped (incremental rewards for damage,
survival, progress) → open question [[sparse-vs-shaped-reward]]. Shaped gives more
signal but invites [[reward-hacking]].

**The learning gap (deep).** Conceptually central to RL, no clean answer. Sparse is
honest but gives little to learn from; dense learns faster but the agent may exploit it
in ways that don't actually win games. Expect to start shaped, watch for hacking, and
adjust. Designing a reward that produces the behavior you *want* rather than the one you
*literally specified* is one of RL's deepest lessons — and you'll feel it here.

**Success check.** A reward function you can defend **and** a written hypothesis about
how it might be gamed, so you know what to watch for in [[stage-8-rl-fine-tuning]].

**Builds:** [[training-reward]]. **Follows:** [[stage-6-sft]].
**Leads to:** [[stage-8-rl-fine-tuning]].
