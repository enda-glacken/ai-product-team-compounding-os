---
name: capture-learnings
description: Use after an implementation return or a project closes, to turn what the team learned into proposed product-brain entries so the next project starts smarter.
---

# Capture learnings

**Inputs:** the project's implementation return, decisions, evidence and risks.
**Writes to:** a proposal section at the end of `implementation-return.md`. Never writes to `context/` directly.

## Steps
1. Collect what turned out differently from the spec: deviations, surprises, risks that fired, assumptions that proved wrong or right.
2. Separate learnings that are **project-specific** (stay in the project) from ones that are **reusable**: about users, the domain, the system, or how the team specifies work.
3. For each reusable learning, draft a product-brain entry: the claim, the evidence behind it (with IDs), how confident it is, and when to re-check it.
4. Check `context/` for entries the learning confirms, contradicts or makes stale. Propose the edit; keep the old reasoning visible.
5. Note one change to a template or skill if the same problem has now happened twice.

## Output
A short list of proposed `context/` edits for human review. Promotion happens only through context-maintenance, after review.
