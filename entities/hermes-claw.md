---
title: hermes-claw
created: 2026-05-05
updated: 2026-05-05
type: entity
tags: [hermes-agent, github-actions, persistence, deployment]
---

# hermes-claw

A specialized deployment of Hermes Agent running on GitHub Actions, designed for high-availability memory persistence.

## Key Features
- **Persistence Strategy**: Automatically pushes `.hermes-data` (sessions, memory, skills) back to the repository every 10 minutes to bypass the 6-hour runtime limit of GitHub Actions.
- **WebUI Access**: Exposes the Hermes WebUI (Port 8787) via Cloudflare Quick Tunnel (`trycloudflare.com`).
- **Messaging Integration**: Native support for Feishu and Telegram bots.

## Troubleshooting (2026-05-05)
- **Environment**: Upgraded to **Python 3.11** to meet `hermes-agent` requirements.
- **Dependency Fix**: Installed `hermes-agent` in editable mode (`pip install -e .`) and explicitly set `PYTHONPATH` to resolve "AIAgent not available" errors.
- **Secret Handling**: Improved YAML logic to correctly detect and enable messaging platforms based on GitHub Secrets.
