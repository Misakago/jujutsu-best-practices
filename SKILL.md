---
name: jujutsu-best-practices
description: 提供 Jujutsu(jj) 的最佳实践与工作流指导。用于规划/整理变更、理解 change ID 与工作副本模型、使用 revset 与日志、处理冲突与回滚、书签与远端协作、GitHub/Gerrit 评审流程、配置与多工作区管理。
---

# Jujutsu Best Practices

## 快速开始

- 先判断用户目标：本地变更管理、协作推送、冲突处理、回滚恢复或配置优化。
- 优先读取 `references/best-practices.md` 获得核心心智模型与常见操作模式。
- 涉及书签/远端时，读取 `references/bookmarks-and-remotes.md`。
- 涉及 GitHub/GitLab 时，读取 `references/github-workflows.md`。
- 涉及 Gerrit 时，读取 `references/gerrit-workflows.md`。
- 涉及配置与默认行为时，读取 `references/config.md`。
- 需要更多学习资源时，读取 `references/resources.md`。

## 决策问题

- 需要协作的代码评审平台是 GitHub/GitLab 还是 Gerrit？
- 是否使用 Git 共存（colocated）仓库？
- 是否需要用书签追踪远端分支、多人协作书签或多远端？
- 是否需要回滚操作或排查“历史为何变成这样”？
- 是否希望保持“干净提交”还是“追加提交”以回应评审？

## 最佳实践输出要求

- 用简洁步骤 + 命令片段回答，先给最短可行路径，再给可选项。
- 明确 `@`（工作副本变更）与 `@-`（上一个变更）的差别。
- 优先使用 change ID（稳定）而不是 commit ID（会变）。
- 避免一次性输出大量命令；按用户场景分段。

## 协作与推送

- GitHub/GitLab：按“生成书签”或“命名书签”两条路径给出步骤，并说明更新评审的两种策略（追加提交 vs 重写提交）。
- Gerrit：强调 `jj gerrit upload` 以 change ID 建立映射，提醒 Change-Id 管理注意事项。

## 配置

- 优先用 `jj config edit --user|--repo|--workspace` 解释配置层级。
- 对“默认远端、自动追踪书签、快照自动追踪路径”等需求给出配置方向。

## 资源与扩展阅读

- 仅在用户明确要求更多学习资源时引用 `references/resources.md`。
