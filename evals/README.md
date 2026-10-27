# Evals for PM output

PM work has no compiler and no test suite. Nothing external tells you a spec or handover was good until something breaks downstream. A rubric plus a judge you've calibrated against human labels is the honest substitute.

**Status:** the rubric below is ready to use by hand or with a model as judge. The eval designs are specifications. Calibrate any judge against a set of hand-labelled examples before trusting its scores, and report the agreement rate alongside them.

## Rubric: is this handover ready?

Score each dimension pass / fail and note why. A handover is **ready** only if every dimension passes.

| # | Dimension | Pass when |
| --- | --- | --- |
| H1 | Traceable | Every in-scope item is a requirement ID in an approved spec revision, and the approval is recorded. |
| H2 | Bounded | Constraints, must-not-change and allowed scope are specific enough that a reviewer could say whether a given change violates them. |
| H3 | Failure-aware | Each requirement has at least one named failure case. |
| H4 | Checkable | Every requirement has a "done when" check that can be run, with an expected result. |
| H5 | Unfakeable | Checks test what the system does, not what the diff looks like; a cosmetic change can't make them pass. |
| H6 | Conflict-free | No two requirements, or requirement and constraint, contradict; or the conflict is flagged with a decision. |
| H7 | Risk-honest | The risk tier matches the blast radius (data, money, users affected). |

The [Brightdesk handover](../examples/brightdesk/projects/waitlist-auto-offer/handoff.md) is a worked example that passes all seven.

## Eval designs

1. **Handover durability.** Give a fresh agent session only the saved project files after a mid-project correction. Pass if the correction survives into its output. This tests whether the repo, not the chat, holds the state.
2. **Contradiction spotting, with a control.** Pair a spec containing a real requirement conflict with a control spec where both requirements can be met. Pass only if the agent pauses on the first and proceeds on the second, and the resolution carries into the implementation. The control stops reflexive scepticism from scoring well.
3. **Restart recovery.** Interrupt an implementation mid-task; resume in a new session. Pass if it continues from the return and tracker without repeating or skipping work.
4. **Cost ratio.** Flag any task costing ~3× its neighbours (time or tokens). It is usually two pieces of work described as one, which makes it a spec smell rather than an engineering one.

**Validity check:** a high score should predict catching different failures in the future, not just reward the behaviour the rubric names. Re-test the rubric against new failure cases periodically.
