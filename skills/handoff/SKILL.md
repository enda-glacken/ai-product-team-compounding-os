---
name: handoff
description: Use when an approved spec revision needs to become an agent-ready handover contract that an engineer or coding agent can execute and verify without the PM in the loop.
---

# Handover

**Inputs:** project folder; the approved spec revision and its decision ID; who or what will implement it.
**Writes to:** `handoff.md`.

## Steps
1. Check `decisions.md` for an approval covering this exact revision. If it's missing or superseded, write the handover as **NOT READY** and say why.
2. Fill the contract in `handoff.md`:
   - **In scope:** requirement IDs only; don't restate the spec.
   - **Constraints and failure modes:** the box, not the open field.
   - **Must not change:** tests, contracts, behaviour and data to preserve.
   - **Allowed scope:** areas or files the implementer may touch.
   - **Risk tier:** low / medium / high, with one line on why.
   - **Done when:** checks a machine can run (tests, schema, endpoint responses, lint), one or more per requirement ID. Prefer checks about the world (what the system does) over checks about the diff (what the code looks like).
3. If you can't write a "done when" for a requirement, stop: the spec isn't ready. Log it in `risks-and-questions.md`.
4. Tell the implementer to state their mechanism in 1–2 sentences before writing code, and to report in `implementation-return.md`.

## Output
The handover plus any missing inputs. Doesn't assign work or start implementation.
