# Phase 2: Tutorial Flow Hardening - Context

**Gathered:** 2026-05-12
**Status:** Ready for planning

<domain>
## Phase Boundary

This phase hardens the three `labs/` tutorials into one continuous tutorial flow. It should make each lab read as part of the same minimum SO-101 + LeRobot loop: environment and device mapping, calibration, teleoperation and data capture, ACT training, then policy deployment.

This phase does not add evaluation mechanisms, grading, course assessment, or a second main tutorial path. It clarifies the reader-facing tutorial sequence and strengthens the handoff between existing documentation layers.

</domain>

<decisions>
## Implementation Decisions

### Main Lab Continuity
- **D-01:** Each `labs/` page should explicitly show how it connects to the previous and next tutorial segment.
- **D-02:** Each lab should include a short continuity block such as "上一段产物", "本段要完成", and "下一段会用到什么" so the three labs form a readable chain.
- **D-03:** The main path remains `README.md -> labs/`. Do not add a new competing main route.

### Unified Lab Template
- **D-04:** Each lab should be normalized to the full tutorial template: goal, preparation, steps, parameter sources, expected effects, practice records, and self-checklist.
- **D-05:** The template should serve tutorial clarity, not assessment. "练习记录" and "自检清单" are for the reader's own traceability and troubleshooting, not scoring.
- **D-06:** Command placeholders must be explained near the commands that use them, especially where values come from `device_simple.json`, serial ports, camera paths, dataset IDs, or checkpoint paths.

### Concept Primer Placement
- **D-07:** Labs may include brief concept notes where a concept affects an operation, then link to the relevant `primer/` page for deeper reading.
- **D-08:** `primer/` should remain concept reference material and should not become mandatory pre-reading before starting the labs.
- **D-09:** Do not move long conceptual explanations into the lab body unless the concept is necessary to complete that exact operation.

### Source Material Extraction
- **D-10:** `source_materials/` should be used only to fill continuity gaps in the three labs during this phase.
- **D-11:** Useful Word material should be distilled into Markdown tutorial text, not linked as the final reading path.
- **D-12:** Avoid broad migration of all Word content in Phase 2. Full source-material extraction can remain a later automation or documentation task if needed.

### Operation Reference Placement
- **D-13:** `basic_operation/` remains lookup reference material, not a second main path.
- **D-14:** For Phase 2, the primary `basic_operation/` relationship should be maintained through the README reference index rather than frequent inline interruptions in every lab.
- **D-15:** Labs may link to a `basic_operation/` page when a detail is essential to avoid reader failure, but the lab should still be complete enough to follow sequentially.

### Tools Usage Guidance
- **D-16:** The tutorial must include clear usage guidance for the repo's tools, especially `tools/detect_system.py`.
- **D-17:** The tool guidance should explain when to run the detector in the tutorial flow, what files it produces, and how to interpret `tools/devices/device_simple.json` and `tools/devices/images/`.
- **D-18:** The tool guidance should connect detector output to LeRobot command parameters: current `tty` / `dev` values are used in commands, while `by-id` / `by-path` help identify physical devices.
- **D-19:** Tool usage should be integrated into the relevant lab steps and README orientation, not treated as a separate tooling product or evaluation mechanism.

### the agent's Discretion
- The agent may choose the exact section titles used inside each lab as long as the required tutorial roles are present and readable.
- The agent may decide where a short primer note is helpful versus where a link alone is enough.
- The agent may add minimal README wording to clarify tool usage and lookup references when it improves the Phase 2 flow.

</decisions>

<canonical_refs>
## Canonical References

**Downstream agents MUST read these before planning or implementing.**

### GSD Scope
- `.planning/PROJECT.md` — Locks the tutorial-only project framing and excludes evaluation mechanisms.
- `.planning/REQUIREMENTS.md` — Defines Phase 2 requirements `CONT-01` through `CONT-04`.
- `.planning/ROADMAP.md` — Defines the Phase 2 boundary, work items, and acceptance criteria.
- `.planning/phases/01-tutorial-foundation/01-CONTEXT.md` — Locks Phase 1 decisions about README, `labs/`, `primer/`, `basic_operation/`, and `source_materials/`.

### Current Tutorial Entry And Structure
- `README.md` — Current public entry and main route index.
- `.planning/codebase/CONVENTIONS.md` — Defines documentation conventions for labs, commands, placeholders, and role names.
- `.planning/codebase/STRUCTURE.md` — Maps existing tutorial files and their intended roles.
- `AGENTS.md` — Repository maintenance rules that protect the tutorial main path.

