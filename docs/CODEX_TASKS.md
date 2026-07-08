# Codex Tasks

## Current Build Principle

Build the structured trip operations workspace before AI features.

## Task 1: Confirm repo/app structure

Inspect the current repo and summarize:

- Framework.
- Package manager.
- Existing app structure.
- Existing Lovable-generated files.
- Existing Supabase files.

Do not make app changes.

## Task 2: Confirm documentation foundation

Ensure `AGENTS.md` and source-of-truth docs exist and are aligned.

## Task 3: Define minimal Supabase schema

Create the first schema plan for:

- schools
- teams
- seasons
- schedules
- games
- trips
- trip_games
- contacts
- host_profiles
- trip_requests
- trip_tasks
- trip_documents
- trip_meals

Do not overbuild finance, ticketing, or services yet unless explicitly requested.

## Task 4: Seed Santa Clara demo data

Seed the University of Portland at Santa Clara scenario with clearly marked mock data.

## Task 5: Build trip workspace page

Create a structured trip operations workspace with sections:

- Overview
- Games
- Travel
- Hotel
- Meals
- Practice/Lift
- Host Profile
- Contacts
- Requests/Open Items
- Documents
- Missing Inputs
- Itinerary

## Task 6: Add trip requests/open items

Create a UI and data structure for trip requests/open items.

Categories should include:

- practice
- lift
- laundry
- ticketing/pass list
- meals
- parking
- showers
- finance
- other

## Task 7: Add missing-input checklist

Show what is missing before a trip is considered ready.

## Task 8: Add itinerary/trip packet generation placeholder

Generate a coach-ready itinerary/trip packet from structured data.

## Future Task: Build trip artifact generation

Generate export-ready trip artifacts from structured data:

1. Itinerary/trip packet first.
2. Travel party summary second.
3. Rooming list later.

## Task 9: Add AI parsing/drafting later

Only after structured workflow exists, add AI support for:

- Schedule parsing.
- Column mapping.
- Document/email parsing.
- Drafting host/visitor communication.
- Missing-input detection.
- Itinerary text generation.

## Guardrail

Do not ask Codex to “build the whole app” in one step. Use small scoped tasks and update `docs/CHANGELOG.md` and `docs/DECISIONS.md` as needed.
