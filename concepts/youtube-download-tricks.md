     1|---
     2|title: YouTube Download Tricks
     3|created: 2026-04-29
     4|updated: 2026-05-05
     5|type: concept
     6|tags: [yt-dlp, github-actions, bypass, automation]
     7|---
     8|
     9|# YouTube Download Tricks
    10|
    11|Techniques for bypassing bot detection (n-challenge, IP reputation) when downloading YouTube content to restricted server environments.
    12|
    13|## 1. GitHub Actions Bypassing
    14|When data center IPs (OCI, AWS) are blocked, use GitHub's infrastructure:
    15|- **Repo**: `joe12803/baidu-downloader`
    16|- **Workflow**: `baidu_transfer.yml`
    17|- **Mechanism**: Trigger via `gh workflow run` to download to GH runners and upload directly to Baidu Netdisk.
    18|
    19|## 2. Cookie Management
    20|- **Format Conversion**: Automated Python script converts Playwright `storage_state.json` (used by [[hermes-notebooklm-integration]]) to Netscape format required by `yt-dlp`.
    21|- **Account Rotation**: Data centers often trigger bans; maintain fresh session cookies from a residential-IP authenticated browser.
    22|
    23|## 3. Toolchain Requirements
    24|- **JS Runtime**: `yt-dlp` requires Deno or Node.js to solve the `n-token` challenge locally.
    25|- **BaiduPCS-Go**: Used for final asset management on the target server.
    26|
    27|## 4. The "NotebookLM" Bypass
    28|If only text/summary is needed, add the URL directly to [[hermes-notebooklm-integration]]. Google's scrapers are rarely blocked and provide full transcripts instantly.
    29|
## 5. GitHub Actions IP Fencing (2026-05-05)
- **Finding**: YouTube effectively blocks Data Center IPs (like GitHub Actions runners) regardless of cookie usage if the account's usual geographic location doesn't match the runner's region. 
- **Outcome**: `yt-dlp` consistently triggers "Sign in to confirm you’re not a bot" on GitHub runners even with valid Netscape cookies.
