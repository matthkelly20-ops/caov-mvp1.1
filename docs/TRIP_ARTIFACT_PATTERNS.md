# Trip Artifact Patterns

## Purpose

CAOV must support not only pre-trip communication, but also the final artifacts that get uploaded to Teamworks or distributed to athletes, coaches, and staff.

These artifacts represent the output layer of the away-trip operations workflow.

This file summarizes structure only. Do not commit raw PDFs, player names, DOBs, phone numbers, room pairings, booking codes, confirmation numbers, payment handles, or private contact details.

## Artifact 1: Travel Party

A travel party document is a structured roster artifact.

Common sections:

- Athletes.
- Coaches.
- Sports medicine.
- Other support staff if applicable.

Common fields may include:

- Name.
- Role/category.
- DOB or travel-required identity field.
- Gender.
- Weight if required by travel provider.
- Mobile number.
- Travel status.

Product implications:

- CAOV should support travel party generation eventually.
- CAOV should distinguish athletes, coaches, sports medicine, support staff, and other travelers.
- CAOV should treat travel party data as sensitive PII.
- CAOV should support export-ready formats for upload/distribution.
- CAOV should track whether travel party is draft, reviewed, approved, or final.

## Artifact 2: Hotel Rooming List

A hotel rooming list is a lodging assignment artifact.

Common fields:

- Room type.
- Travelers assigned to each room.
- Check-in/check-out placeholders or dates.
- Billing responsibility.
- Notes such as coach, athletic trainer, bus driver, or head coach.
- Room type counts.
- Total room count.

Product implications:

- CAOV should eventually support rooming-list generation.
- CAOV should support role-based rooming rules.
- CAOV should support staff notes.
- CAOV should calculate room counts.
- CAOV should mark rooming lists as sensitive.
- CAOV should support export-ready hotel rooming documents.

## Artifact 3: Final Itinerary / Trip Packet

A final itinerary is a day-by-day execution artifact.

Common itinerary event types:

- Depart campus.
- Airport arrival.
- Flight.
- Ground transportation.
- Meal.
- Per diem.
- Practice.
- Hotel check-in.
- Scouting report/team meeting.
- Batting practice/pregame timing.
- Game.
- Postgame meal.
- Curfew.
- Return travel.

Product implications:

- CAOV should generate itinerary/trip packet output from structured trip data.
- Itinerary entries should be created from underlying objects such as flights, ground transportation, meals, practice, hotel, games, meetings, and curfew.
- Itinerary should clearly show time zone, location, notes, and cost/per diem context.
- Unknown items like uncertain BP or in/out times should remain visible as open items instead of being hidden.
- Itinerary should be export-ready for Teamworks or staff distribution.

## Cross-Artifact Product Conclusion

CAOV should own the upstream workflow before Teamworks upload:

1. Gather and parse schedule/trip inputs.
2. Track requests and confirmations.
3. Build travel party.
4. Build rooming list.
5. Build meals/per diem plan.
6. Build itinerary.
7. Validate missing information.
8. Generate export-ready trip packet.
9. Push/upload/share through Teamworks or another distribution channel.

For MVP v1, itinerary/trip packet generation should come first. Travel party and rooming-list generation should be treated as near-future features unless a simple mock/export version is needed for demo.

## Data Model Implications

Conceptual entities:

- `travel_parties`
- `travel_party_members`
- `rooming_lists`
- `room_assignments`
- `room_assignment_members`
- `itinerary_events`
- `trip_artifacts`
- `artifact_exports`

## Key Decision

CAOV should support generation of final trip artifacts before Teamworks upload or team/staff distribution.

Reason: real trip documents show that coaches/staff create travel party, rooming list, and itinerary artifacts before pushing information to Teamworks and the team. CAOV can own the upstream planning, validation, and artifact-generation workflow while treating Teamworks as a downstream distribution system.
