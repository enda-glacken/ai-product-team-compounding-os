# Worked example: Brightdesk waitlist auto-offer

> **Fictional.** Brightdesk, its people, data and numbers are invented to show every file in use. Nothing here describes a real company or product.

**Brightdesk** is a (fictional) desk-booking app for a chain of 40 co-working spaces. Members book a desk for a day; on busy days everything sells out, and same-day cancellations leave desks empty while other members are turned away.

This example follows one feature, **waitlist auto-offer**, through the whole loop:

| Step | File | What to notice |
| --- | --- | --- |
| 1. Frame | [spec.md § Problem](projects/waitlist-auto-offer/spec.md) · [evidence.md](projects/waitlist-auto-offer/evidence.md) | Observations, interpretations and hypotheses kept apart (E1–E5) |
| 2. Prototype | [evidence.md E5–E6](projects/waitlist-auto-offer/evidence.md) | A 5-person test changes the spec (email fallback) |
| 3. Spec | [spec.md](projects/waitlist-auto-offer/spec.md) | Every requirement has an acceptance criterion and a failure case |
| 4. Review | [decisions.md D1–D2](projects/waitlist-auto-offer/decisions.md) | r1 sent back over a quiet-hours conflict; r2 approved, with rejected options recorded |
| 5. Handover | [handoff.md](projects/waitlist-auto-offer/handoff.md) | Must-not-change, allowed scope, risk tier, and a runnable "done when" per requirement |
| 6. Build | [tasks.md](projects/waitlist-auto-offer/tasks.md) | Status lives only here |
| 7. Return | [implementation-return.md](projects/waitlist-auto-offer/implementation-return.md) | Coverage by requirement, checks not run, one deviation, learnings |
| 8. Accept | [decisions.md D3](projects/waitlist-auto-offer/decisions.md) | Acceptance is a separate decision from approval |
| 9. Compound | [context/members.md](context/members.md) | A learning promoted into the product brain after review |

Score the handover with the [evals rubric](../../evals/README.md); it passes all seven dimensions.
