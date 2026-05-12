# Phase 2: Tutorial Flow Hardening - Research

**Date:** 2026-05-12
**Phase:** 02 - Tutorial Flow Hardening

## Research Question

What needs to be known to plan Phase 2 well: how to harden the three `labs/` tutorials into a continuous tutorial, keep `primer/` and `basic_operation/` in their reference roles, selectively use `source_materials/`, and add clear usage guidance for `tools/detect_system.py` without reintroducing evaluation mechanisms?

## Sources Read

### Local Project Sources
- `.planning/phases/02-tutorial-flow-hardening/02-CONTEXT.md`
- `.planning/ROADMAP.md`
- `.planning/REQUIREMENTS.md`
- `.planning/STATE.md`
- `.planning/codebase/CONVENTIONS.md`
- `.planning/codebase/STRUCTURE.md`
- `README.md`
- `labs/01_lab_env_mapping_calibration.md`
- `labs/02_lab_teleop_record_replay.md`
- `labs/03_lab_act_train_deploy.md`
- `basic_operation/00_command_template_guide.md`
- `basic_operation/02_arm_detection.md`
- `basic_operation/02a_device_roles_filling_guide.md`
- `tools/detect_system.py`
- `tools/devices/device_simple.json`
- `source_materials/README.md`

### External Reference Sources
- Hugging Face LeRobot SO-101 docs: https://huggingface.co/docs/lerobot/en/so101
- Hugging Face LeRobot Getting Started with Real-World Robots: https://huggingface.co/docs/lerobot/main/getting_started_real_world_robot
- Hugging Face LeRobot Policy Deployment / `lerobot-rollout`: https://huggingface.co/docs/lerobot/main/inference

## Key Findings

### Current Tutorial Already Has Most Raw Pieces
- The README already presents the main route, concept references, operation references, core tool commands, practice records, source materials, and official references.
- Each lab already has a goal-like intro, preparation, steps, parameter list, expected effects, practice records, self-checklist, and detailed references.
- The missing hardening is mostly structure and continuity rather than new content: the labs need explicit "previous output / current work / next usage" handoffs and a consistent template surface.

### Tool Guidance Is Present But Not Yet a Tutorial Contract
- README has a useful "核心工具" section with:
  - `python3 tools/detect_system.py`
  - `python3 tools/detect_system.py --skip-capture`
  - `python3 tools/detect_system.py --format json`
- `tools/detect_system.py` actually supports `--format text|json` and `--skip-capture`, writes `tools/devices/device_simple.json`, clears and recreates `tools/devices/images/`, and prints either text or JSON.
- `device_simple.json` exposes the fields the tutorial should teach:
  - `arms.*.tty` for current LeRobot serial port values.
  - `arms.*.port` as the stable `/dev/serial/by-id/...` identity helper.
  - `cameras.*.dev` for current LeRobot camera node values.
  - `cameras.*.by_path` / `by_id` as physical identity helpers.
  - `cameras.*.image`, `capture_status`, and `capture_detail` for screenshot-based camera role judgment.
- The plan should make tool usage explicit in the labs and README, but should not turn tools into a separate product or Phase 3 detector reliability work.

### Official LeRobot Docs Confirm The Same Learning Loop
- The official real-world robot tutorial describes the sequence: set up/calibrate, teleoperate, record a dataset, replay, train a policy, then evaluate/deploy. That matches the three-lab structure.
- The official docs emphasize that a robot `id` can be used to store calibration files consistently across teleoperation, recording, and evaluation. The current local tutorial does not focus on `id`; Phase 2 should not introduce a broad command rewrite, but a planner may add a note to verify command form and id handling during execution if it is already relevant to a step.
- The official training example currently shows `python lerobot/scripts/train.py` and `--policy.device=cuda`, while local docs use `lerobot-train` and `--device=cuda`. This phase should not silently replace commands without local CLI verification. It should strengthen parameter-source explanations and leave command-version validation as an explicit verification note.
- The current official rollout docs describe `lerobot-rollout` with `--strategy.type=base`, `--policy.path`, `--robot.port`, `--task`, and `--duration`. The local tutorial uses a simpler rollout command. Phase 2 can flag the command as a template whose placeholders must be explained, but major rollout command modernization should be verified before changing.

