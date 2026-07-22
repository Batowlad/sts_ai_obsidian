# Project pipeline — LLM plays Slay the Spire (SFT + RL)

> Immutable raw input. Ingested 2026-07-22. Do not edit — this is source of truth.
> Wiki summary: [[2026-07-22-project-pipeline]] (in wiki/sources/).

Here is the project pipeline:

## Stage 0: Environment and orientation

Goal: get the simulator and model both running, separately, before connecting anything.

What's used: sts_lightspeed (build it, get the Python bindings working), Hugging Face Transformers (load a small Qwen instruct model), a GPU you can access.

What you do: Build the simulator, write a throwaway script that plays a game with random legal actions, and separately load the model and generate from a trivial prompt. Read the simulator's API surface carefully — what does a game state object actually contain, what does an action look like, how do you query legal actions, how do you detect game-over.

The learning gap: The simulator's API is your foundation and there's no tutorial for it. Spend real time in its source and examples figuring out the data model. Specifically work out: how is game state represented, how do you enumerate legal actions at a given decision point, and how do you step the game forward. Don't proceed until you can drive a full random game start to finish from Python.

Success check: A random agent plays complete games and you can print the outcome (won/lost, floor reached).

## Stage 1: The game interface layer

Goal: a clean Python wrapper around the simulator that the rest of your code talks to, so nothing else needs to know simulator internals.

What's used: Your env/game_interface.py, building on the Stage 0 understanding.

What you do: Design a class that exposes something like reset(), get_state(), get_legal_actions(), step(action), is_terminal(), get_result(). This is your abstraction boundary. The point is that training/ and agent/ code never touches sts_lightspeed directly — only this interface.

The learning gap: The design question is yours: what's the right interface? Look at how Gymnasium structures environments (reset/step/spaces) for inspiration, but you're not bound to it here since you're not using SB3. The judgment call — what to expose, what to hide — is a real software design exercise. Getting the abstraction boundary right is what makes the later stages tractable.

Success check: You can play a random game using only your interface class, never importing the simulator elsewhere.

## Stage 2: State encoding (game → text)

Goal: turn a game state into a text prompt the model can reason about.

What's used: Your env/state_encoder.py. Pure Python; no ML yet.

What you do: Write the function that takes a game state and produces a clear textual description — current HP, energy, hand (with what each card does), enemies and their intents, relics, the decision being asked for. This is one of the two highest-leverage parts of the whole project: the quality of this encoding largely determines how well the model can play, because the model can only reason about what you tell it.

