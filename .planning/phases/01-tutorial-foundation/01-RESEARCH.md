# Phase 1: Tutorial Foundation - Research

**Phase:** 01 Tutorial Foundation
**Date:** 2026-05-12
**Status:** Complete

## Research Question

What does the planner need to know to stabilize this repository as a tutorial-only project without accidentally rebuilding the broader teaching-reform/evaluation structure?

## Findings

### 1. Phase 1 should stabilize navigation, not rewrite tutorial content

Phase 1 is a foundation pass. The important outcome is not fuller tutorial prose; it is a clear information architecture that later phases can trust.

Implications:
- README should become a compact manual-style index.
- `labs/` remains the main operational path.
- `primer/` becomes concept reference material.
- `basic_operation/` becomes lookup reference material.
- `source_materials/` is explicitly source material for later extraction.

### 2. Source materials need first-class reference status without dominating the reader path

The user clarified that the Word documents were hand-built source materials and must be used for reference and extraction. They should not be treated as disposable archive, but also should not become the main entry point.

Best Phase 1 handling:
- Add a small `source_materials/README.md` that explains each source document's role.
- Link to that source index from README in a "source materials" section.
- Defer actual extraction into Markdown tutorial content to Phase 2 unless a tiny clarification is needed for navigation.

### 3. Current codebase maps contain stale course/evaluation language

`.planning/codebase/CONVENTIONS.md` still says each lab should contain "submission requirements and scoring points." That conflicts with the tutorial-only scope and can mislead future agents.

Phase 1 should update codebase-map conventions so future plans do not reintroduce evaluation framing.

### 4. Acceptance should be grep-verifiable

This phase is documentation architecture, so verification should use deterministic text checks:
- README contains index-style section names.
- README does not contain `评分`, `评价`, `rubric`, or `提交要求`.
- README refers to `primer/` as reference or concept material, not mandatory pre-reading.
- README refers to `basic_operation/` as lookup/reference material.
- `source_materials/README.md` exists and lists all four Word files.
- `AGENTS.md` protects the tutorial path and avoids non-tutorial workflow layers.
- `.planning/codebase/CONVENTIONS.md` no longer mentions submission/scoring as required lab structure.

## Recommended Plan Split

### Plan 01: Public tutorial index

Modify:
- `README.md`
- `source_materials/README.md`

Purpose:
- Make README a manual-style index.
- Make source materials visible as references without making them the main path.

### Plan 02: Maintenance conventions

Modify:
- `AGENTS.md`
- `.planning/codebase/CONVENTIONS.md`

Purpose:
- Lock maintenance rules against reintroducing non-tutorial layers.
- Fix stale codebase-map language that still points toward submission/scoring.

## Validation Architecture

### Automated Checks

Use shell/grep checks only; no new framework is needed for Phase 1.

Required checks:
- `python3 -m py_compile tools/detect_system.py`
- local Markdown link resolver script exits 0
- `rg -n '评分|评价|rubric|提交要求' README.md labs basic_operation AGENTS.md` exits 1
- `test -s source_materials/README.md`
- `rg -n '预实验：LeRobot 环境创建.docx|模块一：物理基座构建与遥操作.docx|实验一：物理基座构建与遥操作.docx|实验二：专家示范与高质量数据工程.docx' source_materials/README.md`

### Manual Checks

None required for Phase 1. This phase changes documentation structure only.

## Planning Notes

- Keep both plans autonomous.
- Avoid extracting Word content in Phase 1 beyond source-indexing.
- Do not modify `labs/` content unless a future checker finds non-tutorial language in the public path.
- Do not run hardware detection as part of Phase 1 verification.

## RESEARCH COMPLETE
