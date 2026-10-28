# AI Product Team Compounding OS

**A product operating system for teams that build with agents.**

Specs, evidence and decisions live as markdown in a repo. A small set of skills runs the product workflow. Handovers are contracts a coding agent can execute and verify without the PM in the loop. What the team learns flows back into a shared product brain, so each project starts smarter than the last.

Engineering already has its orchestration layer and its harness. This is the product layer that feeds them.

## Install

No dependencies, no code. Clone it and start a project:

```sh
git clone <this-repo> my-product-os && cd my-product-os
cp -R templates/project projects/my-first-project
```

- **Claude Code:** skills are discovered from `.claude/skills/` (a link to `skills/`). Invoke one by name, e.g. "use the spec-drafting skill on projects/my-first-project".
- **Codex and other agents:** `AGENTS.md` is the entry point; skills are plain markdown in `skills/<name>/SKILL.md`.
- **Any chat assistant:** paste `AGENTS.md` plus one `SKILL.md` and the project files you want it to work on.

## How it works

```
 frame ─▶ spec ─▶ review ─▶ handover ─▶ agent builds ─▶ return ─▶ accept
   ▲                (human     (contract with                (human
   │                 decision)  "done when")                  decision)
   │                                                            │
   └──────────── product brain ◀── capture learnings ◀──────────┘
```

| Piece | What it does |
| --- | --- |
| **Skills** | Seven opinionated PM skills: [problem framing](skills/problem-framing/SKILL.md), [spec drafting](skills/spec-drafting/SKILL.md), [spec review](skills/spec-review/SKILL.md), [prototype feedback](skills/prototype-feedback/SKILL.md), [handover](skills/handoff/SKILL.md), [capture learnings](skills/capture-learnings/SKILL.md), [context maintenance](skills/context-maintenance/SKILL.md). Small on purpose. |
| **Agent-ready handovers** | Constraints, failure modes, what must not change, allowed scope, risk tier, and a machine-checkable **"done when"**. If you can't write the "done when", the spec isn't ready. See [the template](templates/project/handoff.md). |
| **Decision log with reasoning** | Records what was decided, why, and what was rejected and why. Facts alone drift; reasoning lets agents and new teammates handle edge cases. See [decisions](templates/project/decisions.md). |
| **Product brain** | [`context/`](context/README.md) holds durable, reviewed knowledge. Proposals never get in by repetition, only by review. |
| **Compounding loop** | Every implementation return ends with learnings; the [capture-learnings](skills/capture-learnings/SKILL.md) skill turns them into proposed product-brain edits. |
| **Evals** | A [rubric](evals/README.md) for judging PM output (is this handover ready?), plus eval designs for handover durability, contradiction spotting and restart recovery. |
| **Worked example** | [Brightdesk](examples/brightdesk/README.md): a fictional feature taken from framing to accepted delivery, every file filled in. Start here. |

## Principles

1. **Evidence is not opinion, and a plan is not a shipped thing.** Every artefact keeps observation, interpretation, hypothesis, proposal and verified result apart.
2. **One home per fact.** Tasks live in one tracker, approvals in one decision log.
3. **Humans decide; agents recommend.** Approving a plan and accepting a delivery are separate decisions.
4. **Checks about the world, not the diff.** A "done when" an agent can satisfy cosmetically isn't one.
5. **Small and sharp beats big and generic.**

## Repo layout

```text
AGENTS.md                 rules for any assistant (the only place they live)
CLAUDE.md                 Claude Code entry point → AGENTS.md
CONTRIBUTING-A-SKILL.md   how a PM adds a skill
skills/<name>/SKILL.md    the skills (also at .claude/skills)
templates/project/        copy per project
templates/pull-request.md
context/                  the product brain
projects/                 your projects
evals/                    rubric + eval designs
examples/brightdesk/      fully worked fictional example
REVIEW-BEFORE-SHARING.md  checklist before publishing anything you add
LICENSE                   MIT
```

## Licence

[MIT](LICENSE) © 2026 Enda Glacken. The licence covers the files; it doesn't grant use of the name "AI Product Team Compounding OS".