The learning gap (this one's deep): There's no right answer, and the tradeoffs are real. More detail helps the model reason but costs context length (and a full run is 1000+ decisions, so context pressure is constant). Should card descriptions be included every turn or assumed known? How do you represent the deck — fully, or summarized? How do you make enemy intents legible? You'll likely iterate on this encoding many times as you watch the model fail in ways traceable to bad encoding. Treat your first version as a draft. The exercise: design an encoding, watch where the model gets confused, trace the confusion back to the encoding, revise.

Success check: You can print a state encoding and a knowledgeable human could play correctly from it alone. That's the bar — if a person can't play from your text, the model certainly can't.

## Stage 3: Action parsing (text → game)

Goal: turn the model's text output into a legal game action, handling the messy reality that models produce imperfect text.

What's used: Your env/action_parser.py.

What you do: Parse the model's output into an action your interface accepts. Then handle the failure modes: malformed output, actions referencing things that don't exist, illegal-but-well-formed actions (playing a card you can't afford).

The learning gap: The design decision is how to handle invalid output, and it has real consequences for training. Options to weigh: re-prompt the model to try again, constrain generation to only legal outputs, or assign a default/penalty. Each has tradeoffs for both play quality and training dynamics (e.g., penalties become part of your reward signal later). Think about which failures should be "free retries" versus which should cost the agent. There's also a parsing-robustness craft here: how forgiving should your parser be about formatting? Too strict and good decisions get thrown out on formatting; too loose and you misread the model's intent.

Success check: Feed the parser a variety of model outputs (including deliberately broken ones) and confirm it either extracts the right action or fails gracefully in the way you designed.

## Stage 4: The agent loop and prompt design

Goal: wire state-encoder → model → action-parser → game into a loop that plays full games, with no training yet.

What's used: agent/policy.py, agent/prompts.py, Transformers for generation.

What you do: Assemble the loop. Design the system prompt (who the model is, what the game is, what format to respond in). Decide the chain-of-thought question now: do you let the model reason before answering, or force a direct action? Make this configurable — it's one of your best research variables later.

The learning gap: Prompt design is empirical and underspecified. You'll discover that small wording changes meaningfully shift play quality. The configurable-reasoning decision also has design weight: if you allow reasoning, how do you separate the reasoning from the final action in the output so your parser can find the action? That output-format design is a real puzzle.

Success check: The base model plays full games end to end. Quality will be poor — that's expected and fine. The loop working is the milestone.

## Stage 5: Baseline evaluation

Goal: measure how well the un-fine-tuned model plays, with metrics you'll reuse for everything.

What's used: eval/evaluate.py, eval/metrics.py, Weights & Biases for logging.

What you do: Run many games (varied seeds), compute win rate, average floors climbed, average score. Build this measurement harness carefully — every later claim depends on it. Test prompt variations here (does CoT help the base model? few-shot examples?) and record each.

The learning gap: The statistical thinking is the lesson. How many games is enough to trust a win-rate number? (Win rate is a proportion — think about confidence intervals on proportions.) How do you control for seed variance so you're comparing fairly? This is exactly the empirical-rigor skill that matters for both quant and research, so don't shortcut it.

Success check: A documented baseline with numbers and uncertainty, e.g., "base model + CoT: 4% win rate over 200 games, reaches floor 6 on average."

## Stage 6: Supervised fine-tuning (SFT)

Goal: improve play by training on good gameplay examples.

What's used: data/collect_rollouts.py, training/sft.py, TRL (SFTTrainer), PEFT (LoRA), Datasets, bitsandbytes.

What you do: Collect demonstration data (winning or strong games — from the base model's better runs, and/or a heuristic/MCTS agent if the simulator offers one), format it as state→action (or state→reasoning→action) examples, and SFT the model with LoRA.

The learning gaps (several): Data quality is the big one — you're choosing what counts as a "good" example, and garbage in means garbage out. How do you filter for quality? How much data is enough? Then there's the format question: does each training example carry reasoning or just the action, and how does that interact with your Stage 4 format choice? And the LoRA config (rank, target modules, learning rate) is a set of knobs you'll learn to tune from the PEFT and TRL docs. The TRL SFTTrainer quickstart shows the skeleton; mapping your game data into the dataset format it expects is the part you work out.

Success check: The SFT model beats the Stage 5 baseline on your metrics, measured the same way.

## Stage 7: Reward design

Goal: define the signal the RL stage optimizes.

What's used: training/reward.py.

What you do: Map game outcomes to a reward number. Decide between sparse (win/loss, floors) and shaped (incremental rewards for damage, survival, progress), knowing shaped gives more signal but invites reward hacking.

The learning gap: This is conceptually central to RL and there's no clean answer. Sparse rewards are honest but give the agent little to learn from; dense rewards learn faster but the agent may exploit them in ways that don't actually win games. You'll likely start shaped, watch for hacking, and adjust. Designing a reward that produces the behavior you actually want — rather than the behavior you literally specified — is one of the deepest lessons in RL, and you'll feel it here directly.

Success check: A reward function you can defend, plus a hypothesis about how it might be gamed (so you know what to watch for).

## Stage 8: RL fine-tuning

Goal: improve play through reinforcement learning on game outcomes. The hard stage; budget the most time and patience.

What's used: training/rl.py, TRL (GRPOTrainer recommended over PPO — no separate critic, lighter on your GPU), PEFT, vLLM (optional, for faster rollouts), W&B.

What you do: Set up the loop where the model plays games, gets reward, and updates. Connect your reward function as the trainer's reward signal. Keep KL regularization so the model doesn't drift into degeneracy. Start from your SFT checkpoint, not the base model.

The learning gaps (this is where you'll struggle productively): GRPO expects a reward function over generated outputs — but your "output" is a whole game, not a single response. Reconciling "the trainer wants to reward generations" with "my reward comes from a multi-step game" is the central wiring puzzle, and working it out is most of the intellectual content of this stage. Rollout cost is brutal (each step = full games), so you'll think hard about efficiency. And the failure modes — silent non-learning, reward hacking, mode collapse, instability — are diagnostic challenges you'll work through by staring at curves and transcripts.

The critical fallback: if RL won't converge after honest effort, your SFT result plus an analysis of why RL failed is a legitimate, shippable project. Decide in advance how long you'll fight before falling back. Knowing when to stop is a research skill.

Success check: Performance improves over the SFT baseline through RL training, shown as a curve over training steps.

## Stage 9: Experiments

Goal: answer a specific research question — the thing that makes this research, not a demo.

What's used: Everything above, run as controlled comparisons; eval/ for measurement; plotting in notebooks.

What you do: Pick one question and answer it rigorously. The strongest option given your setup: does chain-of-thought reasoning help, and does it survive RL fine-tuning? (Train with and without reasoning; measure; check whether RL preserves or erodes the reasoning.) Alternatives: scaling with model size (0.5B/1.5B/3B), or SFT-vs-RL contribution.

The learning gap: Experimental design. Multiple seeds per condition (RL is noisy — one run is not evidence), proper controls, honest reporting with error bars. This is the single most important stage for your portfolio signal, so the rigor here is the point, not an afterthought.

Success check: Plots that answer the question with quantified uncertainty, and an explanation of why you see what you see.

## Stage 10: Writeup

What's used: GitHub (clean repo, real README), a blog post.

What you do: Research question, setup, method, results with labeled plots and error bars, honest failures, limitations, next steps — and crucially, position against existing Slay the Spire AI work so your contribution is legible.

## Where the real learning concentrates

If you want to know which gaps are the valuable ones to struggle through rather than route around: the state encoding (Stage 2), the reward design (Stage 7), and the RL wiring (Stage 8) are where the genuine intellectual content lives. The interface and parsing stages are good engineering practice but more mechanical. If you find yourself tempted to find a complete example to copy for stages 2, 7, or 8 — resist hardest there, because working those out yourself is most of what this project teaches and most of what you'll have to speak to in an interview.
