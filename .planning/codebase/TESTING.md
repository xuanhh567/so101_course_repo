# Testing

## Current State

There is no automated test suite yet.

## Manual Verification Already Implied

- Run `python3 tools/detect_system.py`.
- Confirm `tools/devices/device_simple.json` is written.
- Confirm camera screenshots are saved when `ffmpeg` and cameras are available.
- Confirm generated device values can be used to rewrite LeRobot commands.

## Needed Tests

- Unit tests for parsing `v4l2-ctl` output.
- Unit tests for stable symlink selection.
- Unit tests for camera color-stream inference.
- Dry-run or fixture tests for JSON output shape.
- Markdown checks for broken relative links and stale absolute paths.
- Command placeholder linting to ensure every placeholder is explained in the same lab.

## Hardware Verification

Automated tests cannot replace classroom hardware checks. Detector changes should document whether they were verified with real SO-101 arms and cameras.
