---
name: commit-code
description: 生成符合 Conventional Commits 规范的 commit message，可选更新 CHANGELOG.md
argument-hint: [可选的 commit message 摘要]
---

> **前提**: 必须先用 `git add` 暂存文件。此命令只处理已暂存的文件。

## Commit 类型速查

| 类型 | 写入 CHANGELOG | 说明 |
|------|----------------|------|
| `feat:` | ✅ | 新功能 |
| `fix:` | ✅ | Bug 修复 |
| `perf:` | ✅ | 性能优化 |
| `security:` | ✅ | 安全修复 |
| `deprecate:` | ✅ | 弃用通知 |
| `breaking:` | ✅ | 破坏性变更 |
| `docs:` | ⚪ 跳过 | 文档更新 |
| `refactor:` | ❌ 跳过 | 代码重构 |
| `style:` | ❌ 跳过 | 格式调整 |
| `test:` | ❌ 跳过 | 测试文件 |
| `chore:` | ❌ 跳过 | 构建/工具 |

## 工作流程

1. **分析暂存**: `git status && git diff --staged`，判断是否跳过 CHANGELOG
2. **分类变更**: 确定 commit 类型和 scope
3. **生成 message**: `{type}{scope}: {简短描述}`，使用祈使语气
4. **更新 CHANGELOG**: 若需记录，在 `## [Unreleased]` 对应 section 顶部添加**中文条目**（见下方格式）
5. **确认并提交**: 展示 message 和 CHANGELOG diff，用户确认后执行

## CHANGELOG 条目格式

条目必须为**中文**，简洁描述"做了什么"：

```markdown
### Added
- 新增批量添加笔记元数据的脚本
- 新增笔记双向链接分析命令

### Fixed
- 修复块 ID 生成不稳定的问题
```

**格式规则:**
- 放在对应 section 顶部（最新在前）
- 格式：`- {中文描述}`（不加括号，不写 commit hash）
- 描述应简洁（<50字），说"做什么"而非"怎么做"
- 不要在条目中写 feat/fix 等英文类型

## 示例

```
feat(markdown-frontmatter-engine): add batch frontmatter script
→ CHANGELOG: - 新增批量添加笔记元数据的脚本

fix(obsidian-smart-links): correct block-id generation
→ CHANGELOG: - 修复块 ID 生成不稳定的问题

chore: update dependencies
→ 不写入 CHANGELOG

docs: update README
→ 不写入 CHANGELOG
```

## 规则

- 只提交已暂存的文件，不自动添加未暂存文件
- CHANGELOG 更新后需单独 `git add CHANGELOG.md`
- 多文件变更可有多条 CHANGELOG 条目
- 破坏性变更在 footer 添加 `BREAKING CHANGE: {说明}`
- 消息摘要不超过 72 字符
