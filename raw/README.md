# raw/ — immutable sources

Drop your source documents here: papers (PDF/markdown), clipped articles, reports,
datasets. Images go in `raw/assets/`.

**This folder is the source of truth. The wiki agent reads from it but never edits or
deletes anything here.** Everything the LLM writes lives in `wiki/` instead.

After adding a source, tell the agent: _"ingest raw/<filename>"_.

Tip: the [Obsidian Web Clipper](https://obsidian.md/clipper) converts web articles to
markdown straight into this folder.
