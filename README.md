# Deep Insight Engines

> A highly structured, polyglot AI engine collection for personal learning, deep reading, repository analysis, and automated engineering workflows.

**Deep Insight Engines** 是一个面向个人学习、深度阅读、代码库解析以及自动化工程流的 AI 引擎集合。本项目采用“胖网关，瘦引擎”的微内核架构，深度融合 Node.js 与 Python 生态，旨在通过统一的接口（如 MCP 协议）向上层业务和 LLM 开发流提供高纯度、结构化的上下文洞察。

---

## 🏗️ 核心引擎 (Engines)

本仓库包含以下独立运行但可协同工作的 AI 引擎：

* **`@deep-insight-engines/repo-insight`** [Python]
    深度代码库分析引擎。能够对目标开源项目进行 AST 级别的结构树解析与核心链路追踪，为理解庞大的源码架构提供结构化视图。
* **`@deep-insight-engines/multi-sense-insight`** [Python]
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

前置依赖
* [Node.js](https://www.google.com/search?q=https://nodejs.org/) (>= 18)
* [pnpm](https://www.google.com/search?q=https://pnpm.io/installation) (>= 8)
* [Python](https://www.google.com/search?q=https://www.python.org/) (>= 3.10)
* [uv](https://www.google.com/url?sa=E&source=gmail&q=https://github.com/astral-sh/uv) (Python 极速包管理器)

---

## 📂 目录架构 (Architecture)

```shell
deep-insight-engines/
├── engines/                   # 独立 AI 引擎
│   ├── repo-insight/          # [Python] 代码库分析器
│   ├── multi-sense-insight/    # [Python] 多模态学习资料综合处理与洞察
```

---

## 📜 许可证 (License)

[MIT](https://www.google.com/search?q=./LICENSE) © Deep Insight Engines
