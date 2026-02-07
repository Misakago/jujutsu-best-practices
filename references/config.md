# 配置层级与编辑

- 配置按层级生效：用户级、仓库级、工作区级。
- 使用 `jj config edit --user`、`--repo`、`--workspace` 编辑对应层级。
- 使用 `jj config path --user|--repo|--workspace` 查看实际配置文件路径。
- 配置为 TOML 格式，后加载的层级会覆盖前一层。

# 常见配置点

- 自动跟踪新文件：`[snapshot] auto-track = true` 或按路径配置 `snapshot.auto-track`。
- 远端书签自动跟踪：`[remotes.<name>] auto-track-bookmarks = "*"`。
- 默认 fetch/push 远端：`[git] fetch = "upstream"`，`push = "origin"`。
- Gerrit 默认远端与分支：`[gerrit] default-remote = "origin"`，`default-remote-branch = "main"`。
