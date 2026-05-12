---
phase: 02-tutorial-flow-hardening
status: passed
verified: 2026-05-12
must_haves_checked: 21
must_haves_passed: 21
human_verification_required: false
---

# Phase 02 Verification

## Verdict

Phase 02 passed.

The three main tutorials now read as a continuous tutorial path, README explains the detector tool and reference layers, `basic_operation/` remains lookup material, and `source_materials/` remains source provenance rather than the reader path.

## Goal Check

**Goal:** 让三段主教程读起来像一套连续教程，而不是分散实验单。

**Status:** Verified.

Evidence:

- `labs/01_lab_env_mapping_calibration.md`, `labs/02_lab_teleop_record_replay.md`, and `labs/03_lab_act_train_deploy.md` each contain `## 主线位置`, `### 上一段产物`, `### 本段要完成`, and `### 下一段会用到什么`.
- Each lab contains `## 参数来源`, `## 预期效果`, `## 练习记录`, `## 自检清单`, and `## 细化参考`.
- README now includes `每段产物` for the three main labs.

## Requirements

| Requirement | Status | Evidence |
|-------------|--------|----------|
| CONT-01 | Verified | All three labs include continuity blocks, parameter sources, expected effects, practice records, and self-checklists. |
| CONT-02 | Verified | Labs include short concept notes and link to `primer/`; `primer/` remains concept reference material. |
| CONT-03 | Verified | README and `basic_operation/00_command_template_guide.md` both state that `basic_operation/` is lookup support, not a second main path. |
| CONT-04 | Verified | `source_materials/README.md` contains `## Phase 2 使用边界` and states Word files only fill continuity gaps. |

## Must-Haves

| ID | Status | Evidence |
|----|--------|----------|
| D-01 | Verified | Each lab has `## 主线位置`. |
| D-02 | Verified | Each lab has `上一段产物`, `本段要完成`, `下一段会用到什么`. |
| D-03 | Verified | README still states `README.md -> labs/` as the main path. |
| D-04 | Verified | Each lab has normalized template sections. |
| D-05 | Verified | `练习记录` and `自检清单` remain self-check/tutorial language. |
| D-06 | Verified | `## 参数来源` sections explain placeholder value sources. |
| D-07 | Verified | Labs include short concept notes and retain primer links. |
| D-08 | Verified | `primer/` remains reference material in README and is not required pre-reading. |
| D-09 | Verified | No long primer content was moved into labs. |
| D-10 | Verified | README and source material index restrict source material use to continuity gaps. |
| D-11 | Verified | Word material remains source provenance, not final reader path. |
| D-12 | Verified | No broad Word migration was performed. |
| D-13 | Verified | `basic_operation/` is framed as lookup reference. |
| D-14 | Verified | README remains the main lookup index for `basic_operation/`. |
| D-15 | Verified | Labs keep detail links in `## 细化参考`. |
| D-16 | Verified | Detector tool usage is documented in labs and README. |
| D-17 | Verified | README explains detector commands, outputs, `device_simple.json`, and `tools/devices/images/`. |
| D-18 | Verified | README maps `tty` / `dev` to command placeholders and `by-id` / `by-path` to physical identity. |
| D-19 | Verified | Tool guidance is integrated into tutorial orientation, not a separate product. |

## Automated Checks

```bash
python3 -m py_compile tools/detect_system.py
python3 tools/detect_system.py --help
rg -n "评分|评价|rubric|提交要求" README.md labs basic_operation AGENTS.md
rg -n "## 主线位置|### 上一段产物|### 本段要完成|### 下一段会用到什么" labs
rg -n "## 参数来源|## 预期效果|## 练习记录|## 自检清单|## 细化参考" labs
rg -n "python3 tools/detect_system.py|--skip-capture|--format json|device_simple.json|tools/devices/images|capture_status|capture_detail" README.md labs basic_operation
```

Results:

- `py_compile` exited 0.
- `detect_system.py --help` shows `--format` and `--skip-capture`.
- The scope guard for `评分|评价|rubric|提交要求` returned no matches.
- Required tutorial continuity and tool guidance strings are present.
- Relative Markdown link check for touched Markdown files reported 0 missing links.

## Human Verification

No human verification is required for Phase 2 completion. Real hardware behavior and installed LeRobot command variants remain documented residual risks for Phase 3 and later quality gates.

## Residual Risk

- This phase did not run SO-101 hardware detection against physical devices.
- This phase did not rewrite LeRobot command names to match the latest upstream docs because local CLI verification is required before changing command forms.

## Verification Complete
