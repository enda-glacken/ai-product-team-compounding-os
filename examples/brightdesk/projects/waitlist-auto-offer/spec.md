# Spec (fictional)

- **Revision:** r2
- **Author:** Aoife Brennan
- **Changed since r1:** added R5 quiet hours (resolves the R2/quiet-hours conflict raised in D1); added email fallback to R2 after E6; R6 narrowed to counts only.
- **Review:** D2 in [decisions](decisions.md)

## Problem

On sold-out days, members who need a desk are turned away (E1) while same-day cancellations (E2) probably leave desks empty (E3, hypothesis). Members cope by refreshing the app (E4). We want freed desks to reach someone who wants them, without members having to watch the app.

## Goals and non-goals

- Goal: a freed desk on a sold-out day gets offered to a waiting member automatically.
- Goal: no double-booking, ever.
- Non-goal: paid priority on the waitlist.
- Non-goal: waitlists for meeting rooms (separate booking system).

## Constraints

- Booking service is the only writer of bookings.
- Notifications go through the existing notification service (push + email); no new providers.

## Requirements

| ID | Requirement | Why (evidence) | Acceptance criterion | Failure cases |
| --- | --- | --- | --- | --- |
| R1 | A member can join the waitlist for a location and day when no desks are free | E1, E4 | Join button appears only when availability = 0; joining returns the member's queue position | Member already booked that day → join refused with message; member already on that waitlist → no duplicate |
| R2 | When a desk frees up, the first member in the queue gets an offer by push **and** email, held for 15 minutes | E5, E6 | Offer created within 30 s of cancellation; push and email both sent; hold expires at +15 min | Notification service down → offer still created, retry sends; member deleted their account → skip to next |
| R3 | An expired or declined offer moves to the next member | E5 | On expiry/decline the next member gets an offer within 30 s | Queue empty → desk returns to general availability |
| R4 | Accepting an offer creates the booking atomically | goal: no double-booking | Two simultaneous accepts for one desk → exactly one booking, other gets "no longer available" | Accept after expiry → refused, member stays in queue at their position |
| R5 | No offers are sent between 22:00 and 07:00 location time; desks freed overnight are offered at 07:00 | D1 | Cancellation at 23:30 → first offer sent at 07:00:00 local, hold to 07:15 | Location in a different time zone from the server; daylight-saving change night |
| R6 | Location managers see waitlist count per day | manager request (Q3) | Admin view shows counts for the next 14 days | Count only, no member names (privacy) |

## Possible conflicts

- R2 (offer within 30 s) vs R5 (quiet hours): resolved in r2 by R5 taking precedence overnight. See D1.

## Accessibility, privacy, dependencies, limits

- Accessibility: offer screen meets the app's existing WCAG 2.2 AA standard; the email has a plain-text part.
- Privacy: managers see counts only (R6); queue positions aren't shown to other members.
- Dependencies: notification service retry behaviour (Q1).
- Limits: max 50 members per location-day waitlist (prevents runaway queues).

## Success signals

| Signal | Baseline | Target | How measured | Owner |
| --- | --- | --- | --- | --- |
| Share of same-day-cancelled desks re-booked on sold-out days | TBD (E3 unverified) | TBD after 4-week pilot | Bookings + cancellations join | Aoife Brennan |
| Waitlist offer acceptance rate | none | Not set; observe in pilot | Offer events | Aoife Brennan |
