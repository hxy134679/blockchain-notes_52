# 贡献指南（CONTRIBUTING）

感谢你关注并参与 **blockchain-notes_52** 项目！请按照以下流程参与贡献。

## 1. 贡献方式

- **提交 Issue**：发现内容错误、过时表述或希望补充新主题，请先提交 Issue 讨论；
- **提交 Pull Request**：针对已达成共识的 Issue 进行修改并提交 PR。

## 2. Issue 规范

本项目内置了两类 Issue 模板：

| 模板 | 用途 |
| ---- | ---- |
| `bug-report` | 笔记内容勘误：描述错误位置、错误内容与建议修改 |
| `note-suggestion` | 新主题建议：描述希望增加的知识点及理由 |

## 3. Pull Request 流程

1. Fork 本仓库或从 `main` 分支拉出功能分支：

```bash
git checkout -b feature/your-topic
```

2. 提交修改，Commit Message 使用中文，格式为 `类型: 简述`，类型包括：
   - `docs`：文档/笔记变更
   - `fix`：内容纠错
   - `chore`：工程配置类变更
3. 推送分支并发起 PR，PR 描述中关联对应 Issue（如 `Closes #1`）；
4. 等待项目维护者 Review，通过后合并入 `main` 分支。

## 4. 分支规范

本项目采用简化的 Git Flow 模型，详细规范见 [docs/git-branch-strategy.md](./docs/git-branch-strategy.md)：

- `main`：稳定分支，始终保持可发布状态；
- `feature/*`：新内容/新功能分支；
- `hotfix/*`：紧急修复分支。

## 5. 内容写作约定

- Markdown 语法书写，一级标题为笔记题目；
- 涉及专业术语时，首次出现给出中英文对照；
- 引用外部资料请在文末注明来源。
