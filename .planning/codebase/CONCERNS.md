# Concerns

## High Priority

- No automated checks protect Markdown links, command placeholders, or detector output shape.
- `tools/devices/device_simple.json` is both generated output and teaching evidence, which can create noisy Git changes after each classroom scan.
- The Word source materials are preserved but not yet reconciled against the Markdown labs.

## Medium Priority

- Course materials are classroom-ready but not publication-ready: no site build, printable package, release checklist, or teacher handoff bundle.
- Scoring criteria exist inside labs but are not normalized into reusable rubrics.
- Detector behavior depends on optional Linux tools and available hardware; fallback behavior needs fixture coverage.

## Low Priority

- The repository has no package metadata because it is not currently distributed as a Python package.
- Some generated screenshots may reveal local classroom hardware state; release policy should decide whether to keep sample screenshots or replace them with anonymized examples.
