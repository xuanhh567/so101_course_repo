# 第三次课：ACT 训练启动与策略部署

本次课的目标是让学生基于第二次课采集的数据，改写训练命令，并根据当前设备扫描结果完成 rollout，同时看懂训练固定参数、输出目录和 checkpoint 的关系。

## 主线位置

### 上一段产物

第二段已经得到 replay 验证过的数据集、明确的 `<DATASET_REPO_ID>`，并形成了操作前重新确认硬件映射的习惯。

### 本段要完成

完成 ACT 训练命令改写、训练输出目录理解、checkpoint 选择，以及 rollout 命令改写和部署验证。

### 下一段会用到什么

本段完成后，SO-101 + LeRobot 的最小教程闭环结束；后续阶段只继续补质量检查、排错路径和工具可靠性。

## 先修导学

- [04. ACT 导学](../primer/04_act_intro.md)

ACT 从 dataset 学习动作策略，训练会产出 checkpoint，rollout 会把某个 checkpoint 部署回机器人；如果这条链路不清楚，先查上面的 ACT 导学。

## 课前准备

- 第二次课已经得到可用数据集
- 本机或服务器具备可用训练环境
- 学生知道本组的数据集名称

## 课内目标

- 会改写 `<DATASET_REPO_ID>`、`<OUTPUT_DIR>`、`<CHECKPOINT_PATH>`
- 能成功启动 ACT 训练
- 能看懂训练输出目录中的 checkpoint 和日志
- 能在已有 checkpoint 上直接执行或改写 rollout 命令

## 课内步骤

### 1. 先检查训练环境

```bash
python3 tools/detect_system.py
```

### 2. 启动 ACT 训练

执行前先确认：

- `--policy.type=act` 和 `--device=cuda` 是课程固定值
- `<DATASET_REPO_ID>`、`<OUTPUT_DIR>` 才是本组需要按任务改的值
- 输出目录要能让你在课后继续找到 checkpoint

```bash
lerobot-train \
  --policy.type=act \
  --dataset.repo_id=<DATASET_REPO_ID> \
  --output_dir=<OUTPUT_DIR> \
  --job_name=act_so101_lab \
  --device=cuda
```

### 3. 识别训练输出

课堂内至少完成：

- 训练命令改写
- 训练启动
- 理解输出目录
- 能指出后续 rollout 该使用哪个 checkpoint

### 4. rollout 前先确认

- `follower`、`top_camera`、`wrist_camera` 仍然是这次真实连接的设备
- checkpoint 路径要对照本组训练输出确认
- 如果你临时换了设备、重插相机或移动了连接，先重新运行一次检测，不要直接沿用旧命令
- rollout 应使用最新的 device_simple.json 里的当前 `tty` / `dev` 值

确认完以后，再执行下面这条命令。

```bash
lerobot-rollout \
  --robot.type=so101_follower \
  --robot.port=<FOLLOWER_PORT> \
  --robot.cameras='{"top": {"type": "opencv", "index_or_path": "<TOP_CAMERA_DEV>", "width": 640, "height": 480, "fps": 30}, "wrist": {"type": "opencv", "index_or_path": "<WRIST_CAMERA_DEV>", "width": 640, "height": 480, "fps": 30}}' \
  --policy.path=<CHECKPOINT_PATH>
```

## 参数来源

- `<DATASET_REPO_ID>`：来自第二段录制并 replay 验证过的数据集
- `<OUTPUT_DIR>`：本组选择的训练输出目录，后续要能在这里找到 checkpoint
- `<FOLLOWER_PORT>`：来自重新运行检测后 `follower` 当前 `tty`
- `<TOP_CAMERA_DEV>`：来自重新运行检测后 `top_camera` 当前 `dev`
- `<WRIST_CAMERA_DEV>`：来自重新运行检测后 `wrist_camera` 当前 `dev`
- `<CHECKPOINT_PATH>`：来自训练输出目录中的目标 checkpoint

## 预期效果

- 课堂上能成功启动训练
- 能说明输出目录里 checkpoint 的位置
- 能在已有或课后完成的 checkpoint 上完成 rollout

## 扩展部署说明

如果本组额外接入了 `side_camera`，可以在默认 `top + wrist` 部署成功后，再把第三路视角加入 `robot.cameras` 配置，作为进阶部署练习。

## 课内必须完成

- 改写训练命令
- 启动训练
- 截图保存训练日志或输出目录结构
- 改写 rollout 命令草稿

## 课后完成

- 等待训练收敛
- 选择 checkpoint
- 完成 rollout 验证

## 兜底路径

如果训练时间过长，可以临时使用已有 checkpoint 完成 rollout 命令改写和部署验证；但仍然要确认自己的训练命令和输出目录是可理解、可复现的。

## 练习记录

- 改写后的训练命令
- 训练启动截图或日志截图
- 一份输出目录说明
- 实际执行过的 rollout 命令
- 使用自训或已有 checkpoint 的 rollout 结果截图

## 自检清单

- 能正确改写数据集与输出目录参数
- 能成功启动 ACT 训练
- 能解释 checkpoint 来源
- 能完成 rollout 命令改写并验证

## 细化参考

- [06. ACT 训练](../basic_operation/06_act_training.md)
- [07. 策略部署](../basic_operation/07_policy_deployment.md)
