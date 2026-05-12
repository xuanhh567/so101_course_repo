# Repository Instructions

This repository is a GSD-managed tutorial project for SO-101 + LeRobot.

## Working Principles

- Preserve the tutorial path: `README.md -> labs/` as the main operational route.
- Treat `primer/` as concept reference material, not mandatory pre-reading.
- Treat `basic_operation/` as lookup/reference material, not a second main tutorial path.
- Treat `source_materials/` as source documents to be distilled into Markdown when useful.
- Keep commands copyable, but do not hide which placeholders students must change.
- Prefer relative Markdown links so the course can be moved between classroom machines.
- Treat `tools/detect_system.py` as classroom infrastructure: changes need manual hardware verification or a documented dry-run limitation.
- Do not commit Python caches, large generated datasets, LeRobot checkpoints, or local training outputs.
- Do not add non-tutorial workflow layers unless the project scope changes explicitly.

## GSD Workflow

- Project context lives in `.planning/PROJECT.md`.
- Requirements live in `.planning/REQUIREMENTS.md`.
- Phase roadmap lives in `.planning/ROADMAP.md`.
- Before implementation work, run the relevant GSD phase planning workflow from the roadmap.
