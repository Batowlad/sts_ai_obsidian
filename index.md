# Index

Content catalog for this project brain. Every page is listed under its category with a
one-line summary. **Read this first when answering a query.** Updated on every ingest.

> Front door: [[overview]] — the living vision, pipeline map, and thesis.
> Current stage: **0 — environment & orientation** (nothing built yet).

---

## Sources
- [[2026-07-22-project-pipeline]] — the 10-stage roadmap; each stage annotated with its learning gap + success check. _(roadmap, 2026-07-22)_

## Stages (the pipeline)
- [[stage-0-environment-orientation]] — get simulator + model each running; random agent plays full games. _(planned)_
- [[stage-1-game-interface]] — clean wrapper around the sim; the abstraction boundary. _(planned)_
- [[stage-2-state-encoding]] ★ — game → text; caps how well the model can play. _(planned)_
- [[stage-3-action-parsing]] — text → legal action; handle imperfect model output. _(planned)_
- [[stage-4-agent-loop-and-prompts]] — wire encoder→model→parser→game; design prompts + CoT flag. _(planned)_
- [[stage-5-baseline-evaluation]] — measure the un-tuned model with reusable, uncertainty-aware metrics. _(planned)_
- [[stage-6-sft]] — supervised fine-tune on strong-play demonstrations (LoRA). _(planned)_
- [[stage-7-reward-design]] ★ — define the RL reward signal; sparse vs. shaped. _(planned)_
- [[stage-8-rl-fine-tuning]] ★ — GRPO on game outcomes; the hard stage. _(planned)_
- [[stage-9-experiments]] — one rigorous research question, with error bars. _(planned)_
- [[stage-10-writeup]] — clean repo + blog post; position vs. prior STS AI work. _(planned)_

## Components (code modules)
- [[env-game-interface]] — `env/game_interface.py`; the only module that imports the sim. _(planned, Stage 1)_
- [[env-state-encoder]] — `env/state_encoder.py`; renders state → prompt text. _(planned, Stage 2)_
- _Redlinks to create when built:_ `env/action_parser.py`, `agent/policy.py`, `agent/prompts.py`, `eval/evaluate.py`, `eval/metrics.py`, `data/collect_rollouts.py`, `training/sft.py`, `training/reward.py`, `training/rl.py`.

## Concepts
- [[slay-the-spire]] — the game as an AI domain; long horizon, sparse win, RNG. _(developing)_
- [[state-encoding]] ★ — game→text; the model reasons only about what you tell it. _(developing)_
- [[reward-design]] ★ — outcome → scalar signal; the intent-vs-letter problem. _(developing)_
- [[reinforcement-learning-grpo]] ★ — group-relative RL, no critic; the wiring puzzle. _(developing)_
- [[supervised-fine-tuning]] — imitate strong play; seeds the RL checkpoint. _(developing)_
- [[lora-peft]] — parameter-efficient fine-tuning that fits one GPU. _(developing)_
- [[chain-of-thought-reasoning]] — reason-then-act as a configurable research variable. _(developing)_
- [[reward-hacking]] — maximizing the reward's letter while missing its intent. _(developing)_
- [[evaluation-statistics]] — win-rate CIs, seed control, multiple seeds. _(developing)_
- [[constrained-decoding]] — force only-legal output; one answer to invalid parsing. _(stub)_

## Decisions
- [[llm-as-policy]] — _accepted_: LLM is the policy (text in/out), not a from-scratch net.
- [[use-grpo-over-ppo]] — _proposed_: GRPO (no critic, lighter GPU) over PPO.
- [[lora-over-full-finetuning]] — _proposed_: LoRA/PEFT over full fine-tuning.

## Open questions
- [[encoding-detail-vs-context-budget]] ★ — _open_: detail vs. 1000+-decision context pressure. _(Stage 2)_
- [[what-to-expose-in-the-interface]] — _open_: interface surface; what to hide. _(Stage 1)_
- [[how-to-handle-invalid-model-output]] — _open_: re-prompt vs. constrain vs. penalize. _(Stage 3)_
- [[cot-vs-direct-action]] — _leaning configurable_: reason-then-act vs. direct. _(Stage 4)_
- [[reasoning-in-sft-data]] — _open_: reasoning in SFT examples or action-only. _(Stage 6)_
- [[sparse-vs-shaped-reward]] — _open_: honesty vs. signal (hacking risk). _(Stage 7)_
- [[grpo-reward-over-a-whole-game]] ★ — _open_: reward a whole game under GRPO. _(Stage 8)_
- [[when-to-abandon-rl]] — _open_: pre-commit the give-up threshold. _(Stage 8)_
- [[how-many-games-to-trust-a-win-rate]] — _open_: sample size for a proportion. _(Stage 5)_
- [[does-cot-survive-rl]] — _open_: leading Stage 9 experiment. _(Stage 9)_

## References (external tools)
- [[sts-lightspeed]] — C++ StS simulator + Python bindings; the environment.
- [[qwen]] — small open instruct LLM; the policy.
- [[hugging-face-transformers]] — model loading + generation.
- [[trl]] — SFTTrainer + GRPOTrainer.
- [[lora-peft]] — (concept page doubles as the PEFT/LoRA reference).
- [[weights-and-biases]] — experiment tracking + curves.
- [[gymnasium]] — interface-design inspiration only.
- [[vllm]] — optional fast rollouts for RL.
- _Prior-art redlinks (fill at Stage 10):_ `spirecomm`, `sts-battle-ai`, `decapitate-the-spire`.

## Syntheses
- _(none yet — filed-back answers land here.)_

---

_Last updated: 2026-07-22 (ingested: Project pipeline — 45 wiki pages created). ★ = highest-leverage._
