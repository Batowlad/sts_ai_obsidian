---
type: claim
title: "Frequent rewards train RL agents far better than sparse, delayed rewards over long episodes"
status: supported
confidence: medium
supported_by: [[[2021-08-15-creating-an-ai-for-slay-the-spire]]]
contradicted_by: []
updated: 2026-06-05
tags: [reinforcement-learning, reward-shaping]
---

# Claim: frequent rewards beat sparse rewards

Rewarding the agent **frequently** (dense feedback) trains far better than **sparse,
delayed** rewards spread over long episodes — the author's analogy is guiding a
blindfolded person with "warm / warmer / cool." From
[[2021-08-15-creating-an-ai-for-slay-the-spire]], where ~15-encounter dungeons with
only complete/die rewards failed to train.

## Evidence
- **For:** author's experience; aligns with well-known RL credit-assignment intuition.
- **Important counter-tension:** dense reward shaping is **dangerous** — a per-timestep
  penalty caused [[reward-engineering|reward hacking]] (the agent learned to die fast).
  So "more frequent" must also be "correctly specified." Not contradictory, but a
  caveat on naive application.

## Related
[[reward-engineering]] · [[curriculum-learning]] · [[model-free-reinforcement-learning]]
