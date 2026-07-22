# raw/ — immutable inputs

This folder is the **source of truth**. Everything here is curated by the builder and
**never modified by the LLM** — the wiki reads from these files and compiles them into
`wiki/`. If an input is wrong or outdated, add a newer input rather than editing an old
one, so the history stays honest.

**How to add a source**
1. Drop the file here (or paste it in chat and I'll save it here).
   - Naming: `YYYY-MM-DD-short-slug.md` (or keep the original name for clipped articles).
   - Images / screenshots go in `raw/assets/`.
2. Tell me to ingest it. I read it, discuss takeaways, then compile it into the wiki
   (source summary + stage/component/concept/decision/question/reference pages),
   update `index.md`, and log it. See `CLAUDE.md` → *Operation 1 — INGEST*.

**What lives here:** project notes and roadmaps, articles and docs you read, chat/call
transcripts, error logs, code snippets you want captured, screenshots.

Current inputs:
- `project-pipeline.md` — the 10-stage project roadmap → [[2026-07-22-project-pipeline]]
