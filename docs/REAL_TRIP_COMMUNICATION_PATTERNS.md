# Real Trip Communication Patterns

## Purpose

This file captures sanitized real-world college baseball trip communication patterns. These examples show why CAOV is solving request/confirmation workflows, not just itinerary creation.

Do not commit raw email threads, personal phone numbers, full email addresses, payment handles, private addresses, DOBs, or private contact details. These examples are intentionally role-based and sanitized.

## Pattern Summary

- Practice/lift = facility access workflow.
- Laundry = service/payment/handoff workflow.
- Tickets/pass list = game-day guest access workflow.
- Per diem = internal finance/roster/meal workflow.
- Visiting-team intake = bundled host/visitor operations workflow.

Larger product model:

- Host profile = reusable answers.
- Trip workspace = trip-specific execution.
- Trip requests = open operational questions and confirmations.
- AI = parser, router, drafter, recommender, and memory layer.

## Example 1: Practice and Lift Coordination

A visiting baseball team coordinated Thursday practice and Friday weight room access with a host school.

Sanitized flow:

1. Visiting team operations requested Thursday practice and Friday lift access.
2. Host baseball operations approved practice and routed lift coordination to sports performance.
3. Sports performance confirmed weight room availability and location.
4. Visiting team later confirmed an updated lift time.
5. Day-of directions still required communication.
6. Visiting team sent a thank-you note afterward.

Product implication:

Facility access should be modeled as a request/confirmation workflow, not just a static itinerary note.

Data model implication:

Use `trip_requests` for practice/lift requests, owner, status, confirmation, and day-of notes.

AI implication:

AI should parse the communication, identify confirmed times, owners, open questions, and draft follow-ups.

## Example 2: Laundry Service Coordination

A visiting baseball team coordinated laundry service with the host school.

Sanitized flow:

1. Visiting team asked whether host laundry or outside vendors were available.
2. Host baseball operations routed the question to equipment staff.
3. Equipment staff offered weekend laundry service for a fixed fee and described locker room or hotel delivery options.
4. Visiting team asked about digital payment and receipt requirements due to university policy.
5. Host confirmed digital payment was acceptable.
6. Visiting team later confirmed Thursday practice laundry.
7. Day-of execution involved leaving laundry in a designated location and coordinating hotel drop-off.

Product implication:

Laundry is a service workflow with owner, cost, payment method, receipt requirement, pickup/drop-off, and delivery status.

Data model implication:

Consider `trip_requests`, `trip_services`, `trip_payments`, and `host_service_options`.

AI implication:

AI should extract service availability, cost, payment method, receipt requirement, pickup/drop-off options, hotel delivery preference, and open follow-ups.

## Example 3: Tickets and Pass List Coordination

A visiting baseball team asked about ticket availability for fans.

Sanitized flow:

1. Visiting team asked how many tickets were available per game.
2. Host confirmed 75 tickets per game via pass list.
3. Host ticketing would collect the pass list from the visiting dugout shortly after arrival each day.

Product implication:

Ticketing/pass list is a game-day handoff workflow, not just a note.

Data model implication:

Consider `trip_ticketing`, `trip_pass_lists`, and `pass_list_entries`.

AI implication:

AI should extract ticket allotment, per-game basis, pass-list process, collection owner, collection location, timing, and repeated game-day tasks.

## Example 4: Per Diem and Travel Finance Coordination

Internal athletics business operations requested travel roster and per diem preferences before a road series.

Sanitized flow:

1. Business operations requested travel roster and per diem preferences by a deadline.
2. Baseball staff clarified that multiple meals were catered, reducing the per diem need.
3. Baseball staff requested a smaller instant card amount.

Product implication:

Per diem is an internal finance workflow tied to roster, meal plan, catered meals, funding method, deadlines, and late-stage changes.

Data model implication:

Consider `trip_finance`, `trip_per_diem`, and `trip_funding_requests`.

AI implication:

AI should calculate expected per diem from travel party count and meal plan, flag missing roster/per diem inputs, and draft business-office responses.

## Example 5: Visiting Team Operations Intake

A visiting baseball operations contact sent a bundled pre-trip request to a host school.

Sanitized request categories included:

- Practice.
- Bat testing.
- Laundry.
- Pregame times.
- Field rules.
- Parking.
- Postgame meals.
- Delivery address.
- Tickets/seating.
- Chart/video/velocity seating.
- Showers.
- Best contact method.

Host operations answered several items, routed laundry/showers to another staff member, provided parking guidance, and left some items pending.

Product implication:

CAOV needs a structured visiting-team operations intake workflow.

Data model implication:

`trip_requests` should support categories like practice, bat testing, laundry, pregame schedule, field rules, parking, meals, delivery address, ticketing, staff seating, showers, athletic training, equipment, transportation, finance, and other.

AI implication:

AI should parse bundled emails into categorized requests, assign likely owners, identify unanswered items, generate host responses from host profile data, and store reusable host answers.

## Cross-Example Product Conclusion

CAOV should not be only an itinerary builder. CAOV should become a trip operations workflow system.

Core objects:

- `host_profiles`
- `trips`
- `trip_requests`
- `trip_services`
- `trip_tasks`
- `trip_documents`
- `contacts`
- `trip_ticketing`
- `trip_pass_lists`
- `trip_finance`
- `trip_per_diem`

Not all of these need to be fully implemented in MVP v1, but the MVP should avoid a data model that makes them impossible later.

## Key Takeaway

Away-trip logistics operate through request/confirmation workflows. CAOV should model these workflows explicitly instead of burying them as notes in an itinerary.
