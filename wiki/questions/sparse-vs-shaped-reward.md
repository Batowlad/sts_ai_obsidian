---
type: question
title: "Sparse vs. shaped reward?"
status: open
stage: 7
tags: [reward, rl, high-leverage]
updated: 2026-07-22
---

# Sparse vs. shaped reward?

**Crux.** Should [[training-reward|reward.py]] be **sparse** (win/loss, floor reached)
or **shaped** (incremental: damage, survival, progress)? See [[reward-design]].

**Trade-off.**
- **Sparse:** honest, aligned with actually winning — but little learning signal on a
  long horizon ([[slay-the-spire]]).
- **Shaped:** dense signal, faster learning — but invites [[reward-hacking]].

**Leaning (from the roadmap):** start shaped, watch for hacking, adjust. Pair whatever
you choose with a written **hypothesis of how it could be gamed** (the Stage 7 success
bar).

**Bites at** [[stage-7-reward-design]]; consequences land in [[stage-8-rl-fine-tuning]].
**Status:** open.
