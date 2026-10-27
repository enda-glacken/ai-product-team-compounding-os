---
name: spec-drafting
description: Use when a framed problem needs to become a reviewable spec with numbered requirements and observable acceptance criteria.
---

# Spec drafting

**Inputs:** project folder with a framed problem; relevant `context/` entries; any decisions already recorded.
**Writes to:** `spec.md` (new revision), `risks-and-questions.md`.

## Steps
1. Bump the spec revision (r1, r2…) and note what changed since the last one.
2. Write goals, non-goals and requirements. Give each requirement an ID (R1, R2…), a rationale linked to evidence, and an acceptance criterion someone could check without asking you.
3. For each requirement, write at least one failure case: what happens when the input is wrong, missing, late or hostile. A happy-path-only spec reads as diligent and lets reviewers relax; don't write one.
4. Cover accessibility, privacy, dependencies and operating limits where they apply; say explicitly when one doesn't.
5. Flag any two requirements that could conflict.
6. Propose success signals only where they'd change a decision. Leave unknown baselines `TBD`.

## Output
The proposed revision and its open questions. Never claims it's approved, validated or built.
