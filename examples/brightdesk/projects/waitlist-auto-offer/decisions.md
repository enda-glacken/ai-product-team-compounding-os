# Decision log (fictional)

## D1 — Spec r1 review: revise

- **Type:** planning review
- **Covers:** spec r1
- **Decided by:** Aoife Brennan (PM) with Tomás Reyes (Head of Product) · **Date:** 24 Jul
- **Decision:** revise
- **Why:** The spec-review skill flagged a blocking conflict: R2 promised an offer within 30 s of any cancellation, but a member who cancels at 23:30 would wake someone with a 15-minute offer they'd sleep through. That wastes the desk and annoys the member. Also E6 (push off) wasn't reflected in R2.
- **Rejected alternatives:** 1) Extend the hold overnight to 9 hours: blocks the desk from everyone else, including early walk-ins. 2) Let members set personal quiet hours: right long-term, but adds settings UI and doubles the scope; revisit after the pilot.
- **Would revisit if:** pilot data shows many overnight cancellations at 24-hour sites.

## D2 — Spec r2 review: approve

- **Type:** planning review
- **Covers:** spec r2
- **Decided by:** Tomás Reyes · **Date:** 29 Jul
- **Decision:** approve for handover, pilot at 3 sites
- **Why:** Conflict resolved by R5; email fallback covers E6; every requirement has a checkable criterion.
- **Rejected alternatives:** 1) Ship chain-wide at once: E3 is still a hypothesis, so pilot at the 3 sensor sites where it can be checked. 2) Hold the build until Q2 (share of members with push off) is answered: R2 sends both channels regardless, so the answer doesn't change the build.
- **Would revisit if:** pilot shows offers going mostly unaccepted.

## D3 — Delivery acceptance: accept with follow-up

- **Type:** implementation acceptance
- **Covers:** booking-service v4.12 + app 7.3, per [implementation return](implementation-return.md)
- **Decided by:** Aoife Brennan with Priya Nair (EM) · **Date:** 2 Oct
- **Decision:** accept; follow-up for the email deviation
- **Why:** All 11 done-when checks pass. The one deviation (email batched at most once per minute) costs at most 60 s of a 15-minute hold. Android 15 push not yet verified on real devices, so that is tracked as T6, not a blocker for a 3-site pilot.
- **Rejected alternatives:** 1) Block acceptance until T6: the pilot sites are 80% iOS and email covers the rest. 2) Lift the email rate limit: that's a notification-service change, outside the allowed scope.
- **Would revisit if:** T6 finds Android offers not arriving.
