---
phase: 01
slug: tutorial-foundation
status: draft
nyquist_compliant: true
wave_0_complete: true
created: 2026-05-12
---

# Phase 01 — Validation Strategy

> Per-phase validation contract for feedback sampling during execution.

---

## Test Infrastructure

| Property | Value |
|----------|-------|
| **Framework** | shell checks |
| **Config file** | none |
| **Quick run command** | `python3 -m py_compile tools/detect_system.py` |
| **Full suite command** | local Markdown link resolver + scope grep checks |
| **Estimated runtime** | ~5 seconds |

---

## Sampling Rate

- **After every task commit:** Run the task-specific grep checks listed in PLAN.md.
- **After every plan wave:** Run the full verification command block from each PLAN.md.
- **Before `$gsd-verify-work`:** Full suite must be green.
- **Max feedback latency:** 5 seconds.

---

## Per-Task Verification Map

| Task ID | Plan | Wave | Requirement | Threat Ref | Secure Behavior | Test Type | Automated Command | File Exists | Status |
|---------|------|------|-------------|------------|-----------------|-----------|-------------------|-------------|--------|
| 01-01-01 | 01 | 1 | TUT-01/TUT-02/TUT-03 | — | N/A | grep/link | README section and forbidden-term checks | ✅ | ⬜ pending |
| 01-01-02 | 01 | 1 | TUT-02 | — | N/A | grep | source materials index lists all source docs | ❌ W0 | ⬜ pending |
| 01-02-01 | 02 | 1 | TUT-04 | — | N/A | grep | AGENTS.md contains tutorial-path guardrails | ✅ | ⬜ pending |
| 01-02-02 | 02 | 1 | TUT-04 | — | N/A | grep | CONVENTIONS.md uses practice/self-check language | ✅ | ⬜ pending |

*Status: ⬜ pending · ✅ green · ❌ red · ⚠️ flaky*

---

## Wave 0 Requirements

Existing infrastructure covers all phase requirements. No new test framework is required.

---

## Manual-Only Verifications

All Phase 1 behaviors have automated text verification.

---

## Validation Sign-Off

- [x] All tasks have automated verify commands.
- [x] Sampling continuity: no 3 consecutive tasks without automated verify.
- [x] Wave 0 covers all MISSING references.
- [x] No watch-mode flags.
- [x] Feedback latency < 5s.
- [x] `nyquist_compliant: true` set in frontmatter.

**Approval:** pending
