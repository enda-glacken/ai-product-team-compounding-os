---
name: spec-review
description: Use when a specific spec revision needs scrutiny before a human decides whether to approve it for handover.
---

# Spec review

**Inputs:** the exact spec revision; the project's evidence register and decisions.
**Writes to:** nothing by default. Saves findings to a file only if asked.

## Review for
- **Correctness:** requirements fit the problem and constraints; no two contradict.
- **Evidence:** claims are supported; contrary evidence is visible, not dropped.
- **Clarity:** terms, scope and acceptance criteria are testable by someone who wasn't in the room.
- **Completeness:** failure cases, dependencies and risks are surfaced.
- **Handover-readiness:** could you write a machine-checkable "done when" for every requirement? If not, say which, and why.

## Output
Findings, each with location, consequence and suggested fix, split into **blocking** and **recommended**. End with a one-line recommendation (approve / revise / reframe). Never fills in `decisions.md`; that entry belongs to the human reviewer.
