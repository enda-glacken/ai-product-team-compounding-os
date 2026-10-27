---
name: problem-framing
description: Use when a problem, opportunity or decision is still fuzzy and needs to become a bounded problem statement with hypotheses and evidence gaps before anyone writes a spec or builds a prototype.
---

# Problem framing

**Inputs:** project folder; the decision this work should inform; who it's for; evidence you're allowed to use.
**Writes to:** `spec.md` (problem section only), `evidence.md`, `risks-and-questions.md`.

## Steps
1. Read `context/` for relevant product-brain entries; cite any you rely on.
2. Describe the user need and today's difficulty without proposing a solution.
3. Log each piece of evidence in `evidence.md` with its kind (observation / interpretation / hypothesis) and limitations.
4. Draft the problem, audience, scope, non-goals and constraints in `spec.md`. Success signals may stay `TBD`.
5. List open questions and risks, each with the evidence that would resolve it.
6. Recommend **spec-first** or **prototype-first** and say why in two sentences.

## Output
A short framing draft plus the three biggest evidence gaps. Never presents a hypothesis as a finding.
