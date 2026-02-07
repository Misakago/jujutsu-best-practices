# Gerrit 基础流程

- 用 `jj gerrit upload -r @-` 上传当前工作副本父变更，或用 `-r <revset>` 指定要上传的变更栈。
- 上传前用 `jj log -r <revset>` 确认范围，避免漏传或多传。

# Change-Id 管理

- `jj gerrit upload` 会在提交说明中写入 Change-Id trailer；若已有 Change-Id 则沿用。
- 默认 Change-Id 由 JJ change ID 派生，便于在重写历史时保持与 Gerrit 变更的映射。
- 需要关联现有 Gerrit 变更时，在变更描述中写入目标 Change-Id。

# 更新评审

- 修改历史变更后再次 `jj gerrit upload`，Gerrit 会生成新的 patch set。
- 建议用 `jj evolog` 或 `jj log -r` 查看变更演化，确保上传的是预期版本。

# 默认远端与分支

- 用仓库级配置简化命令：打开 `jj config edit --repo`，加入以下配置：

```toml
[gerrit]
default-remote = "<remote>"
default-remote-branch = "<branch>"
```

- 之后可直接 `jj gerrit upload`，无需每次指定 `--remote` 与 `--remote-branch`。
