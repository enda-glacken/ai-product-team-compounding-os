# Implementation return (fictional)

- **Delivered:** booking-service v4.12, member app 7.3, admin 2.9
- **Against:** handover for spec r2 (approval D2)
- **Prepared by:** coding agent; reviewed by Priya Nair
- **Acceptance:** D3 in [decisions](decisions.md): accepted with follow-up T6

## Mechanism used

Cancellations emit an event; an offer worker takes a row lock on the location-day queue, creates the offer and schedules expiry as a delayed job. Accept goes through the booking service with a conditional insert on (desk, day), so the database rejects the second writer. Agreed with Priya before coding.

## Coverage

| Req | Delivered behaviour | Check | Result | Evidence |
| --- | --- | --- | --- | --- |
| R1 | Join/leave waitlist; position shown | C1, C2 | pass | CI run 2241 |
| R2 | Offer + push + email within ~4 s | C3, C4 | pass (see deviation) | CI run 2241 |
| R3 | Expiry and advance | C5, C6 | pass | CI run 2241 |
| R4 | Atomic accept | C7 | pass, 1,000/1,000 runs | race-test log |
| R5 | Quiet hours by location TZ | C8, C9 | pass | CI run 2241 |
| R6 | Manager counts, no identities | C10, C11 | pass | CI run 2243 |
| — | Existing suite unchanged | full `npm test` | pass, 0 tests modified | CI run 2243 |

## Checks not run and known gaps

- Real-device push on Android 15 (emulator only). Tracked as T6.
- Load beyond 50-member queues: capped by spec, not tested past the cap.

## Deviations from the spec

- **R2 email:** the notification service rate-limits email to one per member per minute (Q1), so a member offered twice within a minute gets the second email up to 60 s late. Push is unaffected. Changing the limit is outside allowed scope; accepted in D3.

## Learnings

1. The quiet-hours conflict was caught at spec review (D1), not at framing. Time-of-day and time-zone behaviour should be a standard failure case for anything that notifies people.
2. 22% of pilot members have push off (Q2). Any notification-led feature here needs a second channel from day one.
3. Pilot, first two weeks: 61% of offers accepted, median 3 min 40 s; email-only members accepted at 38%, median 9 min (E7). The 15-minute hold looks right for push users and tight for email users (hypothesis; needs more data).

## Proposed product-brain edits

From capture-learnings, reviewed 2 Oct:
- **Promote:** "About 1 in 5 members have push notifications off; design notification-led features with a second channel." Approved by Aoife Brennan → [context/members.md](../../context/members.md).
- **Template change:** add "time of day / time zone / DST" to the spec template's failure-case prompts. Proposed; pending team review.
- **Hold for more data:** the hold-length finding (learning 3). Stays in the project until the 4-week pilot ends.
