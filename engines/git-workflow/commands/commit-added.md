---
name: commit-added
description: 智能提交已 git add 的代码，自动生成与修改相关的 commit message
---

请帮我提交当前已经 git add 的代码。执行以下步骤：

1. 首先检查 git 状态，确认哪些文件已经被 staged（git add 过）
2. 查看这些 staged 文件的具体修改内容（`git diff --cached`）
3. 根据修改内容，遵循项目的 commit 格式规范生成合适的 commit message
   - 格式：`type(scope): description`
   - type 可选：feat, fix, docs, style, refactor, test, chore, perf, ci, build 等
   - scope 是修改的范围（如文件名、模块名等）
4. 在生成的 commit message 尾部添加一行：`Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>`
5. 使用完整的 commit message（包含 Co-Authored-By 行）执行 git commit
6. 提交完成后，告诉用户提交成功，并显示 commit 信息

注意：
- 只提交已经 git add 的文件，不要处理未 staging 的文件，也不要提交未修改的文件。
- 若无修改文件，提示用户没有修改，不执行提交。
- Co-Authored-By 行必须添加在 commit message 的最后，且前面有一个空行。

$ARGUMENTS
