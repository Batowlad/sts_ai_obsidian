---
type: concept
title: "Action-space design"
status: developing
source_count: 1
updated: 2026-06-05
tags: [reinforcement-learning, action-space, method]
---

# Action-space design

How an agent's available actions are represented. In
[[2021-08-15-creating-an-ai-for-slay-the-spire]] this was the single biggest source
of difficulty, and redesigning it was a turning point.

## Indirect vs direct actions
- **Indirect (failed):** the combat action was `<card-in-hand index> × <target index>`,
  e.g. `(4, 1)` = "play the card at hand-index 4 against monster 1." The effect of an
  index changes with whatever card sits there, so the agent must learn that
  "index 4 = 6 damage" only when index 4 happens to be Strike.
- **Direct (better):** a "button" should always have the same effect — key a card by
  its **identity/ID**, not its hand position. → [[direct-action-spaces-easier-to-learn]].

## Overloading the action space (anti-pattern)
The author compressed one action space to cover the **entire game**, so the same
action meant "play 2nd card vs 1st monster" in combat but "buy 2nd relic" in a shop.
Thought to be a mistake — semantics shifting by context makes learning harder.

## Better structure: autoregressive
The successful redesign used **[[autoregressive-actions]]** — deciding an action in
dependent stages rather than one flat joint space.

## Tooling implication
Supporting invalid-action handling cleanly motivated [[action-masking]], which drove
the choice of [[rllib]].

## Related
[[model-free-reinforcement-learning]] · [[autoregressive-actions]] · [[sc2le-pysc2]]
