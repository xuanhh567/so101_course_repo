# Stack

## Runtime

- Python 3 script for classroom device detection: `tools/detect_system.py`.
- LeRobot CLI is the operational dependency used by course commands, including `lerobot-calibrate`, `lerobot-teleoperate`, `lerobot-record`, `lerobot-replay`, `lerobot-train`, and `lerobot-rollout`.
- Linux hardware interfaces are assumed: `/dev/ttyACM*`, `/dev/serial/by-id`, `/dev/video*`, `/dev/v4l/by-id`, and `/dev/v4l/by-path`.

## System Tools

- `v4l2-ctl` is used when available for camera metadata and formats.
- `ffprobe` is used when available for stream probing.
- `ffmpeg` is used when available for camera screenshots.

## Content Format

- Student and teacher materials are Markdown-first.
- Original Word documents are preserved in `source_materials/` as source/reference material.
- GSD planning artifacts are Markdown and JSON under `.planning/`.

## Constraints

- The course is tightly coupled to real SO-101 classroom hardware and LeRobot command behavior.
- The detector must degrade gracefully when optional system tools are missing.
- Absolute local paths reduce portability and should be avoided in course materials.
