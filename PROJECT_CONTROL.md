# PROJECT CONTROL

> 状态口径：`DONE` 仅表示真实执行完成、有正式产物且相应审计通过；`READY` 表示代码、配置与执行链已准备，但真实执行尚未发生；`RUNNING` 表示当前确有执行；`TODO` 表示尚未完成。当前没有正式训练、适配或 test 任务在运行。

## 项目总目标

本项目面向航天器关键组件长期退化预测，组件固定为反作用轮与电池。主线先利用公开跨领域退化数据构建 source future-HI 模型，再利用 Basilisk 航天目标域仿真数据建立严格隔离的 observed/truth 历史接口。随后在验证域比较目标域从零训练与迁移/适配方案，只有验证合同和审计通过后才进入封存测试。最终目标是形成可复现的训练、迁移、评估和工程交付链，而不是把 current-HI、RUL 或合成 dry-run 结果冒充 future-HI 正式结论。

## A. 反作用轮

| 阶段 | 状态 | 证据与边界 |
|---|---|---|
| 1. XJTU-SY 源域数据 | DONE | 已形成 source windows/manifest；固定 test 未解封。 |
| 2. future-HI 数据构建 | DONE | v3 future-window 资产及审计已进入 v8 训练绑定。 |
| 3. source 模型比较 | DONE | v8：Ridge/MLP/GRU/TCN，12 条开发轴承，h=1/5/10。 |
| 4. source final-refit | DONE | 全部 12 条开发轴承、GRU、3 horizon、5 seed。 |
| 5. 正式 source checkpoint | DONE | `runs/bearing_source_future_hi_final_refit_v1/`，独立重建审计通过。 |
| 6. Basilisk 目标域数据 | DONE | observed/truth 元数据与正式目标域资产已存在。 |
| 7. truth/observed 隔离 | DONE | `target_domain_history_truth_bundles_v2` 及 post-run audit 通过。 |
| 8. 目标域历史窗口与 loader | DONE | reference index、合成 loader、受限真实 loader dry-run 已完成；不等于正式训练。 |
| 9. synthetic B0/B1/T1/T2 | DONE | 合成迁移链和独立 auditor 通过。 |
| 10. 真实 B1 | TODO | 尚未正式执行。 |
| 11. 真实 T1 | TODO | 尚未正式执行。 |
| 12. 真实 T2 | TODO | 尚未正式执行。 |
| 13. B0 | TODO | 真实目标域 baseline 尚未执行。 |
| 14. validation 迁移结论 | TODO | 尚无真实 B0/B1/T1/T2 验证比较。 |
| 15. primary test | TODO | 仍封存，禁止读取。 |
| 16. 消融/鲁棒性 | TODO | 需在主验证链完成后按既定合同执行。 |
| 17. RUL | TODO | 当前 future-HI 主线未完成；是否保留需负责人确认，不在本次扩展。 |
| 18. final deliverables | TODO | 尚未形成最终提交包。 |

**CURRENT STEP：READY - 反作用轮 target future-HI reference-only episode index 的一次性真实执行与独立审计。**

**NEXT_STEP_CANDIDATE：PENDING_EXTERNAL_REVIEW - 候选为负责人审查并决定是否授权已冻结的 reference snapshot；本次不执行。**

## B. 电池

| 阶段 | 状态 | 证据与边界 |
|---|---|---|
| 1. NASA 源域解析 | DONE | NASA 电池源域解析和已审计源数据资产存在。 |
| 2. 当前 HI baseline | DONE | 历史 current-HI baseline 已完成，但不能冒充 future-HI。 |
| 3. future-HI 任务合同 | DONE | `d-15..d -> HI(d+h)`，h=1/2/4，合同审计通过。 |
| 4. future-HI 正式窗口 | DONE | 3135 个真实窗口，post-run audit v2 通过。 |
| 5. synthetic trainer | DONE | 48 jobs、checkpoint replay 与故障注入审计通过。 |
| 6. 正式 source future-HI 训练 | READY | v2 snapshot/audit 已冻结，默认拒绝；正式输出不存在。 |
| 7. source 模型选择 | TODO | 等待正式 source 训练及独立审计。 |
| 8. source final-refit | TODO | 尚未执行。 |
| 9. 正式 source checkpoint | TODO | 尚未生成。 |
| 10. 航天电池目标域数据 | DONE | 目标 observed/truth 资产与隔离 bundle 已存在。 |
| 11. target history interface | DONE | reference index 与 loader 接口已建立。 |
| 12. h=1/2/4 目标预测接口 | READY | 合同已定义，尚无正式目标训练结果。 |
| 13. target scratch baseline | TODO | 尚未执行。 |
| 14. transfer/adaptation | TODO | 尚未执行。 |
| 15. validation | TODO | 尚未执行。 |
| 16. test_in_distribution | TODO | 封存。 |
| 17. test_unseen_load | TODO | 封存。 |
| 18. final deliverables | TODO | 尚未形成最终提交包。 |

