# 核心心智模型

- 把工作副本当作一个可变更的变更（change），默认会自动快照并记录状态；不要把它当作“未提交的临时区”。
- 优先使用 change ID 来引用变更；change ID 在重写历史时保持稳定，便于追踪演化。
- 以 revset 思维定位变更，用 `jj log -r <revset>` 精确选择操作对象。

# 基本工作流

- 创建/继续变更：用 `jj new` 生成新变更并把工作副本移动到新变更上；用 `jj edit <rev>` 切换到需要继续编辑的变更。
- 描述变更：用 `jj describe` 或 `jj describe -m "..."` 写清目的与范围。
- 查看历史：用 `jj log` 或 `jj log -r <revset>`，必要时加 `--stat` 或 `-p`。

# 变更整理

- 合并：用 `jj squash` 把当前变更内容并入父变更，清理提交历史。
- 拆分：用 `jj split` 把一个变更拆成多个逻辑变更，便于评审。
- 演化查看：用 `jj evolog` 查看某个变更在重写过程中的演化轨迹。
- 自动吸收：有需要时使用 `jj absorb`，并在执行前用 `jj absorb --help` 明确具体行为。

# 冲突处理

- 冲突会体现在 `jj status` 中；用 `jj resolve` 启动冲突解决流程，或使用你熟悉的合并工具。
- 解决后用 `jj diff` 检查结果是否符合预期，再继续重写或推送。

# 文件跟踪与忽略

- 新文件默认自动跟踪（可用配置项调整）；需要时使用 `jj file track` / `jj file untrack` 精确控制。
- 使用 `.gitignore` 管理忽略模式，避免噪音文件进入工作副本。

# 操作日志与回滚

- 用 `jj op log` 查看仓库的操作历史。
- 用 `jj undo` 回滚最近操作；必要时用 `jj op restore` 恢复到某次操作点。
- 需要只回滚历史记录中的特定操作时使用 `jj op revert`。
- 使用 `--at-op <op>` 临时查看历史操作点的仓库状态。

# 多工作区

- 用 `jj workspace add` 添加工作区，实现多目录并行处理同一仓库。
- 出现工作副本过期或不一致时，使用 `jj workspace update-stale` 同步状态。
