---
name: context-maintenance
description: Use when product-brain entries need adding, reconciling or retiring, including promoting reviewed learnings from a project into context/.
---

# Context maintenance

**Inputs:** the `context/` files in scope; proposed edits (often from capture-learnings); the evidence behind them.
**Writes to:** `context/`, only for edits a named human has approved.

## Steps
1. Compare current entries with the evidence and recorded decisions.
2. Flag stale entries (past their re-check date), conflicts, unsupported claims, and anything not fit for the audience.
3. Propose narrow edits that keep the reasoning, rejected alternatives and uncertainty; don't overwrite history, supersede it.
4. Get human review of the exact proposed text, then apply only what was approved, recording reviewer and date in the entry.

## Output
Proposed edits and a review request, or the applied edits with their approval. Never promotes something because it's been repeated often.
