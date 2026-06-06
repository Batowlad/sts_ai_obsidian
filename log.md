# Log

Chronological, append-only record of everything that happens to the wiki — ingests,
queries, lint passes. Newest at the bottom. Each entry uses a grep-able prefix:

```
grep "^## \[" log.md | tail -5
```

---

## [2026-06-05] note   | wiki initialized
Set up the LLM Wiki system: `CLAUDE.md` schema (research deep-dive, one-source-at-a-time
ingest), `index.md` catalog, this log, `wiki/overview.md` thesis seed, and folder
structure (`raw/`, `raw/assets/`, `wiki/{sources,concepts,people,studies,claims,syntheses}`).
Ready for the first source.

## [2026-06-05] ingest | Creating an AI for Slay the Spire
First source ingested (toypiper, 2021). Created 17 pages: source summary
[[2021-08-15-creating-an-ai-for-slay-the-spire]]; concepts [[slay-the-spire]],
[[model-free-reinforcement-learning]], [[action-space-design]], [[autoregressive-actions]],
[[reward-engineering]], [[curriculum-learning]], [[hierarchical-agents]]; person
[[toypiper-jahabrewer]]; studies/prior-work [[spirecomm]], [[sts-battle-ai]],
[[decapitate-the-spire]], [[dqn-atari]], [[sc2le-pysc2]]; claims
[[hardcoded-ai-wont-scale]], [[tree-search-outplays-rl-but-cheats]],
[[direct-action-spaces-easier-to-learn]], [[frequent-rewards-beat-sparse]]. Seeded the
v0.1 thesis in [[overview]] and updated [[index]]. Flagged two open tensions (dense
rewards vs. reward hacking; "hardcoded won't scale" vs. strong non-learned search).
Redlink stubs left for future pages: [[rllib]], [[action-masking]], [[transfer-learning]],
[[hp-loss-model]], [[evaluation-gauntlet]], [[deepmind]], [[david-silver]].
