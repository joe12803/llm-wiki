# Wiki Log
## [2026-04-28] create | Wiki initialized
- Initialized structure.
- Ingested ds2api and hermes-notebooklm entries.

## 📅 2026-04-29: 工业化采矿体系大一统 (Milestone: Industrial Mining Era)

### 🚀 核心架构升级
- **六位一体流水线**: 正式确立 "勘探-钻探-开采-图谱-入库-同步" 的标准化作业程序 (SOP)。
- **Hermes 钻探工**: Hermes Agent 正式接管核心逻辑钻探职能，实现全链路自主闭环。

### 🛠️ 基建落地成果
- **ds2api v4.1.2**: 成功从官方源切换并完成源码级编译，修正 Nginx 代理错误。
- **NotebookLM 永不掉线**: 升级至 win4r 稳定版，部署 20 分钟心跳任务，实现 Session 自动续期。
- **共享大脑中心**: 在 `/root/hermes-shared/` 建立物理知识库，并为 8 个独立 Agent 完成了软链接挂载，实现知识实时复利。
- **采矿引擎建库**: 在 GitHub 创建了 `autonomous-mining-toolkit` (joe12801)，作为采矿 SOP 和工具的永久中心。
- **图谱化整合**: 接入 `graphify` 引擎，成功对 `chat2api` 及 `ds2api` 进行了初步图谱分析与入库。

### 📤 备份与分发
- **飞书 Wiki 破冰**: 成功完成 `lark-cli` 专家级安装与授权，发布了创世第一篇 "ds2api 架构深度战报"。
- **全量资产备份**: Google Drive (2.5GB 全量) + 飞书/Telegram (灵魂数据精简版) 三路备份达成。

---
*Status: All systems operational. Pipeline is LIVE.*

## [2026-04-29] auto | Daily synchronization triggered
- Automated review of the day's technical milestones.

## 📅 2026-04-30: 工业化开采实战 (Winboat Case Study)

### ⛏️ 自动化开采实战 (Winboat)
- **项目全扫描**: 对 `winboat` 进行了全生命周期开采，从 `driller.py` 钻探到 `graphify` 图谱化分析，识别出 `wa/oa/ta` 三大核心逻辑中枢。
- **NotebookLM 深度融合**: 实现了“源码钻探 -> 知识包生成 -> NotebookLM 自动导入”的半自动链路。
- **多模态产出**: 除了技术报告，首次利用 NotebookLM 生成了项目的 Audio Briefing (40MB MP3)，极大提升了信息吸收效率。

### 🛠️ 基础设施迭代
- **NotebookLM CLI 优化**: 修复了 `notebooklm` 命令行工具中关于 `--output` 和 `--wait` 参数的兼容性问题，目前已能稳定执行自动化音频生成任务。
- **Wiki 自动同步器**: 完善了 `wiki_auto_sync.py` 脚本，支持基于 Session History 的自动增量更新。

---
*Status: All systems operational. 2026-04-30 report finalized.*

## [2026-04-30] auto | Daily synchronization triggered
- Automated review of the day's technical milestones.

## 📅 2026-05-01: 知识复利与多模态扩展 (Knowledge Compounding)

### 🤖 NotebookLM 深度演进
- **多语言支待**: 验证了 NotebookLM 支待 81 种语言的音频生成，成功产出高质量中文 (`zh_Hans`) 播客。
- **CLI 稳定性修复**: 解决了 `notebooklm` 命令行中 `--output` 路径权限与 `--wait` 异步等待的 Bug。
- **Studio 模式接入**: 在 SOP 中新增 “Stage 4: Mining (Studio)” 和 “Stage 5: Storage (Feishu)”，实现从源码到播客/幻灯片的自动化流水线。

### 🛠️ 工具链与协议优化
- **Cookie 转换工程**: 实现了从 Playwright `storage_state.json` 到 Netscape `cookies.txt` 的自动化转换，解决了 `yt-dlp` 在数据中心环境下的鉴权难题。
- **Gemini 策略调整**: 针对官方 API 频发的 `429 RESOURCE_EXHAUSTED` 错误，启动了向 `HanaokaYuzu/Gemini-API` (Web 逆向方案) 的架构迁移。
- **SSE 优化**: 统一了 Nginx 代理层配置，通过 `proxy_buffering off` 和超长超时设置，确保了流式输出的稳定性。

---
*Status: All systems operational. 2026-05-01 report finalized.*

# 工业化采矿报告：Gemini 多账号隔离部署与 API 基础设施升级

