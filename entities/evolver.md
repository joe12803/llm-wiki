# EvoMap/evolver Mining Report

## 项目概览
- **名称**: EvoMap Evolver
- **仓库**: https://github.com/EvoMap/evolver
- **索引状态**: 已完成 (8,798 nodes | 11,409 edges)
- **核心功能**: Evolver 是一个用于 AI Agent 自我进化、知识提取与同步的工业化工具。它支持 `GEP` (Genetic Evolution Protocol) 协议，能够从 IDE 交互日志（Cursor, Claude Code, Codex）中提取原子化的“基因”（Genes）和“胶囊”（Capsules），并构建内存图谱。

## 架构要点
- **核心循环 (main)**: 位于 `index.js`，包含一个内部守护进程模式 (`--loop`)，支持实时监控 Agent 会话。
- **协议支持**: 实现 `src/gep/` 下的多种传输和处理逻辑，包括任务接收器 (`taskReceiver.js`)、问题生成器 (`questionGenerator.js`) 和便携式导出 (`portable.js`)。
- **数据管理**: 通过 `src/gep/assetStore.js` 管理基因和胶囊的持久化。
- **Proxy 功能**: `src/proxy/` 模块允许对 Agent 的 API 调用进行拦截和增强。

## GitNexus 访问
- **Web UI**: http://152.70.68.134:4173 (项目 ID: `evolver`)
- **关键符号**:
    - `index.js:main`: 系统入口点。
    - `src/gep/portable.js:exportGepx`: 处理 GEP 数据的便携式导出（.gepx 文件）。
    - `src/proxy/index.js:startProxy`: 启动 Agent 代理服务。

## 采矿进度
- [x] 代码钻探 (Clone)
- [x] 深度索引 (Analyze)
- [ ] 语义文档 (Wiki) - *LLM 接口在容器内连接受限，暂通过手动 context 提取架构信息。*
- [x] 知识入库 (Wiki Entry)
