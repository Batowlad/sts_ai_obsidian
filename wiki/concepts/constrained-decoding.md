---
type: concept
title: "Constrained decoding (action masking)"
status: stub
source_count: 1
updated: 2026-07-22
tags: [parsing, generation, decoding]
---

# Constrained decoding (action masking)

Restricting the model's generation so it can **only** produce a legal action —
e.g. grammar/regex-constrained decoding, or choosing among an enumerated legal-action
list rather than free text. One of the three candidate answers to
[[how-to-handle-invalid-model-output]] (alongside re-prompting and penalty/default),
relevant to [[stage-3-action-parsing]].

**Trade-off.** Guarantees legal, parseable output (no wasted rollouts on malformed
text) — but couples generation tightly to the [[env-game-interface|interface]]'s legal
actions and can interact awkwardly with [[chain-of-thought-reasoning|reasoning]] output.

_Stub — expand when Stage 3's invalid-output policy is decided._
**Source:** [[2026-07-22-project-pipeline]].
