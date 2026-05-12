# Phase 1: Tutorial Foundation - Context

**Gathered:** 2026-05-12
**Status:** Ready for planning

<domain>
## Phase Boundary

This phase stabilizes the repository as a tutorial-only project. It locks the reader-facing structure, removes non-tutorial framing from the main path, and makes sure downstream phases plan from a tutorial architecture rather than a teaching-reform or evaluation architecture.

</domain>

<decisions>
## Implementation Decisions

### Tutorial Entry
- **D-01:** README should be a manual-style index, not a long narrative landing page. It should help readers find the tutorial path, concept references, operation references, tools, and source materials quickly.
- **D-02:** README should avoid turning into a course design document. The main value is navigation and orientation.

### Concept Primer Placement
- **D-03:** `primer/` should be appendix-like reference material. It should not be a mandatory gate before using `labs/`.
- **D-04:** Main tutorial steps may link to primer pages when a concept is needed, but the reader should be able to start from the operational path without reading all primer files first.

### Operation Reference Placement
- **D-05:** `basic_operation/` should remain as lookup reference material. It should not compete with `labs/` as a second main tutorial path.
- **D-06:** README and later plans should describe `basic_operation/` as "补查参考" or equivalent wording, not as required sequential reading.

### Source Materials
- **D-07:** `source_materials/` contains user-built source materials and must be treated as source references for extraction and refinement.
- **D-08:** Source Word documents should not dominate the README main path, but downstream agents should inspect them when improving tutorial content.
- **D-09:** If a Word source contains useful tutorial material, convert or distill it into Markdown tutorial files rather than merely linking to the Word file.

### the agent's Discretion
- The agent may choose exact README section names and ordering as long as the result stays index-like and preserves a clear tutorial path.
- The agent may choose whether source-material extraction belongs in Phase 1 or is noted for Phase 2, but it must not treat `source_materials/` as disposable archival noise.

</decisions>

<canonical_refs>
## Canonical References

**Downstream agents MUST read these before planning or implementing.**

### GSD Scope
- `.planning/PROJECT.md` — Locks tutorial-only project framing and explicitly excludes evaluation mechanisms.
- `.planning/REQUIREMENTS.md` — Defines Phase 1 requirements `TUT-01` through `TUT-04`.
- `.planning/ROADMAP.md` — Defines Phase 1 boundary and acceptance criteria.

### Current Tutorial Structure
- `README.md` — Current public entry point that must become a clean tutorial index.
- `AGENTS.md` — Repository maintenance rules that should protect the tutorial path.
- `.planning/codebase/STRUCTURE.md` — Current repository structure map.
- `.planning/codebase/CONVENTIONS.md` — Current documentation conventions; note that any stale submission/scoring language should be revised toward tutorial language.
- `.planning/codebase/CONCERNS.md` — Known concerns, including source-language drift and generated-device-output handling.

### Source Materials To Distill
- `source_materials/预实验：LeRobot 环境创建.docx` — User-built source for environment setup tutorial material.
- `source_materials/模块一：物理基座构建与遥操作.docx` — User-built source for physical base and teleoperation material.
- `source_materials/实验一：物理基座构建与遥操作.docx` — User-built source for lab/tutorial material around hardware setup and teleoperation.
- `source_materials/实验二：专家示范与高质量数据工程.docx` — User-built source for data demonstration and dataset engineering material.

</canonical_refs>

<code_context>
## Existing Code Insights

### Reusable Assets
- `README.md`: Primary navigation surface for Phase 1.
- `labs/`: Main tutorial path that should remain the operational route.
- `primer/`: Concept references that should be linked when useful, not treated as a required pre-course.
- `basic_operation/`: Detailed operation references for troubleshooting and lookup.
- `source_materials/`: Source corpus for later tutorial extraction and refinement.

### Established Patterns
- Chinese is the primary tutorial language.
- LeRobot commands should remain copyable fenced shell blocks.
- Placeholder values should be explained near the commands that use them.
- Role names should remain consistent: `leader`, `follower`, `top_camera`, `wrist_camera`, optional `side_camera`.

### Integration Points
- README links into `primer/`, `labs/`, `basic_operation/`, `tools/`, and `source_materials/`.
- GSD planning must continue from tutorial-only scope and should not reintroduce grading or teaching-reform packaging.

</code_context>

<specifics>
## Specific Ideas

- User selected README as a manual/index style entry point.
- User selected `primer/` as appendix-like material.
- User selected `basic_operation/` as lookup reference.
- User clarified that Word files were hand-built source materials and should be referenced and distilled.

</specifics>

<deferred>
## Deferred Ideas

None — discussion stayed within phase scope.

</deferred>

---

*Phase: 1-Tutorial Foundation*
*Context gathered: 2026-05-12*
