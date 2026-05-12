---
phase: 01-tutorial-foundation
plan: 02
subsystem: maintenance-conventions
tags: [documentation, conventions, gsd]
key-files:
  created:
    - .planning/phases/01-tutorial-foundation/01-02-SUMMARY.md
  modified:
    - AGENTS.md
    - .planning/codebase/CONVENTIONS.md
metrics:
  tasks_completed: 2
  verification_passed: true
---

# Summary: Plan 02 - Maintenance Conventions

## What Changed

- Strengthened `AGENTS.md` to protect the tutorial-only architecture.
- Clarified `README.md -> labs/` as the main operational route.
- Clarified `primer/`, `basic_operation/`, and `source_materials/` roles.
- Updated `.planning/codebase/CONVENTIONS.md` to remove stale submission/scoring expectations.
- Replaced stale convention language with practice records and self-checks.

## Tasks

| Task | Status | Files |
|------|--------|-------|
| Strengthen tutorial-only maintenance instructions | Complete | `AGENTS.md` |
| Fix stale documentation conventions | Complete | `.planning/codebase/CONVENTIONS.md` |

## Verification

- PASS: `rg -n 'README.md -> labs/|primer/|basic_operation/|source_materials/|non-tutorial workflow layers' AGENTS.md`.
- PASS: `rg -n 'practice records|self-checks|index-style|lookup reference' .planning/codebase/CONVENTIONS.md`.
- PASS: `rg -n 'submission requirements|scoring points|评分|评价|rubric|提交要求' .planning/codebase/CONVENTIONS.md` exits 1.
- PASS: `python3 -m py_compile tools/detect_system.py`.

## Deviations from Plan

None - plan executed exactly as written.

## Self-Check: PASSED

All acceptance criteria passed and no unrelated files were modified.
