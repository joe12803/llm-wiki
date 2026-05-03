---
name: gitnexus-mining-workflow
description: GitNexus 2.0 Mining Workflow - 结合代码图谱能力的工业化采矿流
category: research
tags: [mining, gitnexus, knowledge-base, automation]
---

# GitNexus 2.0 Mining Workflow

这是一个结合 GitNexus 代码图谱能力的工业化采矿工作流。它将源码的深度静态分析与本地知识库（LLM Wiki）完美融合，实现从“下载代码”到“全量架构图谱入库”的自动化。

## 触发条件
- 需要对一个新的开源项目或代码库进行深度分析、学习并入库。
- 用户提供了 GitHub 仓库链接或本地代码路径。

## 准备工作 (Pre-requisites)
- 部署机器：152.70.68.134
- 部署目录：`/root/GitNexus`
- Docker 容器：`gitnexus-server` 已启动且 `/workspace` 目录已映射为读写模式。

## 执行步骤 (Step-by-Step)

### 1. 钻探 (Drilling) - 代码获取
将代码克隆到宿主机的工作区：
```bash
git clone --depth 1 <REPO_URL> /root/GitNexus/workspace/<PROJECT_NAME>
```

### 2. 开采 (Mining) - 深度索引
进入部署目录并执行容器内分析：
```bash
cd /root/GitNexus
# 修复权限（如果需要）
docker compose exec -u root gitnexus-server chown -R node:node /workspace/<PROJECT_NAME>
# 执行分析（开启语义向量）
docker compose exec gitnexus-server gitnexus analyze /workspace/<PROJECT_NAME> --embeddings --name <ALIAS> --force
```

### 3. 图谱 (Mapping) - 生成笔记
利用 GitNexus 的 Wiki 功能初步生成项目文档：
```bash
docker compose exec gitnexus-server gitnexus wiki /workspace/<PROJECT_NAME>
```

### 3.5 语义讲解 (Explainability) - NotebookLM 联动 (可选)
将 GitNexus 提取的结构化信息（如 `SKILL.md` 或 `processes` 列表）喂给 NotebookLM，生成播客或架构详解：
1. **导出素材**：将 GitNexus 生成的 Wiki 或导出的 `processes` 信息作为 NotebookLM 的 Source。
2. **生成语音/摘要**：调用 `notebooklm` 技能生成中文 `Audio Briefing`，帮助从宏观理解项目设计意图。

### 4. 入库 (Storage) - 知识库整合
将生成的分析结果整理并写入本地 Wiki：
- 路径：`/root/hermes-shared/wiki/entities/<PROJECT_NAME>.md`
- 记录核心架构、关键调用链和 Web UI 访问链接。

### 5. 同步 (Sync) - 云端与代码仓库同步
执行全量同步，确保多端可用：
1. **Google Drive**: `rclone sync /root/hermes-shared/wiki gdrive:ObsidianVault/llm-wiki --verbose` (用于 Obsidian 挂载)。
2. **GitHub**: 在 `/root/hermes-shared/wiki` 执行 `git add . && git commit -m "mining: <PROJECT_NAME> archive" && git push` (用于版本管理与远程备份)。

## 验证
- 访问 `http://152.70.68.134:4173` 确认项目出现在列表中。
- 检查 GitHub 仓库确认笔记与资源（如音频）已入库。

- **环境重置**：若容器重启，可能需要重新安装全局 `gitnexus` CLI。

## 验证
- 访问 `http://152.70.68.134:4173` 确认项目出现在列表中。
