# Requirements: SO-101 LeRobot 教程

**Defined:** 2026-05-12
**Core Value:** 读者必须能按教程独立完成 SO-101 + LeRobot 的最小闭环，并理解每个命令参数来自哪里。

## v1 Requirements

### Tutorial Foundation

- [ ] **TUT-01**: README 明确说明本仓库是一套教程，而不是评价或教改交付系统。
- [ ] **TUT-02**: 教程主路径能从 README 顺序进入 `primer/`、`labs/` 和必要的 `basic_operation/`。
- [ ] **TUT-03**: 教程材料不依赖旧机器绝对路径。
- [ ] **TUT-04**: 仓库维护说明要求后续改动保护教程主路径。

### Tutorial Content

- [ ] **CONT-01**: 三段主教程均包含目标、准备、步骤、参数来源、预期效果、练习记录和自检清单。
- [ ] **CONT-02**: `primer/` 提供足够概念背景，但不阻塞读者进入实际操作。
- [ ] **CONT-03**: `basic_operation/` 作为细化参考，只服务补查，不成为第二套主线。
- [ ] **CONT-04**: Word 源材料仅作为历史来源；需要补入教程的内容应转成 Markdown。

### Device Tutorial Tooling

- [ ] **TOOL-01**: `tools/detect_system.py` 的输出结构有 fixture 测试覆盖。
- [ ] **TOOL-02**: 检测工具缺少 `ffmpeg`、`ffprobe` 或 `v4l2-ctl` 时给出可理解的降级结果。
- [ ] **TOOL-03**: 设备扫描输出和相机截图的 Git 跟踪策略明确，避免运行教程时造成无意义变更。
- [ ] **TOOL-04**: README 明确说明 `device_simple.json`、截图、`tty/dev` 和 `by-id/by-path` 的关系。

### Tutorial Quality

- [ ] **QUAL-01**: 提供 Markdown 链接检查。
- [ ] **QUAL-02**: 提供命令占位符检查，确保每个 `<PLACEHOLDER>` 在文档中有解释。
- [ ] **QUAL-03**: 提供教程运行前自检清单，覆盖环境、硬件、数据集和 checkpoint。
- [ ] **QUAL-04**: 提供常见问题排查章节，覆盖端口变化、相机反接、训练过慢和 rollout 失败。

## v2 Requirements

### Publishing

- **PUB-01**: 生成静态教程网站。
- **PUB-02**: 生成 PDF/打印版教程。
- **PUB-03**: 提供只包含教程正文和工具脚本的轻量发布包。

### Automation

- **AUTO-01**: 自动从 Word 源材料抽取文本并生成差异报告。
- **AUTO-02**: 提供教程运行环境自检报告导出。
- **AUTO-03**: 提供多组设备扫描结果的匿名样例整理工具。

## Out of Scope

| Feature | Reason |
|---------|--------|
| 评价机制、评分表、rubric | 用户明确不需要 |
| 自动完成学生作业评分 | 本仓库目标是教程，不是评测系统 |
| 教改申报书包装 | 当前优先级是可学习、可操作的教程 |
| 重写 LeRobot | 上游框架已提供核心机器人工作流，本项目聚焦教程组织 |
| 远程训练平台 | 当前目标是本地教程闭环，不扩大到基础设施建设 |
| 自动识别 top/wrist 语义 | 通过截图判断相机角色是教程要训练的能力 |

## Traceability

| Requirement | Phase | Status |
|-------------|-------|--------|
| TUT-01 | Phase 1 | Pending |
| TUT-02 | Phase 1 | Pending |
| TUT-03 | Phase 1 | Pending |
| TUT-04 | Phase 1 | Pending |
| CONT-01 | Phase 2 | Pending |
| CONT-02 | Phase 2 | Pending |
| CONT-03 | Phase 2 | Pending |
| CONT-04 | Phase 2 | Pending |
| TOOL-01 | Phase 3 | Pending |
| TOOL-02 | Phase 3 | Pending |
| TOOL-03 | Phase 3 | Pending |
| TOOL-04 | Phase 3 | Pending |
| QUAL-01 | Phase 4 | Pending |
| QUAL-02 | Phase 4 | Pending |
| QUAL-03 | Phase 4 | Pending |
| QUAL-04 | Phase 4 | Pending |

**Coverage:**
- v1 requirements: 16 total
- Mapped to phases: 16
- Unmapped: 0

---
*Requirements defined: 2026-05-12*
*Last updated: 2026-05-12 after tutorial-only scope update*
