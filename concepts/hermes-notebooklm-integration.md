# Hermes NotebookLM Integration

This concept describes the workflow for augmenting AI agents (like Hermes) with NotebookLM's private knowledge context, multi-lingual briefing capabilities, and distributed credentials synchronization.

---

## 🛠️ Key Capabilities

- **Bypass Censorship/Blocks**: The **NotebookLM Proxy** strategy uses Google's infrastructure to ingest content (e.g., YouTube transcripts) that is otherwise blocked for data center IPs.
- **Distributed Session Sync**: Ensures that Playwright Google cookies are seamlessly shared between local and remote agents.

---

## 📅 Chronological Milestones

### [2026-07-10] CLI Code Inspection & Authentication Lockout Diagnosis
- **CLI Code Inspection**: Checked the internal session module (`notebooklm/cli/session.py`) and confirmed that the CLI's `login` command initiates Playwright with `"headless": False`. This prevents automatic re-authentication in headless server environments or automated cron runner environments.
- **Doctor False Positive**: Documented that the `notebooklm doctor` command reports successful authentication (`✓ pass`) based solely on the structural existence of the `SID` cookie and configuration properties in `storage_state.json`, without verifying whether the session tokens are rejected as expired by Google's authentication backend.
- **Remediation**: Confirmed that automated keepalive scripts (`notebooklm_keepalive_sync.py`) are unable to self-heal. Manual re-authentication via `sudo -u joe1280 notebooklm login` remains a hard requirement on the host machine to re-generate valid cookies.


### [2026-07-08] Continued Session Expiration & System Constraints
- **Google Authentication Lockout**: The NotebookLM session remains expired. The automated heartbeat cron jobs continue to log: `Error: Authentication expired or invalid. Run 'notebooklm login' to re-authenticate.`
- **Manual Intervention Required**: Automated state recovery is unable to bypass Google's login redirects. New browser cookies must be generated manually on the host using `sudo -u joe1280 notebooklm login` to re-establish the Playwright storage state.

### [2026-07-02] Storage State Restoration Attempt & Continued Expiration
- **Storage State Copying**: Attempted to restore the NotebookLM session by copying the storage state (`storage_state.json`) from the bot's current active profile `/root/.hermes/profiles/bot_seventh/home/.notebooklm/profiles/default/storage_state.json` to the target `joe1280` user's directory `/home/joe1280/.notebooklm/profiles/default/storage_state.json` and updating its ownership.
- **Expiration Verified**: Even with the restored profile, `notebooklm list` and `notebooklm auth check --test` continued to fail. This confirmed that the credentials (SIDCC/OSID/etc.) have fully expired on Google's servers, rendering all backup cookies invalid.
- **Manual Login Required**: Headless automatic cookie renewal cannot bypass Google's redirect to the sign-in page. A manual interactive login (`notebooklm login`) under user `joe1280` is needed to re-establish a valid session.

### [2026-07-01] Session Expiration & Chromium Multi-Profile Conflict
- **Google Session Expiration**: The Google session for NotebookLM expired around late June 2026. Keepalive checks using `sudo -u joe1280 notebooklm list` now fail with `Authentication expired or invalid. Run 'notebooklm login' to re-authenticate.`
- **Chromium Multi-Profile Discrepancy**: Identified a discrepancy in the user data directories: OpenClaw uses `/home/joe1280/.config/chrome-openclaw-debug` (listening on remote debugging port 9222), while `google_browser_sync_pro.py` accesses `/home/joe1280/.config/chromium`. When Google authentication expires, cookie extraction from the chromium profile fails because it is redirected to the sign-in page, requiring manual re-authentication via `notebooklm login`.
- **Sudoers Restriction Warning**: Running `/root/google_browser_sync_pro.py` directly under `joe1280` throws `joe1280 is not in the sudoers file` when trying to call `sudo -u joe1280 notebooklm login --browser-cookies chromium`.

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
