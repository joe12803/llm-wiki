# Hermes NotebookLM Integration

This concept describes the workflow for augmenting AI agents (like Hermes) with NotebookLM's private knowledge context, multi-lingual briefing capabilities, and distributed credentials synchronization.

---

## 🛠️ Key Capabilities

- **Bypass Censorship/Blocks**: The **NotebookLM Proxy** strategy uses Google's infrastructure to ingest content (e.g., YouTube transcripts) that is otherwise blocked for data center IPs.
- **Distributed Session Sync**: Ensures that Playwright Google cookies are seamlessly shared between local and remote agents.

---

## 📅 Chronological Milestones

### [2026-05-15] Keepalive Stability & Multi-Day Longevity
- **Session Health**: Verified that the Playwright session state remains fully active and healthy under the 20-minute heartbeat mechanism, lasting over a week without needing a manual re-login.
- **Silent Maintenance**: Confirmed that the `notebooklm_keepalive_sync.py` script exits silently when no credentials changes are detected, avoiding cron job notification spam.

### [2026-05-10] Distributed Credentials Sync & Heartbeats
- **Distributed Credentials Sync**: Standardized `notebooklm_keepalive_sync.py` to synchronize `storage_state.json` between local environments and the `hermes-claw` repository. This ensures that even ephemeral agents in GitHub Actions can inherit active Google sessions.
- **Heartbeat Stability**: Confirmed the 20-minute heartbeat (`notebooklm list` run via `sudo -u joe1280`) effectively prevents session logout across multiple days of inactivity.

### [2026-05-07] Auto-Refresh & Multi-Agent Bridging
- **Auto-Refresh Trigger**: Discovered `NOTEBOOKLM_REFRESH_CMD` env var in `win4r/notebooklm-py`. Setting it to `notebooklm login --browser-cookies chrome` enables automatic cookie renewal upon 401/403 errors.
- **Authentication Sync**: Implemented a **Hard Link** strategy between `Claude-API` and `NotebookLM` for `storage_state.json` to share cookies.
- **Industrial Mining Pipeline**: Upgraded to **v2.1**, formally integrating NotebookLM Studio features (Data Tables, Mind Maps, Audio/Video Overviews) into the "Mining" and "Storage" stages.

---
*Back to [Index](../index.md) or [Main README](../README.md).*
