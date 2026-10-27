# Contributing a skill

Any PM can add a skill. Keep the set small: a new skill earns its place by doing something the existing seven don't, often enough to matter.

## Before you write one

- Check whether an existing skill can be extended instead.
- Have you done the task by hand at least three times? Write down what good output looked like each time. That's your spec.

## Format

Create `skills/<kebab-case-name>/SKILL.md`:

```markdown
---
name: <kebab-case-name>
description: One sentence on when to use it. This is what the agent reads to decide whether the skill applies, so name the trigger, not the method.
---

# <Title>

**Inputs:** what the human must provide.
**Writes to:** which project files, if any.

## Steps
1. …

## Output
What comes back, and what it must never claim.
```

Rules:
- Don't restate `AGENTS.md`. Reference it.
- Name exactly which template files the skill reads and writes.
- State what the output must never claim (e.g. "never marks anything approved").
- Under ~60 lines. If it's longer, it's probably two skills.

## Getting it merged

1. Run the skill on the [Brightdesk example](examples/brightdesk/README.md) or a real project and attach the output to your pull request.
2. Score that output against the [evals rubric](evals/README.md) where a dimension applies.
3. Use [the pull-request template](templates/pull-request.md). One reviewer from the team approves; record it like any other decision.
