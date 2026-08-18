# OFFICIAL REQUIREMENTS MAPPING

## 来源验证状态

工作区内存在 `官方要求与项目执行约束.md`，但其自述为项目内部统一约束源，并列出了位于桌面其他位置的比赛方案 PDF、参考资料 PDF、FAQ DOCX、技术方案报告模板 DOCX 和样例 DOCX。本次只扫描当前工作区，未打开这些官方原文件，因此：**OFFICIAL_SOURCE_NOT_VERIFIED**。下表的“官方材料明确要求/官方模板建议”均是对内部整理文件标签的索引，不等同于本次重新核验了官方原文。

## 官方材料明确要求（内部整理文件标注，原件未在工作区核验）

| 要求 | 当前项目映射 | 状态 |
|---|---|---|
| 两个场景需做渐进式长期退化建模 | 电池 + 反作用轮 future-HI 主线 | 部分完成 |
| 公开跨领域数据 -> 航天仿真目标域 -> 迁移/适配 | source 数据、Basilisk 目标域、迁移合同 | 迁移真实执行未完成 |
| 至少输出长期退化趋势或有依据的 RUL | 当前主线为 future-HI/趋势 | 进行中 |
| 提交技术报告、数据说明、可执行 PyTorch 代码和复现说明 | `docs/`、`scripts/`、`train/`、submission staging | 最终交付未完成 |
| 至少与一种现有方法公平对比 | source 比较含 Ridge/MLP/GRU/TCN；目标域 B0/B1/T1/T2 | source 已做，目标域未做 |
| 代码和主要结果可复现 | lock、audit、runner 已存在 | clean reproduction 未完成 |

## 官方模板建议（不是同等级硬要求）

| 建议 | 当前项目映射 | 状态 |
|---|---|---|
| 报告说明输入窗口、域投影、编码器、预测头和训练目标 | configs/contracts 与模型代码 | 阶段性具备 |
| 报告误差、稳定性、提前性、鲁棒性和失败案例 | source 稳定性已有；目标域尚缺 | 未闭环 |
| 使用配置驱动目录职责划分 | `configs/ simulation/ datasets/ models/ train/ evaluate/ tests/` | 基本具备 |
| Docker、独立复跑、部署/使用说明 | 当前控制文件列为工程任务 | 未完成 |
| 样例结构可参考但虚构参数/结果不得复用 | 项目约束明确禁止冒充 | 一致 |

## 当前项目自行采用的工程规则

- `docs/project_progress_network.md` 作为当前进度唯一入口。
- snapshot 默认拒绝、一次性 grant、消费/撤销、独立 post-run auditor 和故障注入。
- primary test / diagnostic_test 封存，开发阶段不读取。
- truth/observed 隔离，禁止将 hidden truth、checkpoint index、退化进度和场景 ID 作为模型输入。
- 活动轨道使用完整 2026 TLE；不恢复 2013 不完整轨道参数。
- Basilisk `u_current` 按实际轮转矩 `N m` 解释，不改名为电流。
- `.train-wheel-cache` 受本地环境审计哈希绑定，不从原工作区删除，但不进入 GitHub 审查包。

这些规则对当前工程是有效约束，但不能在报告中全部表述为官方比赛硬要求。

## 未决冲突

- 内部整理文件记录官方方案对提交渠道同时出现 RAR 邮件和申报系统两种表述。由于官方原件未在本次工作区核验，状态为 `UNKNOWN`，应由赛事方或负责人外部确认。
- Docker 在内部整理文件中同时被描述为重要加分项/评分项，而不是参赛资格门槛；不得写成未经核验的强制资格条件。