**CURRENT STEP：READY - 电池 source future-HI 正式训练的一次性授权与执行。**

**NEXT_STEP_CANDIDATE：PENDING_EXTERNAL_REVIEW - 候选为负责人审查并决定是否签发绑定 v2 snapshot/audit 的一次性正式训练 grant；本次不执行。**

## C. 总工程

| 项目 | 状态 | 说明 |
|---|---|---|
| Docker | TODO | 根目录未发现现成 Dockerfile/compose。 |
| requirements/environment lock | DONE | simulation/train lock 文件与本地受审计环境存在；本地 wheel cache 不进 GitHub。 |
| 一键复跑 | TODO | 当前为多 runner/授权链，尚无最终单入口。 |
| 非主要开发成员 clean reproduction | TODO | 尚未完成独立 clean reproduction。 |
| README | READY | 有根 README，但状态有漂移，需后续按控制文件修订。 |
| deployment/user guide | TODO | 未形成最终用户指南。 |
| 最终图表 | TODO | 有阶段分析图表，最终版未冻结。 |
| 技术报告 | TODO | 未形成最终技术报告。 |
| submission package | READY | staging 与文件选择规则存在，但内容尚非最终版。 |

## 关键状态证据卡

### 反作用轮 source v8 与 final-refit

- STATUS: CURRENT_FORMAL
- CONFIDENCE: HIGH
- EVIDENCE_PATHS: `docs/project_progress_network.md`; `runs/bearing_source_future_hi_forecast_v8/`; `runs/bearing_source_future_hi_final_refit_v1/`; `analysis/bearing_source_future_hi_forecast_stability_v1/model_recommendation_v1.json`
- REASON: 进度网明确记录真实执行完成、独立 checkpoint 重建审计通过、grant 已消费撤销；模型建议明确限制为 source 候选。

### 反作用轮 target future-HI reference

- STATUS: CURRENT_READY
- CONFIDENCE: HIGH
- EVIDENCE_PATHS: `docs/project_progress_network.md`; `analysis/reaction_wheel_target_future_hi_reference_v1/execution_snapshot_v1.json`; `analysis/reaction_wheel_target_future_hi_reference_v1/execution_snapshot_audit_v1.json`
- REASON: 活动 snapshot audit 通过且默认拒绝；正式 output/staging 不存在，真实执行尚未发生。

### 电池 source future-HI 正式训练

- STATUS: CURRENT_READY
- CONFIDENCE: HIGH
- EVIDENCE_PATHS: `docs/project_progress_network.md`; `analysis/battery_source_future_hi_forecast_real/execution_snapshot_v2.json`; `analysis/battery_source_future_hi_forecast_real/execution_snapshot_audit_v2.json`
- REASON: 执行链和 v2 快照已冻结并 `pass_default_deny`，但正式输出和 staging 不存在。

### 其余孤立版本或证据冲突项

- STATUS: UNKNOWN
- CONFIDENCE: LOW
- EVIDENCE_PATHS: 对应目录的 manifest/audit/completion；若缺失则无充分证据。
- REASON: 不以 v1/v2/v8/v9 或目录名推断有效性，等待外部审查。

## 封存测试边界

- SEALED_TEST_CONTENT_READS = 0
- 本次仅记录 test/primary test/diagnostic_test 的路径、文件名、数量、大小和扩展名；未打开内容、未加载数组/HDF5/CSV、未读取 truth/label、未调用 loader、未计算统计、未预测或评估。
