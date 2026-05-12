# Roadmap: SO-101 LeRobot 教改课程仓库

**Created:** 2026-05-12
**Granularity:** Standard

## Milestone v1: 可维护、可开课、可验证的三次课实验仓库

### Phase 1: Repository Foundation

**Goal:** 新仓库从半成品复制状态变成可维护项目骨架。

**Covers:** REPO-01, REPO-02, REPO-03, REPO-04

**Work:**
- 确认仓库目录、Git 分支、GSD 文件和维护说明。
- 清理旧绝对路径链接。
- 明确生成文件、样例文件和源材料的存放规则。
- 建立开工后默认阅读入口：`README.md`、`AGENTS.md`、`.planning/PROJECT.md`。

**Acceptance:**
- `git status` 清晰，初始提交包含课程材料和 GSD 文档。
- `rg '/home/xuan/so101_education|/home/xuan/Documents'` 不再命中文档链接。
- GSD 文件可支撑后续 `$gsd-plan-phase 2`。

### Phase 2: Course Content Hardening

**Goal:** 三次课实验书达到课堂发放质量。

**Covers:** CONT-01, CONT-02, CONT-03, CONT-04

**Work:**
- 逐篇检查 `labs/` 是否都有目标、步骤、参数来源、提交要求和评分点。
- 对照 `source_materials/` 中的 Word 文件，补齐 Markdown 漏掉的教改内容。
- 统一 primer、labs、basic_operation 的交叉引用和术语。
- 把“课堂必做”和“课后继续”区分得更清楚。

**Acceptance:**
- 每次课都能独立作为课堂讲义使用。
- 学生从 README 进入后不会遇到断链或旧路径。
- 教师能看出每个实验对应哪些评分证据。

### Phase 3: Detector Reliability

**Goal:** 让 `detect_system.py` 成为可测试、可维护的课堂基础设施。

**Covers:** TOOL-01, TOOL-02, TOOL-03, TOOL-04

**Work:**
- 为设备解析、相机格式解析和 JSON 输出增加 fixture 测试。
- 把可选系统工具缺失时的输出行为固定下来。
- 决定 `tools/devices/device_simple.json` 和截图是样例、忽略生成物，还是两者分离。
- 在 README 中补充学生如何使用检测结果的最短路径。

**Acceptance:**
- 无硬件环境下也能运行核心测试。
- 真实硬件验证步骤被记录。
- 课堂运行检测脚本不会污染发布仓库，或污染是有意且被说明的。

### Phase 4: Quality Gates

**Goal:** 用自动检查保护课程材料不退化。

**Covers:** QUAL-01, QUAL-02, QUAL-03, QUAL-04

**Work:**
- 增加 Markdown 链接检查。
- 增加 `<PLACEHOLDER>` 解释检查。
- 增加课程发布前检查清单。
- 建立阶段验证记录模板。

**Acceptance:**
- 一条本地命令能检查链接和占位符。
- 修改课程材料后能快速发现断链、漏解释和旧路径。
- 后续 GSD 阶段能用验证记录关闭需求。

### Phase 5: Teacher Delivery Pack

**Goal:** 形成教师可复用的开课交付包。

**Covers:** TEACH-01, TEACH-02, TEACH-03, TEACH-04

**Work:**
- 编写课前准备清单。
- 编写三次课评分 rubric。
- 编写常见故障处理清单。
- 编写 v1 发布包说明，包括复制仓库、检查环境、准备 checkpoint 的步骤。

**Acceptance:**
- 教师可以按清单准备课堂环境。
- 学生提交物和评分点一一对应。
- 训练过慢、设备重插、相机反接等常见问题有兜底路径。

## Suggested Next Command

Run:

```bash
$gsd-plan-phase 1
```

Phase 1 should be treated as the stabilization pass for the new repository before deeper content or tooling work.
