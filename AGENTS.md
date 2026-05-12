# Repository Instructions

This repository is a GSD-managed teaching reform project for an SO-101 + LeRobot course.

## Working Principles

- Preserve the student-facing path: `README.md` -> `primer/` -> `labs/`.
- Keep commands copyable, but do not hide which placeholders students must change.
- Prefer relative Markdown links so the course can be moved between classroom machines.
- Treat `tools/detect_system.py` as classroom infrastructure: changes need manual hardware verification or a documented dry-run limitation.
- Do not commit Python caches, large generated datasets, LeRobot checkpoints, or local training outputs.

## GSD Workflow

- Project context lives in `.planning/PROJECT.md`.
- Requirements live in `.planning/REQUIREMENTS.md`.
- Phase roadmap lives in `.planning/ROADMAP.md`.
- Before implementation work, run the relevant GSD phase planning workflow from the roadmap.
