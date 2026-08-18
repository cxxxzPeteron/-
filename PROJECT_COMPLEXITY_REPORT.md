# PROJECT COMPLEXITY REPORT

## 1. 是否存在过多重复版本

是。`analysis/` 和 `runs/` 中存在多轮 snapshot、grant、audit 与 v2/v5/v6/v7/v8 训练链证据。保留它们对追溯有价值，但没有单一控制面时会显著增加误用风险。

## 2. 最容易混淆的目录

- `analysis/`：活动审计、历史审计、失败证据和 synthetic fixture 混合。
- `runs/`：正式 v8/final-refit 与历史 v2、失败/中间运行并存。
- `data/processed/`：manifest、reference index、真实大数组与多个版本并存。
- `docs/`：进程网是追加式历史，旧 `next_step` 仍可被检索到。

## 3. 已经足够、不建议扩张的审计流程

snapshot 默认拒绝、一次性 grant、post-run 独立重建、checkpoint replay、访问边界记录和故障注入已经覆盖核心工程风险。后续应执行现有链并收敛正式资产，不再新增平行 auditor/grant 体系。

## 4. 仅属于工程护栏的任务

snapshot 哈希绑定、grant 消费/撤销、default-deny、resource preflight、staging 原子发布和 clean reproduction 都是必要工程护栏，但不构成科研创新或模型效果结论。

## 5. 以后可统一 archive 的历史目录

可候选归档：bearing forecast v2、v5 失败证据、superseded v6/v7 snapshots、target truth isolation v1 和中间 metadata snapshots、过期 synthetic fixtures。此次不移动、不删除；归档前需生成正式映射和保留审计引用。

## 6. 真正剩余的大任务数量

按可交付结果归并为 6 类：反作用轮真实 reference；反作用轮真实 B0/B1/T1/T2 与 validation；电池正式 source 训练/选择/final-refit；电池目标 scratch/transfer 与 validation；封存 test 与消融鲁棒性；最终复现、报告和提交包。

## 7. 反作用轮剩余关键任务

真实 future-HI reference-only index、真实 B0/B1/T1/T2、validation 迁移/负迁移结论、封存 primary test、既定消融/鲁棒性和最终交付。

## 8. 电池剩余关键任务

正式 source future-HI 训练、模型选择、final-refit/checkpoint、目标域 h=1/2/4 scratch 与 transfer、validation、两个封存 test 和最终交付。

## 9. 最终提交剩余关键任务

Docker/环境复现入口、一键复跑、非主要开发成员 clean reproduction、统一 README/用户指南、最终图表、技术报告、文件精选与 submission package 冻结。

## 控制建议

今后只在 `PROJECT_CONTROL.md` 更新 DONE/READY/RUNNING/TODO 和唯一下一步；`docs/project_progress_network.md` 继续保存详细时间线；历史资产只做分类与引用，不再以文件名版本号推断有效性。
