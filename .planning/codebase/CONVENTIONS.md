# Conventions

## Documentation

- Chinese is the primary instructional language.
- Keep the student path direct and operational.
- `README.md` is an index-style entry for navigation and orientation.
- `labs/` is the main operational tutorial path.
- `primer/` is concept reference material.
- `basic_operation/` is lookup reference material.
- Each lab should contain: goal, prerequisites, steps, placeholders to modify, expected outcomes, practice records, and self-checks.
- Use role names consistently: `leader`, `follower`, `top_camera`, `wrist_camera`, and optional `side_camera`.

## Commands

- Keep LeRobot commands as fenced shell blocks.
- Use angle-bracket placeholders for student-specific values, such as `<FOLLOWER_PORT>` and `<DATASET_REPO_ID>`.
- Explain where each placeholder value comes from before asking students to execute the command.

## Python

- The detector is a single-file script with standard library first.
- Optional dependencies are checked through `shutil.which`.
- Failures should be reported as status/detail fields rather than crashing during class.
