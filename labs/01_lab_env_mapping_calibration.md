# 第一次课：环境验证、设备映射与主从臂校准

本次课的目标是让学生在已预装好的 LeRobot 环境中，学会读取 `device_simple.json`、识别主从臂，并完成主从臂校准。

## 主线位置

### 上一段产物

这是主线教程的第一段，从已经接入的 SO-101 主从臂、可选相机和已准备好的 LeRobot 环境开始。

### 本段要完成

完成环境验证、设备扫描、`leader` / `follower` 物理角色判断、当前 `tty` 识别和主从臂校准。

### 下一段会用到什么

第二段会直接使用校准后的主从臂、可靠的 `leader` / `follower` 映射，以及每次操作前重新运行 `python3 tools/detect_system.py` 的习惯。

## 先修导学

- [00. 课程导览](../primer/00_course_map.md)
- [01. SO-101 导学](../primer/01_so101_intro.md)
- [02. LeRobot 导学](../primer/02_lerobot_intro.md)

`leader` / `follower` 是物理角色，`/dev/ttyACM*` 是当前系统分配的端口；如果这两个概念不清楚，先查上面的 SO-101 和 LeRobot 导学，再进入本次课的端口识别与校准操作。

## 课前准备

- LeRobot 与依赖已经预装完成
- 学生座位上的主臂、从臂已经接入电脑
- 相机可以接入，但第一次课不要求完成相机实验

## 课内目标

- 会运行 `python3 tools/detect_system.py`
- 会看懂 `leader` 和 `follower` 的当前端口
- 会看懂机械臂的 `tty` 和 `by-id`
- 会把 `<LEADER_PORT>`、`<FOLLOWER_PORT>` 改写成自己的端口
- 完成主从臂校准

## 课内步骤

### 1. 验证环境

```bash
lerobot-find-port --help
lerobot-calibrate --help
python3 tools/detect_system.py
```

`python3 tools/detect_system.py` 会写入 `tools/devices/device_simple.json`，并刷新 `tools/devices/images/` 下的相机截图。截图不需要或相机被占用时，可以使用 `python3 tools/detect_system.py --skip-capture`；需要在终端直接查看 JSON 时，可以使用 `python3 tools/detect_system.py --format json`。

### 2. 识别设备并绑定角色

```bash
python3 tools/detect_system.py
lerobot-find-port
```

第一次运行 `python3 tools/detect_system.py` 后，请按这个顺序看：

1. 打开 [device_simple.json](../tools/devices/device_simple.json)
2. 在 `arms` 里看两只机械臂当前对应的 `tty`
3. 同时记录它们的 `by-id`，帮助你分辨哪只是主臂、哪只是从臂
4. 如果本组已经接了相机，也顺手看一下 `cameras` 和截图，后面第二次课会直接用到

### 3. 执行前先确认

- 先确认你已经分清哪只是 `leader`、哪只是 `follower`
- 先确认这次真正要用的 `tty` 与当前连接一致
- 先确认你写进命令的是当前 `tty`，不是 `by-id`

确认完这 3 件事后，再执行下面这条校准命令。

### 4. 参考命令

```bash
lerobot-calibrate \
  --teleop.type=so101_leader \
  --teleop.port=<LEADER_PORT>

lerobot-calibrate \
  --robot.type=so101_follower \
  --robot.port=<FOLLOWER_PORT>
```

## 参数来源

- `<LEADER_PORT>`：先判断哪只物理臂是 `leader`，再从 `tools/devices/device_simple.json` 里找到它当前 `tty`
- `<FOLLOWER_PORT>`：先判断哪只物理臂是 `follower`，再从 `tools/devices/device_simple.json` 里找到它当前 `tty`

`by-id` 帮助你识别物理设备，当前 `tty` 才是这一次写进 LeRobot 命令的端口。

## 预期效果

- 主臂和从臂分别完成零位校准
- 终端出现保存结果或校准完成提示
- 后续遥操作时主从臂没有明显零位偏差
- 即使断电重连后重新运行检测，`leader` 和 `follower` 仍然能恢复到正确角色

## 课后任务

- 复查一次 `device_simple.json`
- 用文字说明 `by-id` 和 `ttyACM*` 的区别
- 如果课堂上没接相机，课后预习 `top_camera` 和 `wrist_camera` 的角色概念

## 练习记录

- `tools/devices/device_simple.json`
- 你实际执行过的校准命令
- 一张校准成功截图

## 自检清单

- 能正确识别 `leader` 和 `follower`
- 能正确辨认主臂和从臂
- 能手动改写 `<LEADER_PORT>` 和 `<FOLLOWER_PORT>`
- 能完成校准并保留结果

## 细化参考

- [00. 如何从检测结果改写命令](../basic_operation/00_command_template_guide.md)
- [01. 环境搭建与 CLI 验证](../basic_operation/01_environment_setup.md)
- [02. 设备映射与角色绑定](../basic_operation/02_arm_detection.md)
- [02A. 如何根据截图和 device_simple 判断设备角色](../basic_operation/02a_device_roles_filling_guide.md)
- [03. 主从臂校准](../basic_operation/03_calibration.md)
