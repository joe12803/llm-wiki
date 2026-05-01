---
title: Industrial Mining Workflow
created: 2026-05-01
updated: 2026-05-01
type: concept
tags: [workflow, automation, research, mining]
---

# Industrial Mining Workflow

A standardized 6-stage pipeline for autonomous technical research and knowledge extraction.

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
