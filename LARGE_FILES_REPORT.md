# LARGE FILES REPORT

## 汇总

- 原项目总大小（不含派生的 `github_review_bundle/`）：**27594.72 MB**（28,935,161,879 bytes，79,548 files）
- GitHub 审查包：**23.52 MB**（24,663,724 bytes，1,113 files）
- 审查包最大文件：`FILE_INVENTORY.csv` (13.61 MB)
- 原项目阈值统计：>10 MB: 62 个, >50 MB: 18 个, >100 MB: 13 个, >500 MB: 3 个
- Git 状态：当前根目录不是 Git repository，因此无法判断历史 Git index 中是否已跟踪大文件；上传前应在审查包目录初始化新仓库并再次检查。

## 封存测试元数据扫描

- SEALED_TEST_CONTENT_READS = 0
- 仅按路径名称识别并统计：519 files，126.51 MB
- 扩展名计数：.csv: 233, .h5: 38, .json: 156, .md: 1, .py: 11, .pyc: 15, .svg: 36, .tag: 1, .txt: 1, .xml: 23, [no extension]: 4
- 未打开文件内容，未加载 HDF5/NPY/NPZ/CSV，未读取 truth/label，未调用 dataset loader，未计算数据统计量，未运行预测或评估。

## 顶层占用

| 路径 | 大小 | 文件数 |
|---|---:|---:|
| `data` | 19135.90 MB | 26954 |
| `.venv-train` | 4212.70 MB | 26524 |
| `.train-wheel-cache` | 2464.81 MB | 2 |
| `.venv-sim` | 757.81 MB | 12269 |
| `runs` | 505.61 MB | 4935 |
| `simulation` | 290.36 MB | 830 |
| `analysis` | 183.14 MB | 6405 |
| `docs` | 31.50 MB | 132 |
| `scripts` | 4.42 MB | 511 |
| `tests` | 2.98 MB | 519 |
| `deliverables` | 2.21 MB | 22 |
| `configs` | 1.03 MB | 250 |
| `train` | 1.02 MB | 78 |
| `datasets` | 0.90 MB | 76 |
| `.pytest_cache` | 0.17 MB | 6 |
| `evaluate` | 0.07 MB | 6 |
| `models` | 0.05 MB | 12 |
| `官方要求与项目执行约束.md` | 0.02 MB | 1 |
| `.contest_brief_extract.txt` | 0.01 MB | 1 |
| `submission` | 0.00 MB | 3 |
| `__pycache__` | 0.00 MB | 2 |
| `README.md` | 0.00 MB | 1 |
| `AGENTS.md` | 0.00 MB | 1 |
| `conftest.py` | 0.00 MB | 1 |
| `requirements-simulation-lock.txt` | 0.00 MB | 1 |
| `requirements-train-common-lock.txt` | 0.00 MB | 1 |
| `requirements-simulation.txt` | 0.00 MB | 1 |
| `.gitignore` | 0.00 MB | 1 |
| `requirements-train-torch-cu126.txt` | 0.00 MB | 1 |
| `requirements-train-torch-cpu.txt` | 0.00 MB | 1 |
| `requirements-source.txt` | 0.00 MB | 1 |

## 主要排除的大文件

