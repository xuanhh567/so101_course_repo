# SO-101 LeRobot 教程

这是一套 SO-101 + LeRobot 上手教程，目标是带读者从环境检查、设备识别、遥操作、数据采集、ACT 训练一路走到策略部署。

本仓库的主路径是 `README.md -> labs/`。`primer/` 用来查概念，`basic_operation/` 用来补查细节，`source_materials/` 保存手工搭建的原始材料供后续提炼。

## 主线教程

按下面顺序完成三段教程：

1. [第一段：环境验证、设备映射与主从臂校准](labs/01_lab_env_mapping_calibration.md)
2. [第二段：遥操作、数据采集与回放](labs/02_lab_teleop_record_replay.md)
3. [第三段：ACT 训练启动与策略部署](labs/03_lab_act_train_deploy.md)

三段教程对应一条最小闭环：

1. 识别硬件和环境
2. 校准主从臂
3. 通过遥操作采集演示数据
4. 用演示数据训练 ACT 策略
5. 把 checkpoint 部署回机器人

每段产物：

- 第一段产物：校准后的 `leader` / `follower` 主从臂，以及每次操作前重新确认设备映射的习惯。
- 第二段产物：replay 验证过的数据集、明确的 `<DATASET_REPO_ID>`，以及确认过的相机角色映射。
- 第三段产物：ACT 训练输出和 checkpoint 理解，以及可改写的 rollout 命令。

## 概念参考

`primer/` 是概念参考，不是进入主线教程前的必读门槛。遇到概念不清楚时再回来查。

1. [00. 课程导览](primer/00_course_map.md)
2. [01. SO-101 导学](primer/01_so101_intro.md)
3. [02. LeRobot 导学](primer/02_lerobot_intro.md)
4. [03. 具身智能数据采集导学](primer/03_embodied_data_intro.md)
5. [04. ACT 导学](primer/04_act_intro.md)

## 操作补查

`basic_operation/` 是操作补查材料，不是第二条主线。主线教程里某个步骤不清楚时，按主题跳到对应章节。

如果主线教程中的某一步卡住，先回到这里按主题补查；不要把 `basic_operation/` 当成另一条从头读到尾的主线。

1. [00. 如何从检测结果改写命令](basic_operation/00_command_template_guide.md)
2. [01. 环境搭建与 CLI 验证](basic_operation/01_environment_setup.md)
3. [02. 设备映射与角色绑定](basic_operation/02_arm_detection.md)
4. [02A. 如何根据截图和 device_simple 判断设备角色](basic_operation/02a_device_roles_filling_guide.md)
5. [03. 主从臂校准](basic_operation/03_calibration.md)
6. [04. 带相机的遥操作](basic_operation/04_teleoperation.md)
7. [05. 数据采集与回放](basic_operation/05_dataset_recording.md)
8. [06. ACT 训练](basic_operation/06_act_training.md)
9. [07. 策略部署](basic_operation/07_policy_deployment.md)

## 核心工具

```bash
python3 tools/detect_system.py
python3 tools/detect_system.py --skip-capture
python3 tools/detect_system.py --format json
```

三条命令的用途：

- `python3 tools/detect_system.py`：完整扫描，写入 `tools/devices/device_simple.json`，刷新 `tools/devices/images/`，并打印文本摘要。
- `python3 tools/detect_system.py --skip-capture`：只扫描设备，不抓取截图；相机被占用、截图太慢或本次不需要截图时使用。
- `python3 tools/detect_system.py --format json`：在终端输出同一份扫描结果的 JSON，方便复制或进一步检查。

检测工具会输出：

- 当前识别到的设备
- 机械臂当前 `tty` 与 `by-id`
- 相机当前 `dev` 与 `by-path`
- `tools/devices/images/` 下的相机截图
- [device_simple.json](tools/devices/device_simple.json)
- `capture_status` 和 `capture_detail`，用于判断截图是保存、跳过还是失败

如果你现在最大的困惑是“不知道怎么分清主臂、从臂、top 相机、wrist 相机”，先看：

- [02A. 如何根据截图和 device_simple 判断设备角色](basic_operation/02a_device_roles_filling_guide.md)

建议每次都按同一顺序操作：

1. 运行 `python3 tools/detect_system.py`
2. 打开 [device_simple.json](tools/devices/device_simple.json)
3. 先看机械臂的 `tty` 和 `by-id`
4. 再看相机的 `dev`、`by-path` 和 `image`
5. 打开 `tools/devices/images/` 下的截图，确认哪一路是 `top`，哪一路是 `wrist`
6. 再把当前 `tty` / `dev` 手动填入 LeRobot 命令

这里要特别区分两类字段：

- `by-id` / `by-path`：帮助你识别这是哪一个物理设备
- 当前 `tty` / `dev`：用于这一次实际执行的 LeRobot 命令

常用字段对应关系：

- `arms.*.tty`：判断物理角色后，填写 `<LEADER_PORT>` / `<FOLLOWER_PORT>`
- `arms.*.port` 或 `by-id`：帮助识别是哪只物理机械臂
- `cameras.*.dev`：判断截图角色后，填写 `<TOP_CAMERA_DEV>` / `<WRIST_CAMERA_DEV>`
- `cameras.*.by_path` / `by_id`：帮助识别是哪一路物理相机
- `cameras.*.image`：截图保存成功时，对应 `tools/devices/images/` 下的图片
- `capture_status` / `capture_detail`：说明截图保存、跳过或失败的原因

## 练习记录

建议每一段都保留这些记录，方便自己回看和排错：

- 自己修改后的命令
- 改了哪些参数、这些值来自 `device_simple.json` 的哪一项
- 终端截图、训练输出目录截图或本次的 `device_simple.json`

## 来源材料

`source_materials/` 保存手工搭建的 Word 来源材料。后续完善教程时，应参照这些材料，把有价值的内容提炼进 Markdown 教程，而不是让 Word 文件成为最终阅读路径。
Phase 2 只使用这些材料修补三篇主线教程的连续性缺口，不做完整 Word 迁移。

- [来源材料索引](source_materials/README.md)

## 推荐参考

- [LeRobot Installation](https://huggingface.co/docs/lerobot/en/installation)
- [LeRobot SO-101](https://huggingface.co/docs/lerobot/en/so101)
- [LeRobot Real Robot Data Collection](https://huggingface.co/docs/lerobot/en/il_robots)
- [LeRobot Inference / Rollout](https://huggingface.co/docs/lerobot/en/inference)
