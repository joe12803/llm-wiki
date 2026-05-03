# LLM Wiki: Autonomous Mining & Knowledge Graph System

[English](#english) | [中文](#chinese)

---

<a name="english"></a>
## English

### Project Overview
This repository serves as a centralized, multi-modal knowledge base for deep technical mining and architectural analysis of software projects. It leverages AI agents to transform raw source code into structured, navigable knowledge.

### Core Stack
- **Knowledge Engine**: [GitNexus](https://github.com/GitNexus/GitNexus) for code graph analysis and "Explosion Radius" impact assessment.
- **Explainability**: [NotebookLM](https://notebooklm.google.com/) for generating multi-modal insights (Audio Briefings, technical summaries).
- **Automation**: Hermes Agent orchestrating a 6-stage industrial mining workflow.
- **Sync**: Multi-path synchronization via `rclone` (Google Drive/Obsidian) and `git` (GitHub).

### Workflow
1. **Explore**: Reconnaissance of technical domains and paper discovery.
2. **Drill**: Source code acquisition and preliminary scanning.
3. **Mine**: Deep indexing via GitNexus (Vector & Graph).
4. **Map**: Architectural visualization and impact analysis.
5. **Store**: Structured entry into the LLM Wiki.
6. **Sync**: Universal distribution to cloud storage and remote repositories.

---

<a name="chinese"></a>
## 中文

### 项目简介
本项目是一个工业化的自动化采矿与技术知识图谱系统。通过 AI Agent 驱动，将复杂的源代码库转化为结构化、可导航的知识库，旨在为大型项目提供“上帝视角”和“代码地图”。

### 核心技术栈
- **知识引擎**: [GitNexus](https://github.com/GitNexus/GitNexus) - 负责代码图谱分析、依赖关系提取及“爆炸半径”评估。
- **可解释性**: [NotebookLM](https://notebooklm.google.com/) - 负责多模态知识消费，生成项目音频简报 (Audio Briefing) 和中文深度总结。
- **自动化**: Hermes Agent 编排的 6 阶段工业采矿流水线。
- **同步体系**: 通过 `rclone` (Google Drive/Obsidian) 和 `git` (GitHub) 实现多路径实时同步。

### 采矿工作流 (SOP)
1. **勘探 (Explore)**: 领域调研与论文/技术栈探测。
2. **钻探 (Drill)**: 源码获取与初步扫描。
3. **开采 (Mining)**: GitNexus 深度索引（向量搜索 + 图数据库）。
4. **图谱 (Mapping)**: 架构可视化与变更影响分析（爆炸半径）。
5. **入库 (Storage)**: 结构化笔记入库 (LLM Wiki)。
6. **同步 (Sync)**: 全量资产同步至云端与代码仓库。

---
*Powered by Hermes Agent & GitNexus*
