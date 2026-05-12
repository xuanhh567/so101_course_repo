# SO-101 LeRobot 教改课程仓库

## What This Is

这是一个面向 SO-101 机械臂和 LeRobot 工作流的教改项目仓库。它把半成品课程材料整理成可维护、可验证、可继续迭代的三次课实验书，并保留教师备课所需的细化章节和原始 Word 材料。

## Core Value

学生必须能在真实课堂硬件上看懂检测结果、正确改写 LeRobot 命令，并完成从校准到数据采集、训练、部署的最小闭环。

## Requirements

### Validated

- ✓ 三次课主线已经形成：环境与校准、遥操作与数据、ACT 训练与部署。
- ✓ 检测脚本已经能输出 `device_simple.json` 并保存相机截图。
- ✓ 导学与细化操作章节已经分层，学生入口和教师备课入口已初步分离。

### Active

- [ ] 把现有内容整理成可发布的新仓库结构，旧仓库不再承担后续规划。
- [ ] 建立 GSD 项目上下文、需求、路线和阶段验收机制。
- [ ] 修复可移植性问题，特别是绝对路径链接和生成文件边界。
- [ ] 增加内容质量检查，覆盖 Markdown 链接、命令占位符、提交材料和评分点。
- [ ] 把教师侧交付物补齐为可复用包：教案、评分表、课前准备清单、课堂故障处理清单。
- [ ] 为 `tools/detect_system.py` 增加 fixture 级测试，降低课堂前修改脚本的风险。

### Out of Scope

- 重新实现 LeRobot 或 ACT 算法 — 本项目教授和组织 LeRobot 工作流，不替代上游框架。
- 训练大模型或提供通用机器人平台 — v1 只围绕 SO-101 教学闭环。
- 建设完整 LMS/在线判题系统 — 可以后续集成，但当前优先级是课程材料和课堂执行可靠性。
- 自动识别每台相机的物理角色 — 当前仍要求学生结合截图判断，这是课程目标的一部分。

## Context

当前半成品已经有可用内容：`README.md`、`primer/`、`labs/`、`basic_operation/` 和 `tools/detect_system.py`。旧仓库存在未提交的课堂硬件扫描结果；新仓库复制了当前磁盘状态，并把外层 Word 文档放入 `source_materials/` 作为溯源材料。

教学现场假设为 Linux + SO-101 主从臂 + top/wrist 摄像头 + 已预装 LeRobot 环境。学生的核心困难不是记命令，而是理解每个参数来自哪个设备证据，并在重插设备后重新判断。

## Constraints

- **Hardware**: 课程依赖真实 SO-101、串口和 V4L 摄像头 — 文档和工具必须服务课堂现场。
- **Portability**: 仓库会在不同机器之间移动 — Markdown 链接应使用相对路径。
- **Class Time**: 三次课时间有限 — 每次课必须有明确课堂必达成果和兜底路径。
- **Upstream Dependency**: LeRobot CLI 可能变化 — 命令需要定期与官方文档和课堂环境核对。
- **Evidence**: 学生提交必须保留命令、截图或 `device_simple.json` — 评分要能回溯。

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| 新仓库命名为 `so101_course_repo` | 用户选择 1B，偏课程发布语义 | — Pending |
| 先做现有内容梳理 | 用户选择 2A，先把半成品转成代码库地图 | — Pending |
| 使用标准严谨 GSD 配置 | 用户选择 3A，规划入库并启用研究、计划检查和验证 | — Pending |
| 保留三次课主线 | 当前 README 和 labs 已围绕三次课组织，适合课程闭环 | — Pending |
| 保留 Word 源材料 | 便于后续核对教改申报材料和 Markdown 化内容 | — Pending |

## Evolution

This document evolves at phase transitions and milestone boundaries.

**After each phase transition** (via `$gsd-transition`):
1. Requirements invalidated? -> Move to Out of Scope with reason
2. Requirements validated? -> Move to Validated with phase reference
3. New requirements emerged? -> Add to Active
4. Decisions to log? -> Add to Key Decisions
5. "What This Is" still accurate? -> Update if drifted

**After each milestone** (via `$gsd-complete-milestone`):
1. Full review of all sections
2. Core Value check — still the right priority?
3. Audit Out of Scope — reasons still valid?
4. Update Context with current state

---
*Last updated: 2026-05-12 after initialization*