| 路径 | 大小 | 类别 | 排除原因 |
|---|---:|---|---|
| `.train-wheel-cache/torch-2.9.1+cu126-cp312-cp312-win_amd64.whl` | 2464.78 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `.venv-train/Lib/site-packages/torch/lib/torch_cuda.dll` | 985.54 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `.venv-train/Lib/site-packages/torch/lib/cublasLt64_12.dll` | 507.18 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `.venv-train/Lib/site-packages/torch/lib/cudnn_engines_precompiled64_9.dll` | 490.12 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `.venv-train/Lib/site-packages/torch/lib/cusparse64_12.dll` | 274.32 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `.venv-train/Lib/site-packages/torch/lib/cudnn_adv64_9.dll` | 269.36 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `.venv-train/Lib/site-packages/torch/lib/cufft64_11.dll` | 264.50 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `.venv-train/Lib/site-packages/torch/lib/torch_cpu.dll` | 250.63 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `data/processed/battery_source/signals.h5` | 183.65 MB | processed_data | 大型数据、数组或 checkpoint；保留对应 manifest/audit |
| `.venv-train/Lib/site-packages/torch/lib/cusolver64_11.dll` | 131.88 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `.venv-train/Lib/site-packages/torch/lib/cudnn_ops64_9.dll` | 120.65 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `.venv-sim/Lib/site-packages/llvmlite/binding/llvmlite.dll` | 114.79 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `.venv-train/Lib/site-packages/torch/lib/cublas64_12.dll` | 100.02 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `.venv-train/Lib/site-packages/torch/lib/cusolverMg64_11.dll` | 80.74 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `.venv-train/Lib/site-packages/torch/lib/curand64_10.dll` | 60.35 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `runs/bearing_source_future_hi_forecast_v8/predictions.jsonl` | 54.25 MB | run_artifact | 预测明细、checkpoint 或大型运行产物 |
| `.venv-train/Lib/site-packages/torch/lib/cudnn_heuristic64_9.dll` | 54.19 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `runs/bearing_source_future_hi_forecast_v2/predictions.jsonl` | 54.13 MB | run_artifact | 预测明细、checkpoint 或大型运行产物 |
| `.venv-train/Lib/site-packages/torch/lib/nvrtc64_120_0.alt.dll` | 43.80 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `.venv-train/Lib/site-packages/torch/lib/nvrtc64_120_0.dll` | 43.74 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `.venv-train/Lib/site-packages/torch/lib/nvJitLink_120_0.dll` | 37.42 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `.venv-train/Lib/site-packages/numpy.libs/libopenblas64__v0.3.23-293-gc2f4bdbb-gcc_10_3_0-2bde3a66a51006b2b53eb373ff767a3f.dll` | 36.40 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `docs/archive/source_artifacts/tmp_bct_2026.pdf` | 28.85 MB | documentation | 历史 docs archive 已由索引说明，不完整复制 |
| `.venv-train/Lib/site-packages/torch/lib/torch_cpu.lib` | 28.08 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `analysis/battery_source_hi_condition_v2_paired_results_v1/figures/02_逐电池MAE配对变化.tiff` | 25.52 MB | result | 大型或非审查必要的分析中间产物 |
| `analysis/battery_source_hi_condition_v2_paired_results_v2/figures/02_逐电池MAE配对变化.tiff` | 25.52 MB | result | 大型或非审查必要的分析中间产物 |
| `.venv-sim/Lib/site-packages/pymupdf/mupdfcpp64.dll` | 25.08 MB | cache | 本地环境或受审计 wheel 缓存，体积大且不可移植 |
| `analysis/battery_source_hi_condition_v2_paired_results_v1/figures/01_训练池扩充效果总览.tiff` | 25.06 MB | result | 大型或非审查必要的分析中间产物 |
| `analysis/battery_source_hi_condition_v2_paired_results_v2/figures/01_训练池扩充效果总览.tiff` | 25.06 MB | result | 大型或非审查必要的分析中间产物 |
| `runs/bearing_source_future_hi_forecast_v8/job_manifest.jsonl` | 20.86 MB | run_artifact | 预测明细、checkpoint 或大型运行产物 |

## 元数据与恢复路径

- 原始 NASA/XJTU 数据：不复制；从原工作区 `data/raw/` 恢复，数据来源、hash、split 以相邻 manifest/schema/audit 为准。
- Basilisk HDF5 与 processed HDF5：不复制；从原工作区 `data/processed/` 及 simulation 输出恢复，生成配置与审计证据保留在 `configs/`、`analysis/` 和数据目录的 manifest 中。
- Checkpoints：默认全部不复制；从 `runs/` 的正式 runner 按 frozen config/snapshot 复现，正式 run 的 checkpoint manifest、metrics、completion/audit 元数据保留。
- 大型预测明细：不复制 v8/v2 `predictions.jsonl`；聚合指标、稳定性诊断和 recommendation 已在 `analysis/` 保留。
- 本地环境与 wheel cache：不复制；依赖锁文件保留。`.train-wheel-cache` 在原工作区受哈希绑定，不应删除。

## GitHub 适用性

该 bundle 采用白名单复制，没有 HDF5、MAT、NPY/NPZ、Parquet 或 PT/PTH/CKPT。只要上传前确认 GitHub 单文件限制和仓库总量，当前体积适合用于代码与项目状态审查；它不是包含完整数据和模型权重的可离线训练镜像。
