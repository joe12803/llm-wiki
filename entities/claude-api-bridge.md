---
title: Claude-API Bridge
created: 2026-05-02
updated: 2026-05-04
type: entity
tags: [middleware, claude, api-bridge, deployed, automation, tool-calling, hybrid-parser]
---

# Claude-API Bridge

A customized FastAPI-based middleware that transforms the Claude Web API into an OpenAI-compatible service.

## Key Technical Features (2026-05-04)
- **Hybrid Tool Parser**: Introduced `tool_parser.py` to handle Claude's diverse tool-call formats (XML tags, Markdown JSON, KV).
- **Native Streaming**: Implemented true async streaming (`generate_content_stream`) for better UI responsiveness.
- **System Prompt Tuning**: Revised internal system instructions to bypass "As an AI..." tool-use refusals.
- **OpenAI Compatibility**: Full `/v1/chat/completions` and `/v1/models` support.

## Deployment Details
- **Environment**: Debian 13 (ARM64), Python venv.
- **Port**: 8001.
- **Service Control**: `sudo systemctl restart claude-api`

## Deployment Details
- **Environment**: Python virtual environment with `fastapi`, `uvicorn`, and `claude-webapi`.
- **Model Mapping**: Verified compatibility with `claude-sonnet-4-6`.
- **Port**: 8001 (Port 8000 was occupied by Docker).

## Configuration
- **Accounts File**: `/home/joe1280/Claude-API/accounts.json`
- **Service Control**: `sudo systemctl restart claude-api`
- **Logs**: `journalctl -u claude-api -f`
