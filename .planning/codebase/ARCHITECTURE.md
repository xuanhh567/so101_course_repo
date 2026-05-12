# Architecture

## Current Shape

This is a documentation-and-tooling repository, not a packaged software application.

- `README.md` is the student entry point.
- `primer/` provides conceptual preparation.
- `labs/` provides the three-session classroom path.
- `basic_operation/` preserves detailed reference chapters for teachers and student lookup.
- `tools/detect_system.py` produces the hardware evidence students use to rewrite LeRobot commands.
- `source_materials/` stores original Word documents for traceability.

## Core Flow

1. Student reads the course map and relevant primer.
2. Student runs `python3 tools/detect_system.py`.
3. Student uses `tools/devices/device_simple.json` and camera screenshots to identify current ports and camera roles.
4. Student rewrites LeRobot command placeholders.
5. Student completes calibration, teleoperation, recording, replay, training, and rollout across three labs.

## Architectural Gap

The repository has a clear learning path but no build/release layer yet. There is no generated website, no printable handout pipeline, no command validation tests, and no structured rubric package for teachers.
