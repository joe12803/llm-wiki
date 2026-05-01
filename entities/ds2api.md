---
title: ds2api
created: 2026-04-28
updated: 2026-04-29
type: entity
tags: [middleware, deepseek, api-bridge, deployed]
---

# ds2api

A high-performance middleware that bridges DeepSeek Web capabilities to OpenAI-compatible APIs.

## Key Updates (2026-04-29)
- **Version Upgrade**: Updated to **v4.1.2**.
- **Deployment Architecture**: 
  - Application Server: `129.154.39.47` (Docker Compose, Port 6011).
  - Proxy Server: `129.80.98.80` (Nginx).
- **Configuration**:
  - Admin Password: `ab87036181`.
  - Model Aliases: Fixed mappings for `gpt-4o` and `gpt-5.5` to `deepseek-v4-flash`.
- **Infrastructure**: Includes pure Go implementation of **DeepSeekHashV1 PoW** solver for high-performance session handling.
- **Proxy Configuration**: Nginx nodes must use `proxy_buffering off;` and `proxy_read_timeout 3600s;` to support stable SSE streaming.

## Integration
Used as a primary backend for [[hermes-notebooklm-integration]] workflows.