### Main Tutorial Path
- `labs/01_lab_env_mapping_calibration.md` — First main lab: environment, device mapping, and calibration.
- `labs/02_lab_teleop_record_replay.md` — Second main lab: teleoperation, recording, and replay.
- `labs/03_lab_act_train_deploy.md` — Third main lab: ACT training and policy deployment.

### Concept And Lookup References
- `primer/00_course_map.md` — Course chain and learning model.
- `primer/01_so101_intro.md` — SO-101 concept reference.
- `primer/02_lerobot_intro.md` — LeRobot concept reference.
- `primer/03_embodied_data_intro.md` — Data collection concept reference.
- `primer/04_act_intro.md` — ACT concept reference.
- `basic_operation/00_command_template_guide.md` — Placeholder and command rewriting reference.
- `basic_operation/01_environment_setup.md` — Environment setup lookup.
- `basic_operation/02_arm_detection.md` — Device mapping lookup.
- `basic_operation/02a_device_roles_filling_guide.md` — Device role filling guide.
- `basic_operation/03_calibration.md` — Calibration lookup.
- `basic_operation/04_teleoperation.md` — Teleoperation lookup.
- `basic_operation/05_dataset_recording.md` — Dataset recording lookup.
- `basic_operation/06_act_training.md` — ACT training lookup.
- `basic_operation/07_policy_deployment.md` — Policy deployment lookup.

### Tools And Generated Outputs
- `tools/detect_system.py` — Detector tool whose usage must be explained in the tutorial flow.
- `tools/devices/device_simple.json` — Detector output used to map current command parameters.
- `tools/devices/images/` — Detector screenshots used to identify camera roles.

### Source Materials To Distill Selectively
- `source_materials/README.md` — Source material index.
- `source_materials/预实验：LeRobot 环境创建.docx` — Source for environment setup details.
- `source_materials/模块一：物理基座构建与遥操作.docx` — Source for physical base and teleoperation details.
- `source_materials/实验一：物理基座构建与遥操作.docx` — Source for hardware setup and teleoperation tutorial material.
- `source_materials/实验二：专家示范与高质量数据工程.docx` — Source for data demonstration and dataset engineering material.

</canonical_refs>

<code_context>
## Existing Code Insights

### Reusable Assets
- `README.md`: Already presents the main route, concept references, operation references, tool commands, practice records, and source materials.
- `labs/`: Existing three-part main tutorial path to normalize and connect.
- `primer/`: Existing concept reference layer that can receive links from lab-level short notes.
- `basic_operation/`: Existing detail reference layer for lookup via README and occasional essential lab links.
- `tools/detect_system.py`: Existing command-line helper that creates concrete hardware mapping outputs for tutorial commands.
- `source_materials/`: Existing source corpus for selective extraction when lab continuity is missing.

### Established Patterns
- Chinese is the primary instructional language.
- LeRobot commands should remain copyable fenced shell blocks.
- Angle-bracket placeholders such as `<FOLLOWER_PORT>` and `<DATASET_REPO_ID>` should be explained before execution.
- Role names should remain consistent: `leader`, `follower`, `top_camera`, `wrist_camera`, optional `side_camera`.
- Reader records are framed as practice records and self-checks, not scoring.

### Integration Points
- README should continue to orient readers without becoming a long course-design document.
- Each lab should expose the values it produces for the next lab, such as device mapping, calibrated arms, dataset outputs, or checkpoint paths.
- Tool output from `tools/detect_system.py` should connect directly to device mapping and command parameter instructions.
- Source-material extraction should only modify Markdown tutorial files when it improves the sequential lab path.

</code_context>

<specifics>
## Specific Ideas

- User selected a connected three-lab sequence with explicit previous/current/next handoffs.
- User selected the full lab template: goal, preparation, steps, parameter sources, expected effects, practice records, and self-checklist.
- User selected short concept notes in labs with links back to `primer/`.
- User selected selective source-material extraction only where it improves tutorial continuity.
- User selected README-centered `basic_operation/` lookup positioning.
- User explicitly requested usage instructions for the repo's tools.

</specifics>

<deferred>
## Deferred Ideas

None — discussion stayed within Phase 2 scope. Broad automation for full Word extraction remains covered by v2 automation requirements rather than this phase.

</deferred>

---

*Phase: 2-Tutorial Flow Hardening*
*Context gathered: 2026-05-12*
