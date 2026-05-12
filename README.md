# Deep Insight Engines

> A highly structured, polyglot AI engine collection for personal learning, deep reading, repository analysis, and automated engineering workflows.

**Deep Insight Engines** 是一个面向个人学习、深度阅读、代码库解析以及自动化工程流的 AI 引擎集合。本项目采用“胖网关，瘦引擎”的微内核架构，深度融合 Node.js 与 Python 生态，旨在通过统一的接口（如 MCP 协议）向上层业务和 LLM 开发流提供高纯度、结构化的上下文洞察。

---

## 🏗️ 核心引擎 (Engines)

本仓库包含以下独立运行但可协同工作的 AI 引擎：

* **`@deep-insight-engines/repo-insight`** [Python]
    深度代码库分析引擎。能够对目标开源项目进行 AST 级别的结构树解析与核心链路追踪，为理解庞大的源码架构提供结构化视图。
* **`@deep-insight-engines/multi-sense-insight`** [TypeScript]
    多模态学习资料综合处理与洞察引擎。专门针对长篇学术论文、PPT 及重型 PDF 资料，不仅提取源文本，更通过语义理解输出高度结构化的 Markdown 笔记及初步洞察报告。

*未来规划场景 (Roadmap):*
* **SDD Engine**: 基于 Specification-Driven Development (规范驱动开发) 的意图解析与脚手架生成器。
* **D2C Parser**: 提取设计图底层语义，为生产级前端代码生成提供高质上下文的提炼工具。

---

## 🛠️ 技术栈 (Tech Stack)

本项目是一个混合语言的 Monorepo (Polyglot Monorepo)，通过业界标准的工具链保障工程化体验：

* **工作区编排**: [pnpm workspaces](https://pnpm.io/) + [Turborepo](https://turbo.build/)
* **TypeScript 生态**: Node.js, TypeScript, Vite/Vitest
* **Python 生态**: [uv](https://github.com/astral-sh/uv) (极速包管理与虚拟环境), Pytest, Ruff

---

## 📂 目录架构 (Architecture)

```shell
deep-insight-engines/
├── packages/                  # 共享基础库
│   ├── ts-core/               # Node.js 共享逻辑 (MCP, Logger, Utils)
│   ├── py-core/               # Python 共享逻辑 (LLM Client, Prompts)
│   └── eslint-config/         # 代码规范配置
├── engines/                   # 独立 AI 引擎
│   ├── repo-insight/          # [Python] 代码库分析器
│   ├── doc-distiller/         # [TS] PDF 与知识提炼器
│   └── mcp-gateway/           # [TS] 标准 MCP 网关入口
├── package.json               # 顶层 pnpm 依赖与脚本
├── turbo.json                 # Turborepo 任务编排配置
└── Makefile                   # 跨语言的一键启动脚本
```
---

## 🚀 快速开始 (Getting Started)

### 前置依赖

* [Node.js](https://www.google.com/search?q=https://nodejs.org/) (>= 18)
* [pnpm](https://www.google.com/search?q=https://pnpm.io/installation) (>= 8)
* [Python](https://www.google.com/search?q=https://www.python.org/) (>= 3.10)
* [uv](https://www.google.com/url?sa=E&source=gmail&q=https://github.com/astral-sh/uv) (Python 极速包管理器)

### 1. 初始化项目

克隆仓库后，在根目录运行一次 `Makefile` 提供的安装命令，即可同时完成 Node.js 和 Python 的依赖安装与环境初始化：

```bash
make setup

```

### 2. 环境配置

复制全局环境变量文件并填入你的 API Key：

```bash
cp .env.example .env

```

### 3. 开发与调试

通过 Turborepo 或 Makefile 一键启动所有服务的开发模式，或针对单一引擎进行调试：

```bash
# 启动所有引擎的开发模式
pnpm dev

# 仅调试代码库洞察引擎 (Python)
make dev-repo

# 仅调试文档蒸馏引擎 (TypeScript)
make dev-doc

```

---

## 📜 许可证 (License)

[MIT](https://www.google.com/search?q=./LICENSE) © Deep Insight Engines
