# Phase 1: Tutorial Foundation - Discussion Log

> **Audit trail only.** Do not use as input to planning, research, or execution agents.
> Decisions are captured in CONTEXT.md — this log preserves the alternatives considered.

**Date:** 2026-05-12
**Phase:** 1-Tutorial Foundation
**Areas discussed:** Tutorial entry, Primer placement, Operation reference placement, Source materials

---

## Tutorial Entry

| Option | Description | Selected |
|--------|-------------|----------|
| 快速上手型 | 直接告诉读者按 1-2-3 做，少讲背景 | |
| 学习路径型 | 先解释为什么这样学，再进入三段教程 | |
| 手册索引型 | README 主要做目录，具体内容放到各章节 | ✓ |

**User's choice:** 1C
**Notes:** README should behave as an index/manual entry rather than a long course-design narrative.

---

## Primer Placement

| Option | Description | Selected |
|--------|-------------|----------|
| 必读前置 | 先读 primer，再做 labs | |
| 边做边查 | labs 中按需链接 primer | |
| 附录化 | 主线尽量不依赖 primer | ✓ |

**User's choice:** 2C
**Notes:** `primer/` should support the tutorial as reference material, not block entry into the main operational path.

---

## Operation Reference Placement

| Option | Description | Selected |
|--------|-------------|----------|
| 补查参考 | 保留，但 README 明确它不是主线 | ✓ |
| 合并回 labs | 把关键内容并入三段教程 | |
| 进阶细节 | 只给读者深入理解时看 | |

**User's choice:** 3A
**Notes:** `basic_operation/` remains useful, but should not compete with `labs/` as the main tutorial path.

---

## Source Materials

| Option | Description | Selected |
|--------|-------------|----------|
| 只保留归档 | 不在 README 主路径出现 | |
| 来源说明 | README 简短提及 | |
| 逐步吸收 | 后续逐步吸收进 Markdown 教程 | |
| 参照提炼 | 这些是用户手工搭建的材料，需要参照并提炼 | ✓ |

**User's choice:** 4e: 这些是我手工搭建的，需要你参照提炼
**Notes:** `source_materials/` is not disposable archive. It is a source corpus for improving the Markdown tutorial.

---

## the agent's Discretion

- Exact README section names and ordering.
- Whether source-material extraction is done in Phase 1 or prepared for Phase 2, as long as the source corpus is treated as canonical reference material.

## Deferred Ideas

None.
