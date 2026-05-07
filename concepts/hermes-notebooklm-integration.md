---
title: Hermes-NotebookLM Integration
created: 2026-04-28
updated: 2026-05-04
type: concept
tags: [ai-agent, notebooklm, pkm, session-stability, proxy-bypass]
---

# Hermes-NotebookLM Integration

This concept describes the workflow for augmenting AI agents (like Hermes) with the research and multi-modal generation capabilities of Google NotebookLM.

## Core Advantages
- **Augmented Knowledge**: Provides agents with a massive, RAG-optimized external memory.
- **Multi-modal Synthesis**: Enables agents to trigger audio/video summaries of research materials.
- **Reduced Costs**: Offloads document analysis to Google's specialized infrastructure.
- **Bypass Censorship/Blocks**: The **NotebookLM Proxy** strategy uses Google's infrastructure to ingest content (e.g., YouTube transcripts) that is otherwise blocked for data center IPs.

## Stability & Persistence (2026-05-07 Update)
- **Auto-Refresh Trigger**: Discovered `NOTEBOOKLM_REFRESH_CMD` env var in `win4r/notebooklm-py`. Setting it to `notebooklm login --browser-cookies chrome` enables automatic cookie renewal upon 401/403 errors.
- **Authentication Sync**: Implemented a **Hard Link** strategy between `Claude-API` and `NotebookLM` for `storage_state.json`. This allows sharing authentication cookies across tools.
- **Heartbeat System**: Implemented a 20-minute cron heartbeat task (`notebooklm list`) to prevent session expiration for both tools.
- **Industrial Mining Pipeline**: Upgraded to **v2.1**, formally integrating NotebookLM Studio features (Data Tables, Mind Maps, Audio/Video Overviews) into the "Mining" and "Storage" stages.
- **Mobile Knowledge Consumption**: Treat audio/video briefings as core "industrial" assets for mobile-friendly consumption.
- **Multi-modal Support**: Supports generating technical briefings in Chinese (`zh_Hans`) using the `--language` flag.

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
