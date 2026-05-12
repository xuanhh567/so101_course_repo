# SO-101 LeRobot 教程

## What This Is

这是一套面向 SO-101 机械臂和 LeRobot 工作流的教程仓库。它把现有半成品材料整理成一条可按顺序学习的路径：环境检查、设备识别、主从臂校准、遥操作、数据采集、ACT 训练和策略部署。

## Core Value

读者必须能按教程独立完成 SO-101 + LeRobot 的最小闭环，并理解每个命令参数来自哪里。

## Requirements

### Validated

- ✓ 三段式教程主线已经形成：环境与校准、遥操作与数据、ACT 训练与部署。
- ✓ 检测脚本已经能输出 `device_simple.json` 并保存相机截图。
- ✓ 导学、主线教程和细化操作章节已经初步分层。
- ✓ Phase 2 已把三段主教程连接成连续路径，并补充工具使用说明、参数来源和来源材料边界。

### Active

- [ ] 把仓库定位从“教改项目/实验书”收窄为“可顺序学习的教程”。
- [ ] 清理评分、rubric、教师交付包等非教程目标。
- [x] 统一教程导航，让读者知道先读什么、做什么、遇到问题查哪里。
- [ ] 把“提交要求”改成“练习记录”，把“评分点”改成“自检清单”。
- [ ] 增加内容质量检查，覆盖 Markdown 链接、命令占位符和旧路径。
- [ ] 为 `tools/detect_system.py` 增加 fixture 级测试，降低修改脚本的风险。

### Out of Scope

- 评价机制、评分表、rubric、作业判分 — 用户明确不需要。
- 教改申报材料包装 — 当前目标是一套教程，不是申报书。
- 重新实现 LeRobot 或 ACT 算法 — 本项目教授和组织 LeRobot 工作流，不替代上游框架。
- 建设完整 LMS/在线判题系统 — 超出教程仓库边界。
- 自动识别每台相机的物理角色 — 当前仍要求读者结合截图判断，这是教程要训练的能力。

## Context

当前仓库已经有可用内容：`README.md`、`primer/`、`labs/`、`basic_operation/` 和 `tools/detect_system.py`。用户反馈不需要评价机制，只需要一套教程，因此后续规划应优先服务阅读路径、操作连续性、命令可复制性和故障排查。

教学现场仍可使用这套教程，但仓库本身不再围绕教师评分、课程考核或教改交付物组织。保留 `source_materials/` 只是为了追溯原始材料，不代表后续要恢复评价体系。

## Constraints

- **Hardware**: 教程依赖真实 SO-101、串口和 V4L 摄像头 — 文档和工具必须服务实际操作。
- **Portability**: 仓库会在不同机器之间移动 — Markdown 链接应使用相对路径。
- **Continuity**: 读者需要一条连续路径 — 主教程不能被过多教师侧材料打断。
- **Upstream Dependency**: LeRobot CLI 可能变化 — 命令需要定期与官方文档和实际环境核对。
- **Practice Evidence**: 建议保留命令、截图或 `device_simple.json` 作为自查记录，不作为评分机制。

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| 新仓库命名为 `so101_course_repo` | 用户选择 1B，偏课程发布语义 | — Pending |
| 项目定位改为教程仓库 | 用户明确只需要一套教程，不需要评价机制 | — Pending |
| 移除评价机制目标 | 评分表、rubric、作业评价不再进入 v1 范围 | — Pending |
| 保留三段式闭环主线 | 当前 labs 已围绕最小闭环组织，适合作为教程主线 | Validated in Phase 2 |
| 保留 Word 源材料 | 只作为历史来源，不驱动教程架构 | Validated in Phase 2 |

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
*Last updated: 2026-05-12 after Phase 2 tutorial flow hardening*
