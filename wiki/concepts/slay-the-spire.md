---
type: concept
title: "Slay the Spire (as an AI domain)"
status: developing
source_count: 1
updated: 2026-06-05
tags: [slay-the-spire, domain, roguelite]
---

# Slay the Spire (as an AI domain)

Slay the Spire is a single-player deckbuilding roguelite. As a target for AI, its
appeal is that it can be played many times (good for [[model-free-reinforcement-learning|RL]]),
but its **roguelite traits make a single playing policy hard to learn**.

## Why it's hard (per [[2021-08-15-creating-an-ai-for-slay-the-spire]])
- Randomness throughout
- Procedural map generation
- Card drafting decisions
- Convertible currencies — health, gold, cards, etc., traded against each other
- Long reward horizon
- Powerful but **rare synergies** between relics and cards

## Structure relevant to agents
- A **dungeon** is ~15 sequential encounters (combat, shops, events, treasure) ending
  in a boss combat. The first dungeon is **Exordium**.
- Distinct sub-problems: **combat**, **card drafting**, **shop purchasing**, **events**,
  and **map/path selection** — which motivates [[hierarchical-agents|composite-agent]]
  designs.
- The **monster distribution per dungeon is fixed** (not seeded per game), though the
  specific monsters sampled are random — relevant to what counts as "cheating" for an
  assist tool.
- **HP** is arguably the most important currency; predicting HP loss underpins the
  proposed [[hp-loss-model]].

## Related
- Prior agents: [[spirecomm]], [[sts-battle-ai]]
- Tooling: [[decapitate-the-spire]] (headless clone for fast training)
