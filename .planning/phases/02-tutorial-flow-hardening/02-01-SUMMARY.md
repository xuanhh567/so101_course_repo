---
phase: 02-tutorial-flow-hardening
plan: 02-01
subsystem: docs
tags: [tutorial, labs, lerobot, so101, detector]
requires:
  - phase: 01-tutorial-foundation
    provides: Tutorial-only repository framing and main path conventions
provides:
  - Connected three-lab tutorial sequence
  - Normalized lab section headings
  - Detector usage guidance inside lab steps
affects: [labs, primer, basic_operation, tools]
tech-stack:
  added: []
  patterns: [continuity-blocks, parameter-source-sections, tutorial-self-checks]
key-files:
  created:
    - .planning/phases/02-tutorial-flow-hardening/02-01-SUMMARY.md
  modified:
    - labs/01_lab_env_mapping_calibration.md
    - labs/02_lab_teleop_record_replay.md
    - labs/03_lab_act_train_deploy.md
key-decisions:
  - "Labs use 主线位置 blocks to connect previous output, current work, and next usage."
  - "参数来源 and 预期效果 replace older parameter/effect headings."
  - "Detector tool guidance is included where command parameters depend on device scan output."
patterns-established:
  - "Each main lab begins with 主线位置 / 上一段产物 / 本段要完成 / 下一段会用到什么."
  - "Each main lab has 参数来源 and 预期效果 sections with placeholder source explanations."
requirements-completed:
  - CONT-01
  - CONT-02
  - CONT-03
duration: 0 min
completed: 2026-05-12
---

# Phase 02 Plan 02-01: Normalize And Connect The Three Main Labs Summary

**Three main labs now expose a continuous SO-101 + LeRobot tutorial path with parameter-source and detector-output guidance**

## Performance

- **Duration:** 0 min
- **Started:** 2026-05-12T00:00:00Z
- **Completed:** 2026-05-12T00:00:00Z
- **Tasks:** 5
- **Files modified:** 3

## Accomplishments

- Added `## 主线位置` continuity blocks to all three main labs.
- Normalized parameter/effect headings to `## 参数来源` and `## 预期效果`.
- Added short concept bridge notes while keeping `primer/` as reference material.
- Added detector tool guidance for `--skip-capture`, `--format json`, `capture_status`, `capture_detail`, and latest `device_simple.json` usage.

## Task Commits

Plan work was committed together:

1. **Tasks 02-01-01 through 02-01-05: Normalize main labs** - `65b98a6` (docs)

## Files Created/Modified

- `labs/01_lab_env_mapping_calibration.md` - Adds first-lab continuity, physical-role note, detector options, and parameter-source wording.
- `labs/02_lab_teleop_record_replay.md` - Adds second-lab continuity, observation/action/replay note, screenshot status fields, and parameter-source wording.
- `labs/03_lab_act_train_deploy.md` - Adds final-lab continuity, ACT/checkpoint/rollout note, fresh detector guidance, and parameter-source wording.

## Decisions Made

- Kept detailed lookup references at the end of each lab instead of making `basic_operation/` a required path.
- Used short in-lab concept notes rather than copying long primer explanations into the lab body.

## Deviations from Plan

Combined the five documentation tasks into one commit because the edits touched the same three Markdown files and were easier to verify as one coherent lab-template pass. No scope change.

**Total deviations:** 1 procedural deviation.
**Impact on plan:** Content requirements and verification gates were still satisfied.

## Issues Encountered

None.

## User Setup Required

None - no external service configuration required.

## Self-Check: PASSED

- `rg -n "## 主线位置|### 上一段产物|### 本段要完成|### 下一段会用到什么" labs` returns required continuity headings.
- `rg -n "## 参数来源|## 预期效果|## 练习记录|## 自检清单|## 细化参考" labs` returns required lab sections.
- `rg -n "评分|评价|rubric|提交要求" labs README.md basic_operation AGENTS.md` returns no matches.
- `python3 -m py_compile tools/detect_system.py` exits 0.

## Next Phase Readiness

Wave 2 can update README, the command-template lookup guide, and source-material boundary text against the normalized lab structure.

---
*Phase: 02-tutorial-flow-hardening*
*Completed: 2026-05-12*
