---
name: llm-wiki
description: "Karpathy's LLM Wiki: build/query interlinked markdown KB."
version: 2.2.0
author: Hermes Agent
metadata:
  hermes:
    category: research
---

# Karpathy's LLM Wiki

Build and maintain a persistent, compounding knowledge base as interlinked markdown files.
Based on Andrej Karpathy's LLM Wiki pattern.

## Shared Multi-Agent Deployment

When running multiple profiles (e.g., bot_sixth, bot_seventh), use a central shared directory:
1. Clone the Wiki to `/root/hermes-shared/wiki`.
2. Link every agent's `home/wiki` to that path.
3. Set `WIKI_PATH` in each `.env`.

## Critical Pitfall: Active Profile Link Modification

**Never** delete or modify the symlink of the `WIKI_PATH` belonging to the **currently active** profile from within a terminal session that is using that path as its `workdir`.

- **The Symptom**: Future terminal calls fail with `FileNotFoundError` because the shell's current working directory no longer exists.
- **The Fix**: Use `execute_code` to call `os.chdir("/")`, then use Python's `os.symlink` and `os.unlink` to repair the links using absolute paths. Avoid using `terminal()` until the working directory path is physically restored.

## Core Operations

1. **Orientation**: Read `index.md` and `log.md` before any operation.
2. **Ingest**: Add raw sources to `raw/`, update `entities/` or `concepts/`, link back to index.
3. **Log**: Every action must be recorded in `log.md`.
