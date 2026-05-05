     1|---
     2|title: ds2api
     3|created: 2026-04-28
     4|updated: 2026-05-05
     5|type: entity
     6|tags: [middleware, deepseek, api-bridge, deployed, gemini-thinking]
     7|---
     8|
     9|# ds2api
    10|
    11|A high-performance middleware that bridges DeepSeek Web capabilities to OpenAI-compatible APIs.
    12|
    13|## Key Updates (2026-05-04)
    14|- **Version Upgrade**: Updated to **v4.4.2**.
    15|- **Gemini Thinking**: Added support for Gemini reasoning chains (Thinking model).
    16|- **Streaming Optimization**: Improved SSE stream processing for better stability with downstream orchestrators.
    17|- **Deployment Architecture**: 
    18|  - Application Server: `129.154.39.47` (Docker Compose, Port 6011).
    19|  - Proxy Server: `129.80.98.80` (Nginx).
    20|- **Configuration**:
    21|  - Admin Password: `ab87036181`.
    22|  - Model Aliases: Fixed mappings for `gpt-4o` and `gpt-5.5` to `deepseek-v4-flash`.
    23|- **Infrastructure**: Includes pure Go implementation of **DeepSeekHashV1 PoW** solver for high-performance session handling.
    24|- **Proxy Configuration**: Nginx nodes must use `proxy_buffering off;` and `proxy_read_timeout 3600s;` to support stable SSE streaming.
    25|
    26|## Integration
    27|Used as a primary backend for [[hermes-notebooklm-integration]] workflows.
    28|
## Maintenance (2026-05-05)
- **Version Upgrade**: Updated to **v4.4.2** on server `129.80.98.80`.
- **Cleanup**: Deprecated `compat` key removed from `config.json`.
