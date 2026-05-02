---
title: Claude-API Bridge
created: 2026-05-02
updated: 2026-05-02
type: entity
tags: [middleware, claude, api-bridge, deployed, automation]
---

# Claude-API Bridge

A customized FastAPI-based middleware that transforms the Claude Web API into an OpenAI-compatible service.

## Project Information
- **Source Repository**: `https://github.com/cyber-wojtek/Claude-API`
- **Customized Version**: `https://github.com/joe12803/Claude-API-Bridge`
- **Deployment Path**: `/home/joe1280/Claude-API`

## Key Technical Features (2026-05-02)
- **OpenAI Compatibility**: Provides `/v1/chat/completions` endpoint.
- **Account Pooling**: Supports multiple `sessionKey` and `org_id` pairs with round-robin rotation.
- **Auto-Healing**: Automatically detects failed or expired accounts (403/AuthenticationError) and removes them from the active pool, updating `accounts.json` on disk.
- **Dynamic Reloading**: `/reload` endpoint allows refreshing the account pool without service downtime.
- **Service Management**: Managed via `systemd` (`claude-api.service`) on port **8001**.

## Deployment Details
- **Environment**: Python virtual environment with `fastapi`, `uvicorn`, and `claude-webapi`.
- **Model Mapping**: Verified compatibility with `claude-sonnet-4-6`.
- **Port**: 8001 (Port 8000 was occupied by Docker).

## Configuration
- **Accounts File**: `/home/joe1280/Claude-API/accounts.json`
- **Service Control**: `sudo systemctl restart claude-api`
- **Logs**: `journalctl -u claude-api -f`
