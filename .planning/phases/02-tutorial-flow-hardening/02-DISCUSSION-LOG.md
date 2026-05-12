# Phase 2: Tutorial Flow Hardening - Discussion Log

> **Audit trail only.** Do not use as input to planning, research, or execution agents.
> Decisions are captured in CONTEXT.md — this log preserves the alternatives considered.

**Date:** 2026-05-12
**Phase:** 2-Tutorial Flow Hardening
**Areas discussed:** Main lab continuity, unified lab template, primer placement, source material extraction, operation reference placement, tools usage guidance

---

## Main Lab Continuity

| Option | Description | Selected |
|--------|-------------|----------|
| A | Each lab includes previous output, current goal, and next usage so the three labs form a continuous chain. | ✓ |
| B | Keep ordering mainly in README while labs remain mostly independent. | |
| C | Add one overall flow guide while keeping the three labs relatively independent. | |

**User's choice:** 1A
**Notes:** The three main tutorials should read as one connected tutorial rather than scattered lab sheets.

---

## Unified Lab Template

| Option | Description | Selected |
|--------|-------------|----------|
| A | Normalize every lab to goal, preparation, steps, parameter sources, expected effects, practice records, and self-checklist. | ✓ |
| B | Use a shorter action-first template with less reading. | |
| C | Use a troubleshooting-heavy template in every lab. | |

**User's choice:** 2A
**Notes:** Template language must remain tutorial-oriented. Practice records and self-checklists are not assessment mechanisms.

---

## Primer Placement

| Option | Description | Selected |
|--------|-------------|----------|
| A | Labs include short concept notes and link to `primer/` for deeper reading. | ✓ |
| B | Labs only link out to `primer/` without concept explanation. | |
| C | Move key concept summaries directly into labs to reduce jumping. | |

**User's choice:** 3A
**Notes:** `primer/` remains reference material, not required pre-reading.

---

## Source Material Extraction

| Option | Description | Selected |
|--------|-------------|----------|
| A | Extract only content that fixes continuity gaps in the three labs. | ✓ |
| B | Fully review Word sources and produce an extraction list, with limited body changes. | |
| C | Migrate as much useful Word content as possible into Markdown now. | |

**User's choice:** 4A
**Notes:** Word source materials are user-built references, but they should not dominate this phase.

---

## Operation Reference Placement

| Option | Description | Selected |
|--------|-------------|----------|
| A | Add "if X, check Y" lookup hints in important lab steps. | |
| B | Keep the `basic_operation/` lookup relationship primarily in README, with labs less interrupted. | ✓ |
| C | Put related lookup chapters at the end of each lab. | |

**User's choice:** 5B
**Notes:** `basic_operation/` should remain a lookup layer and should not become a second main path.

---

## Tools Usage Guidance

| Option | Description | Selected |
|--------|-------------|----------|
| Required | Add clear usage instructions for repository tools, especially detector usage and output interpretation. | ✓ |

**User's choice:** Free-text addition: "我要有我的tools的使用的说明"
**Notes:** This fits Phase 2 because the detector output is part of the tutorial flow and command parameter source explanation.

## the agent's Discretion

- Choose exact section titles and phrasing that keep the labs readable.
- Choose where short concept notes help and where a simple primer link is enough.
- Add minimal README wording for tool usage if it improves the flow.

## Deferred Ideas

- Broad automation for full Word extraction remains outside Phase 2 and can stay in v2 automation scope.