### Source Materials Should Stay Selective
- `source_materials/README.md` already defines the Word files as source material to distill into Markdown, not final reading paths.
- Phase 2 context chooses selective extraction only when it improves the continuity of `labs/`. The execution plan should avoid broad DOCX migration.
- If extraction is needed, the relevant files are:
  - `预实验：LeRobot 环境创建.docx` for environment/setup continuity.
  - `模块一：物理基座构建与遥操作.docx` and `实验一：物理基座构建与遥操作.docx` for lab 1 and lab 2 continuity.
  - `实验二：专家示范与高质量数据工程.docx` for lab 2 data capture continuity.

## Planning Implications

### Recommended Plan Split
- **Plan 02-01:** Normalize and connect the three `labs/` pages. This covers the main Phase 2 goal and most CONT-01/CONT-02/CONT-03.
- **Plan 02-02:** Harden README/tool/reference guidance. This captures user-requested tools usage guidance, README-centered lookup positioning, and selective source-material handling.

The phase is documentation-focused and does not need code changes unless a doc verification helper is already available. Avoid editing `tools/detect_system.py` in Phase 2.

### Required Content Changes For Labs
Each `labs/*.md` should expose these exact reader-facing roles:
- "上一段产物"
- "本段要完成"
- "下一段会用到什么"
- "目标"
- "准备"
- "步骤"
- "参数来源"
- "预期效果"
- "练习记录"
- "自检清单"

The executor can choose final Chinese headings, but the plan should require grep-verifiable strings or section headings so completion is not subjective.

### Required Tool Guidance
The plan should require docs to state:
- Run `python3 tools/detect_system.py` before device-dependent commands.
- Use `--skip-capture` when screenshot capture is slow, blocked, or unnecessary.
- Use `--format json` when the reader wants machine-readable output in terminal.
- Open `tools/devices/device_simple.json` after detection.
- Open `tools/devices/images/` to judge camera roles when screenshots are saved.
- Use current `tty` / `dev` fields in LeRobot commands.
- Use `by-id` / `by-path` to identify physical devices, not as the main command values unless the tutorial explicitly tests that command form.
- Treat `capture_status` and `capture_detail` as diagnostic clues when an image is not saved.

### Avoided Scope
- No grading, rubric, course assessment, or teacher delivery package.
- No full Word-to-Markdown migration.
- No detector reliability refactor or fixture test expansion; that belongs to Phase 3.
- No large command modernization without local CLI verification.

## Validation Architecture

Phase 2 can be validated with lightweight documentation checks:

1. **Required heading/string checks**
   - `rg -n "上一段产物|本段要完成|下一段会用到什么" labs`
   - `rg -n "参数来源|预期效果|练习记录|自检清单" labs`
   - `rg -n "python3 tools/detect_system.py|--skip-capture|--format json|device_simple.json|tools/devices/images|capture_status|capture_detail" README.md labs basic_operation`

2. **Scope guard checks**
   - `rg -n "评分|评价|rubric|提交要求" README.md labs basic_operation AGENTS.md` should return no matches.

3. **Link checks**
   - Reuse the Phase 1 local Markdown link check approach if available.
   - At minimum, run a local script or shell check that all relative Markdown links in touched Markdown files resolve.

4. **Command/tool sanity checks**
   - `python3 -m py_compile tools/detect_system.py`
   - `python3 tools/detect_system.py --help` should list `--format` and `--skip-capture`.
   - Do not require real hardware execution for Phase 2 verification; hardware validation remains manual or Phase 3+.

## Risks And Mitigations

| Risk | Mitigation |
|------|------------|
| Labs become repetitive after adding the full template | Keep continuity blocks short and operational. |
| `basic_operation/` becomes a second main path again | Keep README as the primary lookup index and only add essential lab links. |
| Tool guidance duplicates existing `basic_operation/00_command_template_guide.md` too much | README explains when to use the tool; `basic_operation/00` explains how to rewrite commands in detail. |
| Official LeRobot command names differ from local commands | Plan should require parameter-source clarity and command-form verification notes, not broad command replacement. |
| Word extraction expands beyond Phase 2 | Only extract snippets that fix continuity gaps, and document source-material scope in the plan. |

## RESEARCH COMPLETE
