# DOCUMENT DRIFT REPORT

核对基准：`docs/project_progress_network.md` 顶部和最新 superseding 段落、正式产物存在性、manifest/completion/audit 状态。历史证据不重写。

## CONFIRMED_STALE

- `README.md`：仍以“迁移/适配尚未开始”等概括描述项目，未反映 target truth isolation v2、target reference index、真实 loader dry-run、反作用轮 synthetic transfer 与 source final-refit 已完成。
- `deliverables/README.md`：只覆盖较早电池交付物，未覆盖当前正式 source v8/final-refit、目标隔离/reference 和最新审计入口，不能作为完整当前资产索引。

## POSSIBLY_STALE

- `submission/README.md`：关于“目标正式历史窗口尚未生成”的表述需要拆分。reference index 已生成并审计，但反作用轮 future-HI reference-only episode index 仍未正式生成。
- `submission/FILE_SELECTION.md`：文件精选口径可能未纳入最新活动 snapshot、completion 与 recommendation，提交前需按 `REPOSITORY_MAP.md` 复核。
- `docs/project_progress_network.md`：作为追加式进程网保留了大量历史“当前唯一下一步”。内容本身是历史证据，但首次阅读者容易误取中段旧状态；应始终以顶部最新段落和 supersede 声明为准。

## CONSISTENT

- `AGENTS.md`：进度入口、真值隔离、Basilisk `u_current` 语义、授权/dry-run 与提交 staging 红线仍一致。
- `官方要求与项目执行约束.md`：作为官方约束入口保留，未发现需要由本次整理改写的科研结论。
- `submission/README.md` 与 `submission/FILE_SELECTION.md` 关于 staging 非开发区、不能整体复制历史目录的原则仍一致。

## 后续修订建议

在负责人确认本审查包后，只更新根 README 和 submission/deliverables 的“当前状态/入口”段落，保留历史审计文件原文；所有当前状态统一链接到 `PROJECT_CONTROL.md` 和 `docs/project_progress_network.md`。
