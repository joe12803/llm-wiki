# ds2api

DeepSeek-to-OpenAI API bridge middleware. Implements highly optimized middleware routing, dynamic server-side load balancing, and non-root Docker execution profiles.

---

## 🛠️ Architecture & Core Components

- **Upstream Connection**: Converts DeepSeek API models into standardized OpenAI format structures.
- **Port Assignment**:
  - Target server running on Port `6011` (e.g. `ds.994938.xyz`) or deployed across heterogeneous server clusters.
- **SSE Buffering**: To enable reliable streaming for long-context outputs, Nginx proxy nodes routing `ds2api` traffic must configure:
  ```nginx
  proxy_buffering off;
  proxy_read_timeout 3600s;
  ```

---

## 📅 Deployment & Update History

### [2026-05-13] Version 4.6.2-beta Upgrade & SSE Buffer Tuning
- **Version**: Upgraded to **v4.6.2-beta** on remote OCI nodes (`129.80.98.80`).
- **SSE Buffer Optimization**: Optimized the internal Server-Sent Events (SSE) output buffer to prevent connection drops during massive context windows.
- **UID/GID Consistency**: Verified that the user mapping consistency of UID/GID `999:999` is preserved across all worker nodes to prevent permissions conflicts when the image mounts local configuration directories.

### [2026-05-10] Version 4.6.1 & Permission Lockdown
- **Version Upgrade**: Updated to **v4.6.1** on server `129.80.98.80`.
- **Security & Compatibility**: Implemented non-root user compatibility for Docker. Changed `config.json` ownership to `999:999` and permissions to `644` to resolve persistent 401 unauthorized errors in newer image versions.
- **Deployment**: Switched to `ghcr.io/cjackhwang/ds2api:latest` with automated `docker compose` refresh.

### [2026-05-08] Version 4.4.5 & ARM64 Support
- **Version**: Updated to **v4.4.5**.
- **ARM64 Support**: Streamlined build process for heterogeneous clusters (OCI ARM + jd184).
- **Load Balancing**: Enhanced account rotation logic in the bridge layer to prevent rate limiting across multiple Gemini accounts.

---
*Back to [Index](../index.md) or [Main README](../README.md).*
