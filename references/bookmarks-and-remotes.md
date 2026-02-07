# 书签的定位与语义

- 书签是“可移动的命名指针”，类似 Git 分支；重写历史后书签会移动到新的变更上。
- 没有“当前书签”的概念；通过 revset 或 `@`/`@-` 来定位当前工作副本和其父变更。

# 常用书签操作

- 列出书签：`jj bookmark list`
- 创建书签：`jj bookmark create <name> -r <rev>`
- 移动书签：`jj bookmark move <name> -r <rev>`
- 删除书签：`jj bookmark delete <name>`
- 重命名书签：`jj bookmark rename <old> <new>`

# 远端书签与跟踪

- 远端书签用 `<bookmark>@<remote>` 形式引用。
- 通过 `jj bookmark track <bookmark>@<remote>` 跟踪远端书签。
- 查看跟踪状态：`jj bookmark list --tracked`。
- 可用配置 `remotes.<name>.auto-track-bookmarks` 批量自动跟踪远端书签。

# 获取与推送

- 获取远端更新：`jj git fetch`。
- 推送书签到远端：`jj git push --bookmark <name>` 或 `jj git push --change <rev>`。
- 推送时包含安全检查，行为类似“force-with-lease”，避免意外覆盖远端更新。

# 书签冲突

- 远端更新与本地重写导致书签冲突时，优先用 `jj log` 找到目标变更，再用 `jj bookmark move` 解决。
- 需要保留双方历史时，用 `jj new` 形成分叉，再用 `jj rebase` 或 `jj merge` 进行整理。
