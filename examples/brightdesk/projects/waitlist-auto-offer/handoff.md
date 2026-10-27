# Handover contract (fictional)

- **Status:** READY
- **Spec revision:** r2 · **Approval:** D2 in [decisions](decisions.md)
- **Implementer:** coding agent, reviewed by Priya Nair (EM)
- **Risk tier:** medium. It writes bookings, which members pay for, so a double-booking is a refund and a complaint. It doesn't touch payments or auth.

## In scope

R1–R6 from spec r2.

Out of scope: personal quiet-hours settings (rejected in D1), meeting rooms, any change to the notification service.

## Constraints and failure modes

- Booking service remains the only writer of bookings; the offer engine calls it and never writes the table directly.
- Every failure case listed against R1–R6 in the spec must be handled.
- All times are evaluated in the **location's** time zone, never the server's.

## Must not change

- `POST /bookings` request and response contract (used by the partner API).
- Existing booking test suite: all tests keep passing, none edited or skipped.
- Cancellation refund rules.

## Allowed scope

- `services/booking/waitlist/**` (new)
- `services/booking/offers/**` (new)
- `services/booking/api/routes/waitlist.ts` (new)
- `apps/member/src/screens/Waitlist*` and `OfferSheet*` (new)
- `apps/admin/src/views/WaitlistCounts*` (new)
- One migration adding `waitlist_entries` and `offers` tables

Anything else, including shared booking code: ask first.

## Done when

| Check | Req | How to run it | Expected result |
| --- | --- | --- | --- |
| C1 | R1 | `npm test -- waitlist/join` | Join allowed only at availability 0; returns position |
| C2 | R1 | same suite | Already-booked or already-queued member refused; no duplicate row |
| C3 | R2 | `npm test -- offers/create` with fake clock | Offer row within 30 s of cancellation; push + email jobs enqueued |
| C4 | R2 | same, notification service stubbed to fail | Offer still created; send retried |
| C5 | R3 | `npm test -- offers/expiry` | At +15 min, next member offered within 30 s |
| C6 | R3 | same | Empty queue → desk back in general availability |
| C7 | R4 | `npm run test:race -- accept --runs 1000` | Exactly one booking per desk in every run; loser gets 409 |
| C8 | R5 | `npm test -- offers/quiet-hours` (TZ=Europe/Dublin and America/New_York) | Cancellation at 23:30 local → offer at 07:00:00 local |
| C9 | R5 | same, clock crossing the DST change | Exactly one 07:00 offer on the change night |
| C10 | R6 | `GET /admin/locations/:id/waitlist-stats` against seeded data | Counts for next 14 days match seed |
| C11 | R6 | same, inspect response | No member names or IDs present |

Plus: existing `npm test` suite green with no tests modified.

## Before you start

State your mechanism in 1–2 sentences and wait for Priya's thumbs-up (medium risk). If two requirements conflict, stop and ask.

## Return

Report in [implementation-return.md](implementation-return.md) against C1–C11.
