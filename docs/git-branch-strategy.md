# Git 分支管理规范

本项目在开发过程中实践了 **创建分支 → 独立开发 → 合并分支 → 解决冲突** 的完整分支管理工作流，规范如下。

## 1. 分支模型

| 分支类型 | 命名规范 | 用途 | 生命周期 |
| -------- | -------- | ---- | -------- |
| 主分支 | `main` | 始终保持稳定、可发布状态 | 永久 |
| 功能分支 | `feature/<主题>` | 开发新笔记、新功能 | 合并后删除 |
| 修复分支 | `hotfix/<问题>` | 紧急修复错误内容 | 合并后删除 |

## 2. 常用操作

### 创建并切换分支

```bash
git checkout -b feature/consensus-notes
```

### 开发完成后的合并

```bash
git checkout main
git merge --no-ff feature/consensus-notes   # 保留合并记录，历史更清晰
git branch -d feature/consensus-notes
```

### 冲突解决

当两个分支修改了同一文件的同一位置时，合并会产生冲突：

```bash
git merge feature/smart-contract-notes
# Auto-merging notes/01-blockchain-overview.md
# CONFLICT (content): Merge conflict in notes/01-blockchain-overview.md
```

处理步骤：

1. 打开冲突文件，定位 `<<<<<<<`、`=======`、`>>>>>>>` 标记；
2. 人工确认保留、修改或融合双方内容，删除冲突标记；
3. `git add <file>` 标记冲突已解决；
4. `git commit` 完成合并提交。

## 3. 提交信息规范

采用 `类型: 描述` 的格式，类型与 [CONTRIBUTING.md](../CONTRIBUTING.md) 一致，如：

```
docs: 添加共识机制学习笔记
fix: 修正区块链概述中的时间线错误
chore: 初始化项目结构
```

## 4. 版本标记

每完成一个阶段性内容集合，在 `main` 分支上打标签：

```bash
git tag -a v1.0.0 -m "首个正式版本：基础概念、共识机制、智能合约、联盟链四大主题"
git push origin v1.0.0
```
