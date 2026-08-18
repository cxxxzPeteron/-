# 航天器关键组件寿命预测项目

本项目面向挑战杯揭榜挂帅赛题，组件范围固定为：

- 电池
- 反作用轮

当前项目状态、完成项、未完成项和唯一下一步请先阅读：

[项目进程网](docs/project_progress_network.md)

## 目录

```text
configs/      配置与策略
data/raw/     原始数据
data/processed/处理后的源域和目标域数据
datasets/     数据处理脚本
simulation/   Basilisk 仿真与验证
tests/        自动化测试
analysis/     审计与结果证据
docs/         研究、政策、报告和进程文档
scripts/      辅助脚本
deliverables/ 当前已审计、可直接查看和引用的成果
submission/   按官方五类交付物组织的提交 staging 与完成度
```

面向最终提交结构的当前精选副本位于桌面 `航天器关键组件寿命预测_提交包_当前版/`。开发仍只在本工作区进行，阶段完成后再按 manifest 同步，不直接在提交副本里继续开发。

## 当前可确认结果

- NASA 电池源域和 XJTU-SY 轴承源域已完成整理与预处理。
- 反作用轮 Basilisk 目标域正式数据已生成并通过全量完整性与泄漏审计。
- 电池目标域 `formal_v1` 已生成并通过独立完整性、质量字段与跨集合重复审计。
- 独立 PyTorch 本机训练环境已冻结并通过 CPU/CUDA smoke 与依赖审计。
- 电池源域六设备嵌套 CV 已完成 `96 job / 756 fit`，结果聚合、独立复算和中文图表人工验收均通过；当前成果入口见 `deliverables/battery_source_cv_v6/`。
- Ridge 的六设备平均 MAE 最低，但设备间差异较大；末步 MLP 更均衡但种子敏感；TCN 略优于 GRU。当前不宣布最终模型胜出。
- 电池 `diagnostic_test`、目标域训练/迁移和新的 Basilisk 执行仍封闭，当前下一步见 `docs/project_progress_network.md`。
- 迁移适配/微调尚未开始。

## 重要边界

目标域仿真真值（摩擦、容量、内阻、HI、RUL、EOL）不能直接作为模型输入。反作用轮当前保存的是轮速、转矩、姿态误差等已实现遥测；电流、功率和温度只有在建立并说明可靠模型后才能加入。

不要根据单个历史配置文件的 `next_step` 判断当前状态；以 `docs/project_progress_network.md` 和对应审计产物为准。
