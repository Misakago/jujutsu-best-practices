# GitHub/GitLab 基础流程

- 创建提交栈后再创建书签；只有需要推送时才需要书签。
- 当前没有 `git pull` 等价命令，使用 `jj git fetch` + `jj rebase -o <main-bookmark>` 更新本地变更。

# 生成式书签流程

- `jj new main` 从主线开始新变更。
- 完成一段工作后 `jj commit -m "..."`，jj 会创建新工作副本并保留上一个变更。
- 推送时用 `jj git push --change @-`（或 `-c`）让 jj 自动创建远端书签名。

# 命名书签流程

- `jj new main` 创建新变更，完成若干次 `jj commit -m "..."`。
- `jj bookmark create <name> -r @-` 在工作副本父变更上创建书签。
- `jj bookmark track <name>` 建立跟踪关系后 `jj git push`。

# 回复评审的两种策略

- 追加提交：`jj new <bookmark>` 继续工作，`jj commit -m "..."` 后 `jj bookmark move <bookmark> --to @-` 再 `jj git push`。
- 重写提交：`jj new <bookmark>-`（revset 语法）创建要修改的历史位置，修复后 `jj squash`，再 `jj git push --bookmark <bookmark>`。

# 与他人书签协作

- 需要基于他人远端书签工作时：`jj new <bookmark>@<remote>`。
- 需要自动导入所有远端书签时：配置 `remotes.<name>.auto-track-bookmarks = "*"`。

# GitHub CLI 在非 colocated 仓库

- 设置 `GIT_DIR=.jj/repo/store/git` 让 `gh` 能正确定位 Git 元数据。

# 多远端工作流

- 典型结构：`upstream` 作为主仓库，`origin` 作为个人 fork。
- 配置默认远端：`[git] fetch = "upstream"`，`push = "origin"`。
- 需要双向同步时：`fetch = ["upstream", "origin"]`。
