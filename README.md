# jujutsu-best-practices

一个面向 **Jujutsu (jj)** 用户的中文技能仓库，聚焦“最佳实践 + 工作流”。
内容基于官方文档整理，并补充了社区资源列表，适合中级用户快速上手与协作。

## 适用场景

- 需要快速整理变更、拆分/合并变更
- 需要理解 change ID 与工作副本模型
- 需要处理冲突或回滚操作
- 需要与 GitHub / Gerrit 协作评审
- 需要配置 jj 的默认行为或多工作区

## 目录结构

- `SKILL.md`：技能入口与执行指南
- `references/best-practices.md`：核心心智模型与操作最佳实践
- `references/bookmarks-and-remotes.md`：书签与远端协作要点
- `references/github-workflows.md`：GitHub/GitLab 协作流程
- `references/gerrit-workflows.md`：Gerrit 工作流与 Change-Id 管理
- `references/config.md`：配置层级与常用配置项
- `references/resources.md`：awesome-jj 资源速览

## 使用方式

当用户询问以下问题时，适合触发该技能：

- “如何把当前改动拆成多个提交？”
- “如何用 jj 更新 PR 评审意见？”
- “Gerrit 下怎么保证 Change-Id 对齐？”
- “jj 的书签和 Git 分支有什么不同？”

## 许可

MIT License
