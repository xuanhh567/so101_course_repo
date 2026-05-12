---
phase: 01-tutorial-foundation
plan: 01
subsystem: tutorial-entry
tags: [documentation, tutorial, source-materials]
key-files:
  created:
    - source_materials/README.md
    - .planning/phases/01-tutorial-foundation/01-01-SUMMARY.md
  modified:
    - README.md
metrics:
  tasks_completed: 2
  verification_passed: true
---

# Summary: Plan 01 - Public Tutorial Index

## What Changed

- Reworked `README.md` into a compact tutorial index.
- Made `labs/` the main operational path.
- Repositioned `primer/` as concept reference material.
- Repositioned `basic_operation/` as operation lookup material.
- Added `source_materials/README.md` to describe the hand-built Word sources and the extraction direction.

## Tasks

| Task | Status | Files |
|------|--------|-------|
| Rework README as tutorial index | Complete | `README.md` |
| Add source materials index | Complete | `source_materials/README.md` |

## Verification

- PASS: `rg -n '评分|评价|rubric|提交要求' README.md` exits 1.
- PASS: `rg -n '## 主线教程|## 概念参考|## 操作补查|## 来源材料' README.md`.
- PASS: `rg -n '/home/xuan/so101_education|/home/xuan/Documents' README.md source_materials/README.md` exits 1.
- PASS: `test -s source_materials/README.md`.
- PASS: all four Word source filenames are listed in `source_materials/README.md`.
- PASS: local Markdown links in `README.md` and `source_materials/README.md` resolve.

## Deviations from Plan

None - plan executed exactly as written.

## Self-Check: PASSED

All acceptance criteria passed and no unrelated files were modified.
