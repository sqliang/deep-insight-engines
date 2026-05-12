# Deep Insight Engines

> A highly structured, polyglot AI engine collection for personal learning, deep reading, repository analysis, and automated engineering workflows.

**Deep Insight Engines** 是一个面向个人学习、深度阅读、代码库解析以及自动化工程流的 AI 引擎集合。通过统一的 Claude Code Skill/Command 接口向上层 LLM 开发流提供高纯度、结构化的上下文洞察。

---

## 🏗️ 核心引擎 (Engines)

| 引擎 | 语言 | 描述 |
|------|------|------|
| **repo-insight** | Python | 深度代码库分析 — AST 级结构树解析与核心链路追踪 |
| **multi-sense-insight** | Python | 多模态学习资料处理 — PDF 转结构化 Markdown 与 OCR 兜底 |
| **insight-stack-blog** | Python | Obsidian 知识库管理 — 笔记元数据语义生成与智能双向链接 |
| **git-workflow** | — | Git 工作流自动化 — 规范提交、分支管理、CHANGELOG 集成 |

### repo-insight

深度代码库分析引擎。支持 GitHub URL 或本地目录的一键分析，生成项目概述、架构分析、核心模块解读，自动翻译 README 并生成中文代码注释。

包含两个技能：
- **github-source-decoder** — GitHub 仓库在线分析
- **repo-insight-skill** — 本地仓库深度扫描

### multi-sense-insight

多模态学习资料综合处理引擎。自动将 PDF 文件转为结构化 Markdown — 文本型通过 markitdown 提取，图片/扫描型通过 tesseract OCR 兜底，配合 Claude 生成带 YAML frontmatter 的结构化总结。

包含技能：
- **pdf-reader** — PDF 智能提取与结构化

### insight-stack-blog

Obsidian 笔记知识库管理引擎。通过 Claude Code AI 能力实现笔记的自动化整理与智能关联。

包含技能和命令：
- **markdown-frontmatter-engine** — 批量语义生成/更新 Markdown frontmatter 属性
- **obsidian-smart-links** — 三层粒度（笔记/章节/段落）双向链接构建
- 3 个 slash commands — 链接状态查看、搜索、上下文分析

### git-workflow

Git 工作流自动化引擎。管理全周期 Git 操作，包括分支管理、Conventional Commits 规范提交、线性历史同步、CHANGELOG 更新集成。

包含命令：
- **commit-added** — 智能提交已暂存代码
- **commit-code** — 符合 Conventional Commits 规范的提交与 CHANGELOG 更新

---

## 🛠️ 技术栈 (Tech Stack)

* **Python 生态**: [uv](https://github.com/astral-sh/uv) (极速包管理与虚拟环境), Pytest, Ruff

### 前置依赖

* [Python](https://www.python.org/) (>= 3.10)
* [uv](https://github.com/astral-sh/uv) (Python 极速包管理器)

---

## 📂 目录架构 (Architecture)

```shell
deep-insight-engines/
├── engines/
│   ├── repo-insight/              # [Python] 代码库分析器
│   │   ├── github-source-decoder/ # GitHub 仓库在线分析
│   │   └── repo-insight-skill/    # 本地仓库深度扫描
│   ├── multi-sense-insight/       # [Python] 多模态学习资料处理
│   │   └── pdf-reader/            # PDF 智能提取与 OCR
│   ├── insight-stack-blog/        # [Python] Obsidian 知识库管理
│   │   ├── skills/                # 笔记元数据引擎 + 智能链接
│   │   ├── commands/              # Obsidian 专用 slash commands
│   │   └── test/                  # 测试用例
│   └── git-workflow/              # Git 工作流自动化
│       ├── commands/              # commit-added, commit-code
│       └── skills/                # Git 全周期工作流
└── .gitignore
```

---

## 📜 许可证 (License)

[MIT](LICENSE) © Deep Insight Engines
