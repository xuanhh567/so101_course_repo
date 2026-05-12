# Phase 2: Tutorial Flow Hardening - Patterns

**Date:** 2026-05-12

## Pattern Map

| Target | Role | Closest Existing Analog | Pattern To Preserve |
|--------|------|-------------------------|---------------------|
| `labs/01_lab_env_mapping_calibration.md` | Main lab 1 | Existing same file plus `basic_operation/02_arm_detection.md` | Keep direct operational steps, explain `tty` vs `by-id`, and keep detailed lookup links at the end. |
| `labs/02_lab_teleop_record_replay.md` | Main lab 2 | Existing same file plus `basic_operation/04_teleoperation.md` and `basic_operation/05_dataset_recording.md` | Keep camera-role confirmation before commands; explain `dev` and screenshot usage before command blocks. |
| `labs/03_lab_act_train_deploy.md` | Main lab 3 | Existing same file plus `basic_operation/06_act_training.md` and `basic_operation/07_policy_deployment.md` | Keep dataset/output/checkpoint explanation close to train and rollout commands. |
| `README.md` | Main route and lookup index | Current README | Preserve index-style route; add concise tool usage and reference positioning without turning README into a long narrative. |
| `basic_operation/00_command_template_guide.md` | Detailed command rewriting reference | Current same file | Keep as detailed reference for translating `device_simple.json` fields into LeRobot command placeholders. |
| `source_materials/README.md` | Source-material scope note | Current same file | Keep Word sources as references to distill, not final reading path. |

## Local Documentation Conventions

- Chinese is the primary instructional language.
- `README.md -> labs/` is the main route.
- `primer/` is concept reference material.
- `basic_operation/` is lookup reference material.
- `source_materials/` is source material for selective extraction.
- LeRobot commands stay in fenced shell blocks.
- Angle-bracket placeholders are used for reader-specific values.
- Placeholder sources should be explained before the command that uses them.
- Reader records are `练习记录` and `自检清单`, not grading.

## Concrete Reusable Wording

Use or adapt these existing phrases:

- `本仓库的主路径是 README.md -> labs/。`
- `basic_operation/ 是操作补查材料，不是第二条主线。`
- `by-id / by-path：帮助你识别这是哪一个物理设备`
- `当前 tty / dev：用于这一次实际执行的 LeRobot 命令`
- `Word 文件保留为来源，不作为最终阅读路径。`

## File-Level Notes

### Labs
- Add short continuity blocks near the top of each lab.
- Normalize section names without removing existing command content.
- Keep `细化参考` at the end unless an essential warning must be near a command.

### README
- Keep concise.
- Tool guidance belongs in `## 核心工具`.
- Lookup guidance belongs in `## 操作补查`.

### Tooling
- Do not edit `tools/detect_system.py` in Phase 2 unless a broken doc claim is discovered.
- It is enough to validate `python3 -m py_compile tools/detect_system.py` and `python3 tools/detect_system.py --help`.

## PATTERN MAPPING COMPLETE
