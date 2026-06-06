---
type: claim
title: "Direct action spaces (button = fixed effect) are easier to learn than indirect (index → variable effect) ones"
status: supported
confidence: medium
supported_by: [[[2021-08-15-creating-an-ai-for-slay-the-spire]]]
contradicted_by: []
updated: 2026-06-05
tags: [reinforcement-learning, action-space]
---

# Claim: direct action spaces are easier to learn than indirect ones

When an action's effect is **stable** ("pressing a button always does the same thing")
the agent learns faster than when an action is an **index whose effect depends on
context** (e.g., "play card at hand-index 4," where index 4 might be Strike or
anything else). From [[2021-08-15-creating-an-ai-for-slay-the-spire]].

## Evidence
- **For:** author's reasoning and experience; the indirect `<hand index> × <target>`
  space contributed to *Attempt 1*'s failure, and keying by card identity plus
  [[autoregressive-actions]] worked better.
- Single-project, qualitative evidence — no controlled comparison. Confidence medium.

## Related
[[action-space-design]] · [[autoregressive-actions]] · [[sc2le-pysc2]]
