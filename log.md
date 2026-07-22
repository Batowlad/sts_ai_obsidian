# Log

Chronological, append-only record of everything that happens to the wiki — ingests,
queries, lint passes. Newest at the bottom. Each entry uses a grep-able prefix:

```
grep "^## \[" log.md | tail -5
```

---

## [2026-07-22] note   | wiki initialized (fresh project brain)
Set up the LLM Wiki as a **project brain** for the "LLM plays Slay the Spire (SFT+RL)"
side project. Created `CLAUDE.md` schema (project-brain archetype: stages / components /
concepts / decisions / questions / references / syntheses / sources), `index.md`,
`log.md`, `raw/README.md`, and the folder structure. Note: a prior *research* wiki about
STS AI exists only in the `git init` commit (b1da19b), abandoned by choice — do not
resurrect it; this is a distinct project.

## [2026-07-22] ingest | Project pipeline — LLM plays Slay the Spire (SFT + RL)
First source ingested (the 10-stage roadmap). Saved raw at
`raw/2026-07-22-project-pipeline.md`; summary [[2026-07-22-project-pipeline]]. Created
**45 wiki pages**: [[overview]] (vision + pipeline map + thesis); 11 stage pages
[[stage-0-environment-orientation]]…[[stage-10-writeup]]; 2 components
[[env-game-interface]], [[env-state-encoder]] (other 9 modules left as redlinks); 10
concepts ([[state-encoding]], [[reward-design]], [[reinforcement-learning-grpo]],
[[supervised-fine-tuning]], [[lora-peft]], [[chain-of-thought-reasoning]],
[[reward-hacking]], [[evaluation-statistics]], [[constrained-decoding]],
[[slay-the-spire]]); 3 decisions ([[llm-as-policy]] accepted, [[use-grpo-over-ppo]] &
[[lora-over-full-finetuning]] proposed); 10 open questions (incl. the three
high-leverage: [[encoding-detail-vs-context-budget]], [[sparse-vs-shaped-reward]],
[[grpo-reward-over-a-whole-game]]); 7 references. Seeded the thesis (encoding/reward/RL
are where the real learning is) and updated [[index]].
**Tensions flagged:** shaped reward ↔ [[reward-hacking]]; [[cot-vs-direct-action]] output
format ↔ [[how-to-handle-invalid-model-output]]; [[when-to-abandon-rl]] should be
pre-committed before Stage 8.
**Dangling redlinks (intended future pages):** 9 component modules; prior-art
[[spirecomm]], [[sts-battle-ai]], [[decapitate-the-spire]].
