# REPOSITORY MAP

第一次阅读建议按此顺序：`PROJECT_CONTROL.md` -> `EXECUTIVE_STATUS.md` -> `docs/project_progress_network.md` -> 本文件列出的当前正式资产。历史文件中的 `next_step` 只代表当时状态，不能覆盖进度网顶部的当前状态。

## 1. 核心入口

| 目的 | 当前入口 |
|---|---|
| 项目进度入口 | `docs/project_progress_network.md` |
| 负责人控制面 | `PROJECT_CONTROL.md`、`EXECUTIVE_STATUS.md` |
| 反作用轮数据入口 | `data/processed/reaction_wheel_source/`、`data/processed/target_domain_history_windows_real_v1/` 及各自 manifest/audit |
| 反作用轮训练入口 | `scripts/run_bearing_source_future_hi_forecast_real_v2.py`、`scripts/run_bearing_source_future_hi_final_refit_v1.py` |
| 反作用轮迁移入口 | `train/bearing_to_rw_transfer.py`、`configs/bearing_to_reaction_wheel_future_hi_transfer_contract_v1.json` |
| 电池数据入口 | `data/processed/battery_source/`、`configs/battery_future_hi_forecast_task_contract_v1.json` |
| 电池训练入口 | `scripts/run_battery_source_future_hi_forecast_real_v1.py`（以活动 snapshot 实际绑定为准） |
| 主要配置 | `configs/` |
| 主要审计入口 | `analysis/` 中 `postrun_audit*`、`execution_snapshot_audit*` 与 recommendation |
| 主要结果入口 | `analysis/bearing_source_future_hi_forecast_results_v2/`、`analysis/bearing_source_future_hi_forecast_stability_v1/` |
| submission | `submission/README.md`、`submission/FILE_SELECTION.md` |
| deliverables | `deliverables/README.md` |

> 仓库中没有独立 `adapt/` 目录；迁移核心当前位于 `train/bearing_to_rw_transfer.py`，配置与执行脚本分别位于 `configs/`、`scripts/`。

## 2. 当前正式资产

- Dataset manifests：反作用轮 source future-window v3 manifest；`data/processed/battery_source/future_hi_windows_v1/` 的 manifest；`data/processed/target_domain_history_truth_bundles_v2/` 与 `data/processed/target_domain_history_windows_real_v1/` 的 manifest。
- Source model runs：`runs/bearing_source_future_hi_forecast_v8/`，独立 checkpoint 重建审计通过。
- Final-refit runs：`runs/bearing_source_future_hi_final_refit_v1/`，15 个 GRU source checkpoints，独立重建审计通过。
- Target manifests：target truth isolation v2、target history reference index v1 相关 manifest/completion。
- Audit reports：`analysis/bearing_source_future_hi_forecast_real/postrun_audit_v8.json`（若实际名称以目录登记为准）、`analysis/battery_source_future_hi_window_real/postrun_audit_v2.json`、`analysis/target_domain_truth_isolation_real_v2/postrun_audit_v1.json`、`analysis/target_domain_history_window_real_v1/postrun_audit_v1.json`。
- Model recommendations：`analysis/bearing_source_future_hi_forecast_stability_v1/model_recommendation_v1.json`；GRU 为 source 主候选，Ridge 为线性基线，不是目标域最终结论。
- Transfer contracts：`configs/bearing_to_reaction_wheel_future_hi_transfer_contract_v1.json`；B0/B1/T1/T2 仅 synthetic 链已通过。
- 当前 READY 资产：`analysis/reaction_wheel_target_future_hi_reference_v1/execution_snapshot_v1.json` 及 audit；`analysis/battery_source_future_hi_forecast_real/execution_snapshot_v2.json` 及 audit。二者均默认拒绝，不是结果。

## 3. 历史与失败资产

- `runs/bearing_source_future_hi_forecast_v2/`：历史真实训练与审计资产，已被 v8 当前正式版本替代。
- v5 runner 试跑：因 Ridge checkpoint 缺失而停止，属于 `REJECTED/FAILED`；证据保留，不复用。
- v6/v7 snapshot：实现迭代中间快照，属于 `HISTORICAL_VALID` 或 superseded，不是活动入口。
- target truth isolation v1 及 v1-v3/v5 metadata snapshots：历史/中间证据；当前正式执行结果为 v2 bundle。
- 旧 synthetic battery fixture：checkpoint 1 capacity-delta mask 与真实 producer 合同不一致，不作为真实逐值证据。
- 根 `README.md`、`submission/README.md`、`deliverables/README.md`：部分状态落后，见 `DOCUMENT_DRIFT_REPORT.md`，属于 `STALE_DOC` 或 `POSSIBLY_STALE`。
- 仅凭文件名无法确定的孤立 snapshot/run：统一标为 `UNKNOWN`，需依据 manifest、completion、errors 和活动配置人工确认。
