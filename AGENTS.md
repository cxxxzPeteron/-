# 项目协作规则

这是挑战杯揭榜挂帅项目，不是数学建模项目。组件固定为电池和反作用轮，官方约束优先于个人假设。

## 开始任何工作前

1. 先阅读 `docs/project_progress_network.md`，确认当前阶段、已完成项和唯一下一步。
2. 再阅读相关配置、数据清单和审计证据；不要用历史文件里的阶段性 `next_step` 覆盖当前状态。
3. 区分官方事实、软件默认、项目基线、假设、可见遥测和隐藏真值。

## 红线

- 不把 2013 不完整轨道参数重新作为活动基线；活动轨道使用完整 2026 TLE。
- 不把真值字段、`checkpoint_index`、退化进度或场景 ID直接喂给模型。
- 不把 Basilisk 的 `u_current` 改名为电流；当前语义是实际轮转矩 `N m`。
- 不在没有电池目标域数据和源域模型前开始迁移微调。
- 不修改或删除历史审计证据来掩盖旧方案；新结论写入当前状态文档。
- 不把 `.train-wheel-cache` 当作普通缓存删除；当前 wheel 与 metadata 受环境审计哈希绑定。
- 桌面 `航天器关键组件寿命预测_提交包_当前版` 只由工作区精选同步，不在其中直接开发，也不把历史目录整体复制进去。
- 正式批量生成前必须有用户明确授权、输入哈希快照和全量 dry-run。

## 当前入口

项目进度唯一入口：`docs/project_progress_network.md`

根目录使用说明：`README.md`

当前已审计成果入口：`deliverables/README.md`

最终提交 staging 与文件选择：`submission/README.md`、`submission/FILE_SELECTION.md`
