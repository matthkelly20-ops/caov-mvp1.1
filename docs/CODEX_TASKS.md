# Codex Tasks

## Current Build Principle

Build the structured trip operations workspace before AI features.

## Task 1: Prepare clean app foundation

Goal:

Prepare for the first actual application scaffold.

Instructions:

- Confirm the repo is docs-only.
- Do not treat missing Lovable files or Supabase files as a problem.
- Recommend the clean first app foundation path.
- Do not change app code yet.

Expected output:

- Recommended frontend scaffold path.
- Recommended Supabase setup sequence.
- Recommended first implementation branch name.
- Confirmation that docs are ready for Lovable/Codex build.

## Task 2: Scaffold Lovable/frontend app

Create the initial frontend app structure through Lovable or a Codex-approved scaffold only after explicit user approval.

## Task 3: Create minimal Supabase schema

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
- itinerary_events

Do not overbuild finance, ticketing, or services yet unless explicitly requested.

## Task 4: Seed Santa Clara demo data

Seed the University of Portland at Santa Clara scenario with clearly marked mock data.

- Use `docs/SCU_DEMO_DATA_REQUIREMENTS.md` for sanitized demo data categories and priority fields.
- Use `docs/MVP_FIELD_PRIORITIZATION.md` for UX guidance.
- Do not seed raw private data.
- Clearly mark mock values.

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

Create the first UI/data workflow for trip requests.

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

## Task 8: Add coach-ready trip packet output

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