**日期**: 2026-05-02
**状态**: ✅ 已完成

## 1. 勘探 (Exploration): 核心逻辑
为了应对 Google 账号的风控并提高并发能力，本项目采用了 **Backend-Bridge 物理隔离架构**。每个账号独占一个 `GeminiWeb2API` 后端（负责 Cookie 会话管理）和一个 `Gemini-Tool-Bridge`（负责 OpenAI 协议转换）。

## 2. 钻探 (Drilling): 技术规格
- **服务器**: 152.70.68.134 / 129.80.98.80 (Nginx 代理层)
- **容器对**: 5 组 (acc1 - acc5)
- **端口映射**: 18789, 18791, 18793, 18795, 18797
- **统一 Token**: `sk-123456`
- **基础设施升级**:
  - `ds2api` 更新至 **v4.3.0**，支持 DeepSeek-V4。
  - `NotebookLM` 切换至 `win4r` 分支，配合 20 分钟一次的 `heartbeat` 保持 Session 活性。

## 3. 图谱 (Mapping): 网络拓扑
```text
[远程 CPA/OneAPI] 
      |
      v
[Nginx: gemini-api.994938.xyz] 
      |-- /acc1/ -> 127.0.0.1:18789
      |-- /acc2/ -> 127.0.0.1:18791
      |-- ...
      v
[Docker: Bridge Container]
      |
      v
[Docker: Backend Container (Cookie 会话)]
```

## 4. 开采 (Mining): 关键交付
- **管理脚本**: `/opt/gemini-agent-docker/manage-gemini.sh` 支持一键 `add` 账号。
- **自定义模型支持**: 实测支持 `gemini-3.1-flash` 和 `gemini-3.1-pro-high` 等伪装模型名。
- **健康检查**: 5 个节点均通过逻辑验证（1+1=2），知识库已更新至 2025 年。

## 5. 入库 (Storage)
- 本报告已追加至 `/root/hermes-shared/wiki/log.md`。
- 相关配置备份至 GitHub: `joe12803/llm-wiki`。

## 6. 同步 (Sync)
- 已通过 `lark-cli` 同步至飞书云文档。

## [2026-05-02] auto | Daily synchronization triggered
- Automated review of the day's technical milestones.

## [2026-05-03] auto | Daily synchronization triggered
- Automated review of the day's technical milestones.


## 📅 2026-05-03: 基础设施闭环与工具集成 (Infrastructure Integration)

### 🤖 API 基础设施升级 (API Bridge & OpenClaw)
- **Claude-API-Bridge 增强**: 为 Claude-API-Bridge 增加了 /v1/models 接口，解决了与 OpenClaw 等编排器的兼容性探测问题。
- **OpenClaw-Zero-Token 集成**: 成功在 Debian 13 (ARM64) 环境下将本地 Claude-API 桥接到 OpenClaw。通过 "Auth Spoofing" 技术将 OpenClaw 的 Anthropic Provider 重定向至本地桥接器 (http://10.0.118.235:8001/v1)，实现了 Web 版 Claude 的工具调用 (Tool-Calling) 能力。
- **Gemini-API Bridge (v2) 修复**: 解决了 Gemini Bridge 在内部调用 geminiweb2api 时缺失 Authorization Header 的 Bug，并优化了账号自动清理逻辑。
- **Docker & 网络优化**: 将 OpenClaw 容器绑定地址从 loopback 扩展至 lan，确保了跨服务通信的稳定性。

### 🛠️ 远程协作与管理 (Claude-Client & Feishu)
- **Claude-Client 部署**: 在 jd184.994938.xyz 服务器成功部署 claude-client，将其作为 /root/hermes-shared/wiki 知识库的远程管理门户。
- **飞书集成**: 完成了 Feishu Bot 的对接 (App ID: cli_a931...)，支持通过飞书直接操作远程 Claude Code CLI，打通了 “移动端对话 -> 远程知识库修改” 的链路。
- **端口管理**: 解决了 Node.js 进程僵死导致的 EADDRINUSE (3000) 错误。

## [2026-05-04] add | GitNexus knowledge ingestion & Deployment
- Extracted core content from YouTube video Zy6tS-7xg9M using NotebookLM.
- Added [[gitnexus]] to Wiki Entities with local deployment details.
- Successfully deployed GitNexus Web and Server on 152.70.68.134 via Docker Compose.
- Automated sync of updated Wiki to Google Drive.

---
*Status: Infrastructure loop CLOSED. Multi-agent collaboration active.*
