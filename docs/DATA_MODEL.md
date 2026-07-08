# Data Model

This is a conceptual planning document for CAOV MVP 1.1. It is not a migration file.

## Product Flow

```text
Team -> Schedule -> Games -> Away Trips -> Trip Workspace -> Requests/Open Items -> Missing Inputs -> Trip Artifacts
```

## MVP Data Model Clarifications

- The repo previously referenced a flexible `logistics_items` concept in earlier planning.
- `logistics_items` is now deprecated as the primary MVP workflow model.
- `trip_requests` is the central flexible object for MVP request/confirmation workflows.
- Specialized entities like `trip_services`, `trip_ticketing`, `trip_finance`, `trip_per_diem`, `travel_parties`, `rooming_lists`, and `artifact_exports` are future/conceptual unless explicitly pulled into an implementation task.
- MVP schema should start small and should not implement every conceptual future table.
- `docs/SCU_DEMO_DATA_REQUIREMENTS.md` should guide Santa Clara seed data and schema planning, but not every spreadsheet field should become a required MVP column.
- First schema implementation should prioritize:
  - `schools`
  - `teams`
  - `seasons`
  - `schedules`
  - `games`
  - `trips`
  - `trip_games`
  - `contacts`
  - `host_profiles`
  - `trip_requests`
  - `trip_tasks`
  - `trip_documents`
  - `trip_meals`
  - `itinerary_events`

Operational fields may eventually include metadata such as `source_type`, `review_status`, `visibility`, `confidence`, and `priority` so the app can distinguish user-entered values, parsed values, calculated values, AI suggestions, mock values, and missing inputs.

## Core MVP Entities

MVP v1 should prioritize these entities:

- `schools`
- `teams`
- `seasons`
- `schedules`
- `games`
- `trips`
- `trip_games`
- `contacts`
- `host_profiles`
- `trip_requests`
- `trip_tasks`
- `trip_documents`
- `trip_meals`
- `itinerary_events`

## Central Entity: trip_requests

`trip_requests` should be central because real away-trip logistics operate as request/confirmation workflows.

## trip_requests MVP Definition

`trip_requests` is the core object for operational questions, requests, confirmations, handoffs, and open items.

MVP statuses:

- `draft`
- `open`
- `requested`
- `routed`
- `pending_confirmation`
- `confirmed`
- `needs_follow_up`
- `blocked`
- `completed`
- `canceled`

Minimum required fields:

- `id`
- `trip_id`
- `category`
- `title`
- `status`
- `owner_type`
- `priority`
- `created_at`
- `updated_at`

Optional fields:

- `description`
- `internal_owner_contact_id`
- `host_owner_contact_id`
- `requested_by_contact_id`
- `due_date`
- `confirmed_answer`
- `confirmed_at`
- `source_type`
- `source_id`
- `follow_up_needed`
- `notes`

Ownership rules:

- `internal_owner_contact_id` = visiting/team-side owner accountable for making sure the item gets done.
- `host_owner_contact_id` = host-side person responsible for answering or executing.
- `requested_by_contact_id` = person who originally created or asked the item.
- `owner_type` = `internal`, `host`, `vendor`, `business_office`, or `unknown`.

For MVP v1, `trip_requests` should be flexible enough to represent practice requests, lift requests, laundry coordination, parking questions, pass-list handoffs, per diem/finance questions, showers, meals, staff seating, bat testing, and other host/visitor operations items.

Suggested categories:

- `practice`
- `lift`
- `bat_testing`
- `laundry`
- `pregame_schedule`
- `field_rules`
- `parking`
- `meals`
- `delivery_address`
- `ticketing`
- `pass_list`
- `staff_seating`
- `showers`
- `athletic_training`
- `equipment`
- `transportation`
- `finance`
- `other`

## Service / Handoff Entities

These are future/conceptual unless explicitly pulled into an implementation task:

- `trip_services`
- `trip_ticketing`
- `trip_pass_lists`
- `pass_list_entries`
- `trip_finance`
- `trip_per_diem`
- `trip_funding_requests`

## Future Artifact Entities

Real trip artifacts suggest these future entities:

- `travel_parties`
- `travel_party_members`
- `rooming_lists`
- `room_assignments`
- `room_assignment_members`
- `trip_artifacts`
- `artifact_exports`

Not every entity needs to be fully implemented in MVP v1. The goal is to keep the model extensible so CAOV can eventually generate final artifacts before Teamworks upload or team/staff distribution.

## Schedule Mapping Fields

A schedule upload should eventually map raw rows into normalized game records.

Suggested fields:

- `source_file_id`
- `source_row_number`
- `season_year`
- `sport`
- `team_id`
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

## Itinerary Event Fields

Itineraries should be generated from structured data, not manually typed from scratch.

Suggested `itinerary_events` fields:

- `trip_id`
- `event_date`
- `start_time`
- `end_time`
- `time_zone`
- `event_type`
- `title`
- `location_name`
- `address`
- `related_game_id`
- `related_transportation_id`
- `related_meal_id`
- `related_request_id`
- `cost_context`
- `per_diem_context`
- `notes`
- `status`
- `source`
- `review_status`

Event types may include:

- Depart campus.
- Airport arrival.
- Flight.
- Ground transportation.
- Meal.
- Per diem.
- Practice.
- Lift.
- Hotel check-in.
- Team meeting.
- Scouting report.
- Batting practice.
- Pregame timing.
- Game.
- Postgame meal.
- Curfew.
- Return travel.

## Privacy Notes

Travel party and rooming list data can include sensitive PII such as names, DOBs, mobile numbers, travel status, and room assignments. Treat these as sensitive and avoid committing raw examples to the repository.
