# LLM Wiki: Autonomous Mining & Knowledge Graph System

[English](#english) | [中文](#chinese)

---

<a name="chinese"></a>
## 中文：工业化采矿系统 (SOP)

本项目是你的“数字大脑”中枢，通过 AI Agent 驱动的 6 阶段流水线，将 GitHub 源码、YouTube 技术视频和 PDF 文档提纯为永久知识资产。

### 🚀 快速开始 (Quick Start)

#### 1. 勘探 (Exploration) - 快速建立认知
直接喂给 NotebookLM 建立初步理解：
```bash
sudo -u joe1280 notebooklm create "项目名称"
sudo -u joe1280 notebooklm source add <GitHub_URL_or_YT_URL>
```

#### 2. 钻探 (Drilling) - 源码提纯
针对大项目，先在本地进行“脱模”处理：
```bash
# 运行提纯脚本：剔除 node_modules/git，去注释去空行，自动切片
python3 /root/hermes-shared/skills/mining/driller.py /path/to/repo <prefix>
```

#### 3. 深度分析 (Deep Mapping)
在 `152.70.68.134` 部署 GitNexus 进行代码图谱分析：
- **Web UI**: `http://152.70.68.134:4173`
- **索引指令**: `gitnexus analyze /workspace/repo --embeddings`

### 🏗️ 基础设施 (Infrastructure)
- **中枢服务器 (152.70.68.134)**: 运行 GitNexus 容器，处理重型代码分析。
- **本地 Agent**: 负责 NotebookLM 调用、Wiki 笔记生成、rclone 云端同步。
- **存储路径**: `/root/hermes-shared/wiki` (此仓库)。

### 📦 资产同步 (Sync)
- **Obsidian**: 自动同步至 Google Drive `ObsidianVault/llm-wiki`。
- **GitHub**: 实时推送到 `joe12803/llm-wiki` 仓库。

---

<a name="english"></a>
## English: Industrial Mining SOP

### Project Overview
This repository serves as a centralized, multi-modal knowledge base for deep technical mining and architectural analysis of software projects. It leverages AI agents to transform raw source code into structured, navigable knowledge assets.

### Core Stack
- **Knowledge Engine**: [GitNexus](https://github.com/GitNexus/GitNexus) for code graph analysis and "Explosion Radius" impact assessment.
- **Explainability**: [NotebookLM](https://notebooklm.google.com/) for generating multi-modal insights (Audio Briefings, technical summaries).
- **Automation**: Hermes Agent orchestrating a 6-stage industrial mining workflow.
- **Sync**: Multi-path synchronization via `rclone` (Google Drive/Obsidian) and `git` (GitHub).

### 6-Stage Workflow
1. **Explore**: Reconnaissance of technical domains and paper discovery.
2. **Drill**: Source code acquisition, de-slagging, and refined slicing.
3. **Mine**: Deep indexing via GitNexus (Vector & Graph).
4. **Map**: Architectural visualization and impact analysis.
5. **Store**: Structured entry into this LLM Wiki.
6. **Sync**: Universal distribution to cloud storage and remote repositories.

---
*Powered by Hermes Agent & GitNexus*
