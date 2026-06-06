---
type: concept
title: "Autoregressive actions"
status: developing
source_count: 1
updated: 2026-06-05
tags: [reinforcement-learning, action-space, method]
---

# Autoregressive actions

An [[action-space-design]] technique where a complex action is chosen in **dependent
stages**, each pass through the model aware of the **partial action chosen so far**.
The author of [[2021-08-15-creating-an-ai-for-slay-the-spire]] adopted it from the
[[sc2le-pysc2|SC2LE paper]] and found it far more natural than a flat, overloaded
action space.

## How it works (the source's example)
1. First pass: decide the action *type* — play a card, use a potion, etc.
2. If "play a card": another pass decides *which* card.
3. If the card is complete (e.g., Defend), send it to the game.
4. If it needs more (e.g., **Survivor** requires discarding a card): another pass
   chooses *which card to discard*.

Each pass conditions on the partial actions already selected — that's the
"autoregressive" part. Note: this is awareness of the **current** partial action, not
of previous **completed** actions.

## Why it helps
- Avoids one flat point in action space carrying several meanings by "request type."
- Naturally expresses actions that require follow-up choices.

## Related
[[action-space-design]] · [[direct-action-spaces-easier-to-learn]] · [[sc2le-pysc2]] ·
[[model-free-reinforcement-learning]]
