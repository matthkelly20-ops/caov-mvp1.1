# Trip Data Mapping Patterns

## Purpose

CAOV must understand both the upstream planning inputs and downstream artifacts involved in college baseball away-trip operations.

The product should map raw inputs into structured operational data, then use that structured data to generate trip artifacts.

Core workflow:

```text
Raw inputs
  -> parsed structured data
  -> trip operations workspace
  -> missing-input checklist
  -> reviewed/verified data
  -> final trip artifacts
  -> Teamworks upload or team/staff distribution
```

## Core Product Insight

CAOV should not only store documents. CAOV should understand the structure of the information inside typical athletics operations documents and map those fields into reusable trip objects.

## Input Pattern 1: Coach-Shared Schedule File

A typical schedule file may include:

- Schedule title.
- Date.
- Day of week.
- Opponent.
- Location.
- Game time.

Observed schedule-level structure:

- One title row.
- One header row.
- One row per game.
- Dates may be text values rather than normalized dates.
- Times may be blank, incomplete, or include time-zone notes.
- Opponent names may include symbols like `*` to indicate conference games.
- Opponent names may include notes like `(DH)` to indicate doubleheaders.
- Locations may be city/state rather than venue-specific addresses.
- Home/away status may need to be inferred from location.

Suggested schedule mapping fields:

- `source_file_id`
- `source_row_number`
- `season_year`
- `sport`
- `team`
- `raw_date_text`
- `normalized_date`
- `day_of_week`
- `opponent_raw`
- `opponent_normalized`
- `conference_game`
- `doubleheader_flag`
- `home_away_neutral`
- `location_raw`
- `city`
- `state`
- `venue`
- `raw_time_text`
- `normalized_start_time`
- `time_zone`
- `parsing_status`
- `review_status`
- `notes`

Important parsing logic:

- `*` before opponent may indicate conference game.
- `(DH)` may indicate doubleheader.
- Location matching the home city/campus may indicate home game.
- Out-of-market locations usually indicate away or neutral games.
- Consecutive away games against the same opponent should be grouped into one trip.
- Blank times should become missing inputs, not guessed values.
- Time zones should be preserved when present.

Product implication:

Schedule upload should create game records first, then group away games into trip records.

## Input Pattern 2: Real Communication Threads

Real trip communication often includes:

- Practice requests.
- Lift requests.
- Laundry requests.
- Ticket/pass-list questions.
- Per diem questions.
- Parking questions.
- Meal recommendations.
- Showers.
- Staff seating.
- Bat testing.
- Delivery address.
- Host contact routing.
- Day-of execution details.

Suggested mapping:

Communication threads should generate `trip_requests` and `trip_tasks`, not just notes.

Key fields:

- `request_category`
- `request_title`
- `requested_by`
- `assigned_to`
- `host_owner`
- `status`
- `confirmed_answer`
- `source_thread`
- `due_date`
- `confirmed_at`
- `follow_up_needed`
- `notes`

## Output Pattern 1: Travel Party

Travel party documents are structured roster artifacts.

Common sections:

- Athletes.
- Coaches.
- Sports medicine.
- Other support staff if applicable.

Common fields:

- Last name.
- Middle name.
- First name.
- DOB or travel-required identity field.
- Gender.
- Weight if required by travel provider.
- Mobile number.
- Role/category.

Suggested CAOV objects:

- `travel_parties`
- `travel_party_members`

Privacy note: travel party data is sensitive PII and should require careful permissions, review, and export controls.

For MVP v1, CAOV may only need travel party count and role categories. Full travel-party generation can come after the trip workspace is validated.

## Output Pattern 2: Hotel Rooming List

Rooming list documents are lodging assignment artifacts.

Common fields:

- Room type.
- Travelers assigned to each room.
- Check-in.
- Check-out.
- Billing indicator.
- Notes.
- Room type count.
- Total room count.

Suggested CAOV objects:

- `rooming_lists`
- `room_assignments`
- `room_assignment_members`

Privacy note: rooming lists are sensitive and should be permissioned.

For MVP v1, start with hotel details, travel party count, and room count summary.

## Output Pattern 3: Final Itinerary / Trip Packet

Final itineraries are day-by-day execution artifacts.

Common itinerary event types:

- Depart campus.
- Airport arrival.
- Flight.
- Ground transportation.
- Meal.
- Per diem.
- Practice.
- Hotel check-in.
- Team meeting.
- Scouting report.
- Batting practice.
- Pregame timing.
- Game.
- Postgame meal.
- Curfew.
- Return travel.

Suggested CAOV object:

- `itinerary_events`

Important itinerary logic:

- Itinerary should be generated from structured data, not manually typed from scratch.
- Unknown items like uncertain BP times or in/out times should remain visible as open items.
- Meals should connect to funding type: per diem, boxed, catered, hotel-provided, team-paid, or other.
- Ground transportation should connect airport, hotel, venue, meals, and campus.
- Time zones should remain explicit.
- Curfew and meeting times should be supported as itinerary event types.

Product implication:

The MVP should generate a coach-ready itinerary/trip packet from structured trip data.

## Cross-Document Data Flow

A schedule file creates:

- Games.
- Away trip candidates.
- Trip date windows.
- Opponent/host school references.
- Missing input checklist.

Communication threads create:

- Trip requests.
- Trip tasks.
- Host contact updates.
- Service workflows.
- Confirmed answers.
- Open items.

Travel party inputs create:

- Travel party count.
- Role categories.
- Traveler list.
- Roster dependency for per diem and rooming.

Meal/per diem inputs create:

- Trip meals.
- Per diem notes.
- Finance open items.
- Funding requests.

Rooming inputs create:

- Rooming list.
- Room assignments.
- Room counts.
- Hotel requirements.

Final itinerary output uses:

- Games.
- Flights.
- Ground transportation.
- Hotel.
- Meals.
- Practice/lift requests.
- Meetings.
- Curfew.
- Open items.
- Confirmed host details.

## MVP v1 Mapping Priority

Prioritize:

1. Schedule upload/manual entry.
2. Game records.
3. Away-trip grouping.
4. Trip workspace.
5. Host profile.
6. Contacts.
7. Trip requests/open items.
8. Missing inputs.
9. Meals/per diem notes.
10. Travel party count and role categories.
11. Hotel summary.
12. Itinerary events.
13. Trip packet generation.

Do not prioritize full PII-heavy travel party generation or detailed rooming automation in MVP v1 unless needed for a controlled demo.

## Product Conclusion

CAOV should own the upstream planning and artifact-generation layer before Teamworks upload.

Teamworks may remain the downstream distribution system, but CAOV can help produce cleaner, validated, structured trip artifacts before information is pushed to athletes, coaches, and staff.
