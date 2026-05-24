# llm-wiki

Based on Andrej Karpathy's LLM Wiki pattern. A compounding, persistent, and organized knowledge base constructed as interlinked markdown files.

This repository tracks architectural diagrams, deployments, system environments, and conceptual guides for various tools integrated with our multi-agent framework (Hermes Agent).

---

## 📅 Chronological Logs

For daily synchronization records and system-wide steady-state verification history, check **[log.md](log.md)**.

## 🛠️ Main Projects & Entities

- **[ds2api](entities/ds2api.md)**: DeepSeek-to-OpenAI API bridge middleware. Tracks ARM64 optimizations, Nginx proxy setups, SSE buffer tuning, and non-root Docker permissions.
- **[gitnexus](entities/gitnexus.md)**: AI-native code graph indexer and MCP server. Maps codebases to structured graphs for tools like Claude Code and Cursor.
- **[hermes-claw](entities/hermes-claw.md)**: Deployment hub and session storage for Hermes Agent. Details credentials sync and persistent volume mapping.
- **[claude-api-bridge](entities/claude-api-bridge.md)**: High-availability middleware bridging reverse-engineered Claude sessions.
- **[evolver](entities/evolver.md)**: Multi-agent system optimization and self-evolving loops.

## 💡 Concepts & Architectural Guides

- **[Hermes NotebookLM Integration](concepts/hermes-notebooklm-integration.md)**: Heartbeats, cookie management (`storage_state.json`), and the NotebookLM proxy strategy to bypass IP bans.
- **[Industrial Mining Workflow](concepts/industrial-mining-workflow.md)**: Our structured 7-stage pipeline (Exploration, Drilling, Mapping, Mining, Storage, Sync, Context) for knowledge mining.
- **[YouTube Download Tricks](concepts/youtube-download-tricks.md)**: Cookie conversion scripts (Playwright to Netscape) and GitHub Actions spoofing configurations to bypass crawler detection.
- **[Hindsight Integration](concepts/hindsight-integration.md)**: System status recovery and active session tracing protocols.

---
*Maintained automatically by Hermes Agent cron routines.*
