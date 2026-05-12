---
phase: 02-tutorial-flow-hardening
plan: 02-02
subsystem: docs
tags: [tutorial, readme, tools, source-materials, lookup-reference]
requires:
  - phase: 02-tutorial-flow-hardening
    provides: Plan 02-01 normalized the three main labs
provides:
  - README tool usage guidance
  - README-centered lookup reference positioning
  - Phase 2 source-material boundary
affects: [README, basic_operation, source_materials]
tech-stack:
  added: []
  patterns: [index-style-readme, lookup-reference-layer, selective-source-extraction]
key-files:
  created:
    - .planning/phases/02-tutorial-flow-hardening/02-02-SUMMARY.md
  modified:
    - README.md
    - basic_operation/00_command_template_guide.md
    - source_materials/README.md
key-decisions:
  - "README remains the main tutorial index and documents each lab's output."
  - "README explains tools/detect_system.py commands, output files, and key device fields."
  - "basic_operation/00 is explicitly framed as lookup support for labs."
  - "source_materials/README documents Phase 2 selective-use boundaries."
patterns-established:
  - "README core tool guidance explains command purpose, output files, and field mappings."
  - "Source materials are provenance for selective extraction, not reader-facing path."
requirements-completed:
  - CONT-01
  - CONT-03
  - CONT-04
duration: 0 min
completed: 2026-05-12
---

# Phase 02 Plan 02-02: Harden README Tool Guidance And Reference Layers Summary

**README now explains the three-lab outputs, detector tool usage, lookup reference role, and selective Word-source boundary**

## Performance

- **Duration:** 0 min
- **Started:** 2026-05-12T00:00:00Z
- **Completed:** 2026-05-12T00:00:00Z
- **Tasks:** 5
- **Files modified:** 3

## Accomplishments

- Added a `每段产物` summary to README so the three labs read as one path.
- Expanded README's `## 核心工具` section with `detect_system.py` command purposes and field mappings.
- Clarified that `basic_operation/` is a lookup layer and readers should return to the current lab.
- Added `## Phase 2 使用边界` to `source_materials/README.md`.
- Verified relative Markdown links in touched files.

## Task Commits

Plan work was committed together:

1. **Tasks 02-02-01 through 02-02-05: Harden tutorial references** - `bd28456` (docs)

## Files Created/Modified

- `README.md` - Adds lab outputs, detector command explanations, field guide, lookup reminder, and source-material boundary sentence.
- `basic_operation/00_command_template_guide.md` - Adds relation to `README.md -> labs/` main route.
- `source_materials/README.md` - Adds Phase 2 selective-use boundary.

## Decisions Made

- Kept README concise and index-like while adding enough tool detail for readers to use `tools/detect_system.py`.
- Kept detailed command rewriting in `basic_operation/00_command_template_guide.md`.

## Deviations from Plan

Combined the five documentation tasks into one commit because the edits were small, tightly coupled, and verified together. No scope change.

**Total deviations:** 1 procedural deviation.
**Impact on plan:** Content requirements and verification gates were still satisfied.

## Issues Encountered

None.

## User Setup Required

None - no external service configuration required.

## Self-Check: PASSED

- `python3 -m py_compile tools/detect_system.py` exits 0.
- `python3 tools/detect_system.py --help` contains `--format` and `--skip-capture`.
- `rg -n "评分|评价|rubric|提交要求" README.md labs basic_operation AGENTS.md` returns no matches.
- `rg -n "上一段产物|本段要完成|下一段会用到什么" labs` returns all three lab files.
- `rg -n "python3 tools/detect_system.py|--skip-capture|--format json|device_simple.json|tools/devices/images|capture_status|capture_detail" README.md labs basic_operation` returns required tool guidance.
- Markdown relative-link check reports 0 missing links for touched Markdown files.

## Next Phase Readiness

Phase 2 content is ready for phase-level verification. Phase 3 can focus on detector reliability without needing to reframe the tutorial route.

---
*Phase: 02-tutorial-flow-hardening*
*Completed: 2026-05-12*
