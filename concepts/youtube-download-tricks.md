---
title: YouTube Download Tricks
created: 2026-04-29
updated: 2026-04-29
type: concept
tags: [yt-dlp, github-actions, bypass, automation]
---

# YouTube Download Tricks

Techniques for bypassing bot detection (n-challenge, IP reputation) when downloading YouTube content to restricted server environments.

## 1. GitHub Actions Bypassing
When data center IPs (OCI, AWS) are blocked, use GitHub's infrastructure:
- **Repo**: `joe12803/baidu-downloader`
- **Workflow**: `baidu_transfer.yml`
- **Mechanism**: Trigger via `gh workflow run` to download to GH runners and upload directly to Baidu Netdisk.

## 2. Cookie Management
- **Format Conversion**: Use scripts to convert Playwright `storage_state.json` to Netscape format for `yt-dlp`.
- **Account Rotation**: Data centers often trigger bans; maintain fresh session cookies from a residential-IP authenticated browser.

## 3. Toolchain Requirements
- **JS Runtime**: `yt-dlp` requires Deno or Node.js to solve the `n-token` challenge locally.
- **BaiduPCS-Go**: Used for final asset management on the target server.

## 4. The "NotebookLM" Bypass
If only text/summary is needed, add the URL directly to [[hermes-notebooklm-integration]]. Google's scrapers are rarely blocked and provide full transcripts instantly.
