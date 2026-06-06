# Index

The content catalog for this wiki. Every page is listed here under its category with
a one-line summary. **Read this first when answering a query.** I update it on every
ingest and whenever pages are created.

> Front door: [[overview]] — the living thesis and map of the wiki.

---

## Overview & syntheses
- [[overview]] — living thesis (v0.1): what makes a Slay the Spire AI hard, and which engineering choices matter most.

## Sources
- [[2021-08-15-creating-an-ai-for-slay-the-spire]] — toypiper's RL retrospective: failed attempts and lessons on action spaces, rewards, and decomposition. _(article, 2021-08-15)_

## Concepts
- [[slay-the-spire]] — the game as an AI domain; why roguelite traits make a single policy hard.
- [[model-free-reinforcement-learning]] — the method chosen; advantages, sample-inefficiency, PPO/A2C via rllib.
- [[action-space-design]] — direct vs. indirect actions; the overloaded-action anti-pattern.
- [[autoregressive-actions]] — choosing complex actions in dependent stages (from SC2LE).
- [[reward-engineering]] — sparse-reward failure and reward-hacking (die-fast) cautionary tale.
- [[curriculum-learning]] — decomposition into milestones and verifiable toy environments.
- [[hierarchical-agents]] — proposed orchestrator + specialist sub-agents (future work).

## People & organizations
- [[toypiper-jahabrewer]] — author of the source; built decapitate-the-spire. _(attribution inferred)_

## Studies
- [[spirecomm]] — ForgottenArbiter's hardcoded-heuristic STS AI/mod; used as the live-game interface.
- [[sts-battle-ai]] — combat-only A* tree-search agent; strong but exploits the RNG seed.
- [[decapitate-the-spire]] — author's headless Python clone for fast RL training.
- [[dqn-atari]] — DeepMind's Atari-from-pixels result; set the author's expectations too high.
- [[sc2le-pysc2]] — DeepMind StarCraft II env; source of the autoregressive-action idea.

## Claims
- [[hardcoded-ai-wont-scale]] — _open, low_: hardcoded heuristics won't reach high-level play (author opinion).
- [[tree-search-outplays-rl-but-cheats]] — _supported, medium_: A* combat search beats RL but sees the future via RNG.
- [[direct-action-spaces-easier-to-learn]] — _supported, medium_: stable-effect actions learn faster than index-indirect ones.
- [[frequent-rewards-beat-sparse]] — _supported, medium_: dense rewards train better — but beware reward hacking.

---

_Last updated: 2026-06-05 (ingested: Creating an AI for Slay the Spire)_
