# YouTube Download Tricks & Bypass Strategies

This concept maps our strategies for bypassing YouTube's strict bot detection and IP bans affecting data center and cloud IP ranges.

---

## 🛠️ Key Techniques & Workarounds

### 1. The NotebookLM Proxy
When cloud IPs (OCI, AWS, etc.) are blocked and standard `yt-dlp` calls return `Sign in to confirm you’re not a bot`, the absolute best workaround is the **NotebookLM Proxy**:
1. Create a temporary notebook via `notebooklm create`.
2. Add the target YouTube video URL as a source via `notebooklm source add --type youtube`.
3. Query the video contents via `notebooklm ask`.
4. Output the extracted transcript and structured summaries directly into the local wiki.

### 2. GitHub Actions Offline Downloader
Since GitHub Actions runners have higher reputation IP addresses, we route heavy downloads through a dedicated repository (`joe12803/baidu-downloader`):
- **Spoofing User-Agent**: Configures `BaiduPCS-Go` to use an Android mobile User-Agent (`netdisk;11.12.3;android-android;11`) and AppID `266719` to bypass Baidu's strict upload/download block parameters (avoiding Code 31023).
- **Playwright Cookie Conversions**: Run custom Playwright routines to load an active authenticated session (`storage_state.json`), capture stream resources, or dump fresh Google cookies into the Netscape format expected by `yt-dlp`.

---

## 📅 Chronological Updates

### [2026-05-24] Heartbeat & Download Steady-State
- **Steady-State Operations**: Verified that both the OCI nodes (`129.80.98.80`) and the GitHub Actions offline downloader remain stable.
- **Baidu Netdisk Verification**: Handled periodic session refreshes for `BaiduPCS-Go` to prevent login expirations (Code 31045) during large file transfers.

### [2026-05-09] Cookie Conversion Refinements
- **Netscape Formatting**: Refined the Playwright-to-Netscape cookie converter Python script to ensure that the second column (domain matching flag) is formatted correctly, resolving `AssertionError` crashes during local `yt-dlp` calls.
- **Credential Rotation**: Configured automatic secret syncing to ensure that fresh browser cookies are distributed to remote download runners without requiring manual workflow edits.

---
*Back to [Index](../index.md) or [Main README](../README.md).*
