# Deep Insight Engines

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![uv](https://img.shields.io/badge/uv-package%20manager-DE5FE9?logo=python&logoColor=white)](https://github.com/astral-sh/uv)

> AI 引擎集合 — 面向学习、阅读、代码分析与工程自动化，通过 Claude Code Skill/Command 接口提供结构化上下文洞察。

---

## 引擎总览

| 引擎 | 说明 | 文档 |
|------|------|------|
| `repo-insight` | 代码库深度分析 · AST 解析 · 链路追踪 | [→](engines/repo-insight/README.md) |
| `multi-sense-insight` | PDF 智能提取 · OCR · 结构化 Markdown | [→](engines/multi-sense-insight/pdf-reader/README.md) |
| `insight-stack-blog` | Obsidian 知识库 · 元数据管理 · 双向链接 | [→](engines/insight-stack-blog/README.md) |
| `git-workflow` | 规范提交 · 分支管理 · CHANGELOG | [→](engines/git-workflow/skills/git-workflow/SKILL.md) |

---

## 引擎详情

### `repo-insight` — 代码库深度分析

对目标项目进行 AST 级结构树解析与核心链路追踪，生成结构化架构视图。支持 GitHub URL 或本地目录一键分析。

- **github-source-decoder** — GitHub 仓库在线分析 → [README](engines/repo-insight/github-source-decoder/README.md)
- **repo-insight-skill** — 本地仓库深度扫描 → [README](engines/repo-insight/repo-insight-skill/README.md)

### `multi-sense-insight` — 多模态学习资料处理

自动将 PDF 转为结构化 Markdown：文本型通过 [markitdown](https://github.com/microsoft/markitdown) 提取，扫描型通过 tesseract OCR 兜底。

- **pdf-reader** — PDF 智能提取与结构化 → [README](engines/multi-sense-insight/pdf-reader/README.md)

### `insight-stack-blog` — Obsidian 知识库管理

AI 驱动的笔记整理与智能关联，无需 Obsidian 环境，通用 Markdown 文件均可用。

- **markdown-frontmatter-engine** — 语义生成/更新 frontmatter 属性 → [README](engines/insight-stack-blog/skills/markdown-frontmatter-engine/README.md)
- **obsidian-smart-links** — 笔记/章节/段落三层粒度双向链接 → [SKILL](engines/insight-stack-blog/skills/obsidian-smart-links/SKILL.md)

### `git-workflow` — Git 工作流自动化

Conventional Commits 规范提交、rebase 线性历史、CHANGELOG 自动更新。

- **commit-added** — 智能提交已暂存代码 → [命令](engines/git-workflow/commands/commit-added.md)
- **commit-code** — 规范提交 + CHANGELOG 集成 → [命令](engines/git-workflow/commands/commit-code.md)
- **git-workflow** — 分支管理 / 同步 / push 安全协议 → [SKILL](engines/git-workflow/skills/git-workflow/SKILL.md)

---

## 环境

| 依赖 | 版本 | 说明 |
|------|------|------|
| [Python](https://www.python.org/) | ≥ 3.10 | 运行环境 |
| [uv](https://github.com/astral-sh/uv) | latest | 包管理与虚拟环境 |

---

## 目录结构

```
deep-insight-engines/
├── engines/
│   ├── repo-insight/          # 代码库分析器
│   │   ├── github-source-decoder/
│   │   └── repo-insight-skill/
│   ├── multi-sense-insight/   # 多模态学习资料处理
│   │   └── pdf-reader/
│   ├── insight-stack-blog/    # Obsidian 知识库管理
│   │   ├── skills/
│   │   ├── commands/
│   │   └── test/
│   └── git-workflow/          # Git 工作流自动化
│       ├── commands/
│       └── skills/
├── LICENSE
├── .gitignore
└── README.md
```

---

## 许可证

[MIT](LICENSE) © Deep Insight Engines
