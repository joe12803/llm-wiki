---
title: Industrial Mining Workflow
created: 2026-04-29
updated: 2026-05-02
type: concept
tags: [mining, workflow, notebooklm, automation, research]
---

# Industrial Mining Workflow

A 6-stage industrial-grade knowledge extraction pipeline for deep codebase and document analysis.

## Workflow Stages (v2.1)
1. **Reconnaissance**: Initial exploration using `pygount` and `graphify` to understand project topology.
2. **Ingestion**: Uploading codebase/documentation to [[hermes-notebooklm-integration]].
3. **Mining**: Deep technical analysis using specialized AI agents and NotebookLM "Data Tables".
4. **Synthesis**: Generating multi-modal briefings (Audio Podcast, Mind Maps, Technical Slides).
5. **Storage**: Syncing all assets to Feishu (Lark) Wiki and GitHub repositories.
6. **Distribution**: Sharing mobile-friendly audio briefings for convenient consumption.

## Key Updates (2026-05-02)
- **Multi-modal Assets**: Audio briefings (MP3) and Video overviews are now treated as primary artifacts.
- **Tooling**: Integrated `lark-cli` for automated uploads to Feishu Drive.
- **Verification**: Added `notebooklm list` heartbeat to ensure tool stability during long mining runs.

## Pipeline Stages

### 1. Exploration (勘探)
Identification of target repositories or documentation sites.

### 2. Drilling (钻探)
Using `driller.py` to refine codebases into concentrated "mining packs" (context bundles).

### 3. Extraction (开采)
Analysis using LLMs and tools to identify core logic nodes (e.g., `wa`, `oa`, `ta` architecture).

### 4. Studio/Synthesis (图谱/多模态)
- **Graphify**: Generating architecture and dependency graphs.
- **NotebookLM**: Generating Multi-lingual Audio Briefings and technical slides.

### 5. Ingestion (入库)
Saving reports and assets to local Wiki and Feishu Drive.

### 6. Synchronization (同步)
Automated syncing across GitHub, Feishu Wiki, and Agent Shared Memory.

## Tooling
- `driller.py`: Context refinement.
- `notebooklm-py (win4r)`: RAG and synthesis.
- `lark-cli`: Feishu integration.
- `wiki_auto_sync.py`: Daily automated maintenance.
