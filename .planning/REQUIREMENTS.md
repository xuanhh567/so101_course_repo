# Requirements: SO-101 LeRobot 教改课程仓库

**Defined:** 2026-05-12
**Core Value:** 学生必须能在真实课堂硬件上看懂检测结果、正确改写 LeRobot 命令，并完成从校准到数据采集、训练、部署的最小闭环。

## v1 Requirements

### Repository Foundation

- [ ] **REPO-01**: 新仓库包含现有 Markdown 课程、检测工具和原始 Word 源材料。
- [ ] **REPO-02**: 新仓库具备 GSD 配置、项目上下文、需求、路线和状态文件。
- [ ] **REPO-03**: 仓库内 Markdown 链接不依赖旧机器绝对路径。
- [ ] **REPO-04**: 仓库有明确贡献/维护说明，指导后续改课时保护学生主路径。

### Course Content

- [ ] **CONT-01**: 三次课实验均包含课前准备、课内目标、操作步骤、参数来源、提交要求和评分点。
- [ ] **CONT-02**: `primer/` 和 `labs/` 的阅读顺序清晰，学生可以从 README 进入完整路径。
- [ ] **CONT-03**: `basic_operation/` 章节与三次课主线互相引用，作为教师备课和学生补查材料。
- [ ] **CONT-04**: Word 源材料与 Markdown 课程完成一次差异核对，缺失内容被补入或明确废弃。

### Classroom Tooling

- [ ] **TOOL-01**: `tools/detect_system.py` 的输出结构有 fixture 测试覆盖。
- [ ] **TOOL-02**: 检测工具缺少 `ffmpeg`、`ffprobe` 或 `v4l2-ctl` 时给出可理解的降级结果。
- [ ] **TOOL-03**: 设备扫描输出和相机截图的 Git 跟踪策略明确，避免课堂运行造成无意义变更。
- [ ] **TOOL-04**: README 明确说明 `device_simple.json`、截图、`tty/dev` 和 `by-id/by-path` 的关系。

### Quality Gates

- [ ] **QUAL-01**: 提供 Markdown 链接检查。
- [ ] **QUAL-02**: 提供命令占位符检查，确保每个 `<PLACEHOLDER>` 在文档中有解释。
- [ ] **QUAL-03**: 提供课程发布检查清单，用于开课前确认环境、硬件、材料和兜底路径。
- [ ] **QUAL-04**: 每个阶段完成后有验证记录，说明哪些需求已满足、哪些还需继续。

### Teacher Deliverables

- [ ] **TEACH-01**: 形成教师课前准备清单。
- [ ] **TEACH-02**: 形成三次课评分表或 rubric。
- [ ] **TEACH-03**: 形成常见故障处理清单，覆盖端口变化、相机反接、训练过慢和 rollout 失败。
- [ ] **TEACH-04**: 形成 v1 发布包说明，帮助教师复制到课堂机器。

## v2 Requirements

### Publishing

- **PUB-01**: 生成静态课程网站。
- **PUB-02**: 生成 PDF/打印版实验书。
- **PUB-03**: 将课堂提交模板整理成可分发压缩包。

### Automation

- **AUTO-01**: 自动从 Word 源材料抽取文本并生成差异报告。
- **AUTO-02**: 提供课堂机器环境自检报告导出。
- **AUTO-03**: 提供多组学生设备扫描结果的匿名汇总工具。

## Out of Scope

| Feature | Reason |
|---------|--------|
| 重写 LeRobot | 上游框架已提供核心机器人工作流，本项目聚焦教学组织 |
| 自动完成学生作业评分 | v1 先把评分标准和证据链做清楚 |
| 远程训练平台 | 当前目标是课堂最小闭环，不扩大到基础设施建设 |
| 自动识别 top/wrist 语义 | 通过截图判断相机角色是课程要训练的能力 |

## Traceability

| Requirement | Phase | Status |
|-------------|-------|--------|
| REPO-01 | Phase 1 | Pending |
| REPO-02 | Phase 1 | Pending |
| REPO-03 | Phase 1 | Pending |
| REPO-04 | Phase 1 | Pending |
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
| TEACH-01 | Phase 5 | Pending |
| TEACH-02 | Phase 5 | Pending |
| TEACH-03 | Phase 5 | Pending |
| TEACH-04 | Phase 5 | Pending |

**Coverage:**
- v1 requirements: 20 total
- Mapped to phases: 20
- Unmapped: 0

---
*Requirements defined: 2026-05-12*
*Last updated: 2026-05-12 after initial definition*
