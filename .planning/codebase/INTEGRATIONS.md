# Integrations

## LeRobot

The repository teaches LeRobot workflows rather than wrapping LeRobot in an application. The integration surface is the set of CLI commands embedded in `labs/` and `basic_operation/`.

## Linux Device Discovery

`tools/detect_system.py` integrates directly with Linux device paths:

- Serial devices for SO-101 leader/follower arms.
- Video4Linux devices for top/wrist camera discovery.
- Stable symlink directories for identity hints.

## Camera Capture

The detector saves screenshots under `tools/devices/images/` to support manual camera role assignment. This is essential because camera names alone are not enough to distinguish `top_camera` and `wrist_camera` in a classroom.

## Source Materials

Word documents in `source_materials/` are retained for comparison with the Markdown course. They are not yet integrated into an automated build or publishing pipeline.
