# Roadmap: SO-101 LeRobot 教程

**Created:** 2026-05-12
**Granularity:** Standard

## Milestone v1: 可顺序学习、可实际跑通的 SO-101 + LeRobot 教程

### Phase 1: Tutorial Foundation

**Goal:** 把仓库定位稳定为教程仓库，并清理非教程目标。

**Covers:** TUT-01, TUT-02, TUT-03, TUT-04

**Work:**
- 确认 README、PROJECT、REQUIREMENTS、ROADMAP 都使用教程定位。
- 清理旧绝对路径链接。
- 把“提交要求/评分点”改成“练习记录/自检清单”。
- 更新 `AGENTS.md`，要求后续维护保护教程主路径。

**Acceptance:**
- `rg '评分|评价|rubric|提交要求' README.md labs basic_operation AGENTS.md` 没有命中。
- 读者从 README 能理解教程入口和学习顺序。
- GSD 文件只保留 tutorial-only 的范围边界，不再规划非教程交付物。

### Phase 2: Tutorial Flow Hardening

**Goal:** 让三段主教程读起来像一套连续教程，而不是分散实验单。

**Covers:** CONT-01, CONT-02, CONT-03, CONT-04

**Work:**
- 逐篇检查 `labs/` 是否都有目标、准备、步骤、参数来源、预期效果、练习记录和自检清单。
- 调整 `primer/`，让概念导学支撑操作但不喧宾夺主。
- 整理 `basic_operation/` 的定位：只作为补查，不抢主线。
- 对照 `source_materials/`，只补入能改善教程连续性的内容。

**Acceptance:**
- 三段主教程能按顺序完成最小闭环。
- 读者遇到细节问题能跳到对应 `basic_operation/`。
- Word 源材料不会影响教程主路径。

### Phase 3: Detector Reliability

**Goal:** 让 `detect_system.py` 成为教程中可靠的设备识别辅助工具。

**Covers:** TOOL-01, TOOL-02, TOOL-03, TOOL-04

**Work:**
- 为设备解析、相机格式解析和 JSON 输出增加 fixture 测试。
- 把可选系统工具缺失时的输出行为固定下来。
- 决定 `tools/devices/device_simple.json` 和截图是样例、忽略生成物，还是两者分离。
- 在 README 中补充读者如何使用检测结果的最短路径。

**Acceptance:**
- 无硬件环境下也能运行核心测试。
- 真实硬件验证步骤被记录。
- 运行检测脚本不会污染教程仓库，或污染是有意且被说明的。

### Phase 4: Tutorial Quality Gates

**Goal:** 用自动检查保护教程材料不退化。

**Covers:** QUAL-01, QUAL-02, QUAL-03, QUAL-04

**Work:**
- 增加 Markdown 链接检查。
- 增加 `<PLACEHOLDER>` 解释检查。
- 增加教程运行前自检清单。
- 增加常见问题排查章节。

**Acceptance:**
- 一条本地命令能检查链接和占位符。
- 修改教程材料后能快速发现断链、漏解释和旧路径。
- 读者遇到端口变化、相机反接、训练过慢、rollout 失败时有排查路径。

## Suggested Next Command

Run:

```bash
$gsd-plan-phase 1
```

Phase 1 should be treated as the stabilization pass for the tutorial-only scope.
