---
title: Hermes-NotebookLM Integration
created: 2026-04-28
updated: 2026-04-29
type: concept
tags: [ai-agent, notebooklm, pkm, session-stability]
---

# Hermes-NotebookLM Integration

This concept describes the workflow for augmenting AI agents (like Hermes) with the research and multi-modal generation capabilities of Google NotebookLM.

## Core Advantages
- **Augmented Knowledge**: Provides agents with a massive, RAG-optimized external memory.
- **Multi-modal Synthesis**: Enables agents to trigger audio/video summaries of research materials.
- **Reduced Costs**: Offloads document analysis to Google's specialized infrastructure.

## Stability & Persistence
- **Session Management**: Switched to the **win4r** fork of `notebooklm-py` to resolve 15-minute cookie expiration issues.
- **Heartbeat System**: Implemented a 20-minute cron heartbeat task to keep the session alive.
- **Storage**: Cookies and session state maintained at `/home/joe1280/.notebooklm/profiles/default/storage_state.json`.

## Multi-modal & Language Support
- **Multi-lingual Audio**: Supports 81 languages. Use `--language zh_Hans` for simplified Chinese briefings.
- **Studio Integration**: Capable of generating technical slides and video overviews (currently in grayscale testing).
- **CLI Robustness**: Fixed `--output` and `--wait` flag handling in the automated pipeline.

## Proven Workflow
1. **Source Ingestion**: Add URLs or YouTube videos via `notebooklm source add`. 
   - *Pro Tip*: This bypasses most IP-based download blocks as Google performs the ingestion.
2. **Analysis**: Use `notebooklm ask` for deep analysis.
3. **Artifact Generation**: Generate Mind Maps or Audio briefings.

## Related
- [[ds2api]]: Underlying model provider.
- [[youtube-download-tricks]]: Alternative methods when NotebookLM ingestion is insufficient.
