---
type: source
title: "Creating an AI for Slay the Spire"
authors: [toypiper (jahabrewer)]
source_type: article
published: 2021-08-15
ingested: 2026-06-05
url: https://www.toypiper.com/creating-an-ai-for-slay-the-spire/
raw: raw/Creating an AI for Slay the Spire.md
tags: [reinforcement-learning, slay-the-spire, action-space, reward-shaping, project-retrospective]
status: ingested
---

# Creating an AI for Slay the Spire

A candid engineering retrospective by [[toypiper-jahabrewer]] on an (incomplete)
attempt to build a [[model-free-reinforcement-learning|model-free RL]] agent that
plays [[slay-the-spire]]. Structured as a sequence of failed attempts, each yielding
a concrete lesson.

## Summary
The author argues that the roguelite traits that make Slay the Spire fun —
randomness, procedural maps, card drafting, convertible currencies, long reward
horizons, rare relic/card synergies — also make it very hard to learn a single
playing policy. After several failed attempts with naive RL, the key insights were
about **action-space design**, **reward engineering**, and **breaking the problem
into measurable milestones**. The project has since narrowed to a **combat-only**
agent, with a roadmap of future ideas (hierarchical agents, per-encounter agents,
transfer learning, and an assist mod for human players).

## Key points
- **Prior work** the author knows of: [[spirecomm]] (hardcoded strategy; won't scale
  to high-level play, in the author's view) and [[sts-battle-ai]] (combat-only A\*
  search over the decision tree; plays better than any trained agent but "sees the
  future" by exploiting the hidden RNG seed — effectively save-scumming).
- **Approach chosen:** model-free RL via [[rllib]] (picked over stable-baselines for
  its [[action-masking]] support at the time); trained with PPO and A2C.
- **Attempt 0 — human speed:** hooked rllib to the real game via spirecomm, playing
  at human speed with graphics. Failed. Lesson → need a fast game; began building
  [[decapitate-the-spire]], a headless Python clone.
- **Attempt 1 — "RL is magic":** overhyped by [[dqn-atari|DeepMind's Atari-from-pixels
  result]], threw the whole game at a trainer. Failed. The action space was an
  overloaded `<card-in-hand index> × <target index>` with **indirection** between an
  index and its effect, plus episodes that were too long with rewards too sparse.
- **Attempt 2 — half measures:** shorter dungeons, easier combat, more frequent
  rewards — little improvement. Author walked away for a couple months.
- **Attempt 3 — hit the books:** read papers, watched [[david-silver]]'s lectures,
  drastically simplified the game.
  - **[[autoregressive-actions]]** (learned from the [[sc2le-pysc2|SC2LE paper]]):
    the model decides in stages (play card → which card → which discard), each pass
    aware of partial actions already chosen.
  - **[[curriculum-learning|Toy environments]]:** reduced the game to a single combat,
    then to trivial 2-action games, adding one feature at a time (observation-driven
    choice, then random-noise robustness) to get baselines for training cost.
- **Current status:** focusing on a **combat-only** agent — more approachable, easier
  to measure.

## Future work (roadmap)
- **[[hierarchical-agents|Composite agent]]:** an orchestrator agent makes map
  choices and delegates to specialist sub-agents (combat, drafting, shopping, events);
  open problem is pushing long-term strategy down to short-sighted subordinates
  (e.g., a 0–1 "how much trouble before using consumables" signal).
- **Per-encounter combat agents:** cheaper to train, tighter feedback loop, but huge
  infra cost and duplicated core knowledge across encounters.
- **[[transfer-learning]]:** seed the agent with expert play — blocked by the lack of
  a replay system (save files only encode current state); ideas include a replay-mod
  or reconstructing replays from YouTube videos.
- **Assist mod for humans** (no hidden-internal exploitation needed):
  - **[[hp-loss-model|Deck-analysis / HP-loss model]]:** predict HP loss for a combat
    from deck, relics, monster, ascension; dream is low-dimensional features matching
    established deckbuilding stats (single-target scaling, card manipulation, etc.) to
    guide card drafting.
  - **Map annotation:** annotate map nodes with expected HP loss + variance (monster
    distribution per dungeon is fixed, so not considered cheating).
- **[[evaluation-gauntlet]]:** hand-built combat puzzles with known-optimal answers to
  measure agent skill (e.g., the Defend-then-Strike lethal-timing puzzle).

## Notable data / examples
- The "evaluation gauntlet" lethal-timing puzzle (lines 199–205): monster attacks for
  11 with 7 HP; hand = 4 Defend + 1 Strike; draw pile = 2 Strike. Optimal is 3 Defend
  now, 2 Strike next turn → 0 HP lost; the naive Strike-first line loses 1 HP.
- Reward-hacking anecdote: a small per-timestep penalty (as a discount-factor
  substitute) made the agent learn to **die as fast as possible** (line 99).

## Connections
- Domain: [[slay-the-spire]]
- Method: [[model-free-reinforcement-learning]], [[action-space-design]],
  [[autoregressive-actions]], [[reward-engineering]], [[curriculum-learning]],
  [[hierarchical-agents]]
- Prior work: [[spirecomm]], [[sts-battle-ai]], [[decapitate-the-spire]]
- External references: [[dqn-atari]], [[sc2le-pysc2]], [[david-silver]]
- Author: [[toypiper-jahabrewer]]
- Claims grounded here: [[hardcoded-ai-wont-scale]],
  [[tree-search-outplays-rl-but-cheats]], [[direct-action-spaces-easier-to-learn]],
  [[frequent-rewards-beat-sparse]]
