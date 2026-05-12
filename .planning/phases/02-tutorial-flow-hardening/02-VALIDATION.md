---
phase: 02
slug: tutorial-flow-hardening
status: draft
nyquist_compliant: true
wave_0_complete: true
created: 2026-05-12
---

# Phase 02 — Validation Strategy

> Per-phase validation contract for feedback sampling during execution.

---

## Test Infrastructure

| Property | Value |
|----------|-------|
| **Framework** | shell + Python standard library |
| **Config file** | none |
| **Quick run command** | `python3 -m py_compile tools/detect_system.py` |
| **Full suite command** | `python3 -m py_compile tools/detect_system.py && rg -n "评分|评价|rubric|提交要求" README.md labs basic_operation AGENTS.md` |
| **Estimated runtime** | ~5 seconds |

---

## Sampling Rate

- **After every task commit:** Run `python3 -m py_compile tools/detect_system.py`
- **After every plan wave:** Run the relevant `rg` checks listed in each plan.
- **Before `$gsd-verify-work`:** Full suite and Markdown link checks must pass.
- **Max feedback latency:** 10 seconds for automated checks.

---

## Per-Task Verification Map

| Task ID | Plan | Wave | Requirement | Threat Ref | Secure Behavior | Test Type | Automated Command | File Exists | Status |
|---------|------|------|-------------|------------|-----------------|-----------|-------------------|-------------|--------|
| 02-01-01 | 02-01 | 1 | CONT-01 | — | N/A | docs grep | `rg -n "上一段产物|本段要完成|下一段会用到什么" labs` | ✅ | ⬜ pending |
| 02-01-02 | 02-01 | 1 | CONT-01, CONT-02 | — | N/A | docs grep | `rg -n "参数来源|预期效果|练习记录|自检清单" labs` | ✅ | ⬜ pending |
| 02-02-01 | 02-02 | 2 | CONT-03 | — | N/A | docs grep | `rg -n "操作补查|basic_operation|不是第二条主线" README.md labs` | ✅ | ⬜ pending |
| 02-02-02 | 02-02 | 2 | CONT-04 | — | N/A | docs grep | `rg -n "source_materials|Word|提炼" README.md .planning/phases/02-tutorial-flow-hardening` | ✅ | ⬜ pending |
| 02-02-03 | 02-02 | 2 | CONT-01 | — | N/A | docs grep | `rg -n "python3 tools/detect_system.py|--skip-capture|--format json|capture_status|capture_detail" README.md labs basic_operation` | ✅ | ⬜ pending |

*Status: ⬜ pending · ✅ green · ❌ red · ⚠️ flaky*

---

## Wave 0 Requirements

Existing infrastructure covers all phase requirements.

---

## Manual-Only Verifications

| Behavior | Requirement | Why Manual | Test Instructions |
|----------|-------------|------------|-------------------|
| Real hardware detector output maps to actual classroom devices | CONT-01 | Requires SO-101 arms and cameras connected to the machine | Run `python3 tools/detect_system.py`, inspect `tools/devices/device_simple.json`, and confirm screenshots match physical `top_camera` / `wrist_camera` roles. |
| LeRobot command form matches installed local version | CONT-01 | Local LeRobot version may differ from current upstream docs | On a configured machine, run the relevant `lerobot-* --help` or `python -m lerobot.* --help` commands before changing command names. |

---

## Validation Sign-Off

- [x] All tasks have automated verify commands or manual-only rationale.
- [x] Sampling continuity: no 3 consecutive tasks without automated verify.
- [x] Wave 0 covers all missing references.
- [x] No watch-mode flags.
- [x] Feedback latency < 10s for automated checks.
- [x] `nyquist_compliant: true` set in frontmatter.

**Approval:** approved 2026-05-12
