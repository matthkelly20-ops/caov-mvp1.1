# CAOV Away-Trip Operations Workspace

CAOV stands for **College Athletics Operations Venture**.

This repository is the MVP 1.1 build for CAOV: an AI-native college athletics operations product starting with baseball away-trip operations.

## MVP Wedge

The current MVP wedge is:

> Upload a schedule, and CAOV creates an operations workspace for each away trip — showing what’s known, what’s missing, what needs confirmation, who owns it, and what goes into the final itinerary.

The product promise is:

> We help college athletics teams execute away trips with less chaos, less manual work, and fewer missed details.

## What This MVP Is

MVP 1.1 should become an **Away-Trip Operations Workspace** for college baseball staff.

It should help users:

1. Upload or enter a season schedule.
2. Detect away games.
3. Group away games into trips/series.
4. Create a structured workspace for each trip.
5. Track host logistics, contacts, requests, confirmations, open items, and missing inputs.
6. Generate a coach-ready itinerary/trip packet from structured data.

## What This MVP Is Not

This MVP is not:

- A Teamworks replacement.
- A generic AI travel planner.
- A chatbot-first product.
- A static visitor guide.
- A full finance system.
- A full ticketing system.
- A fully automated booking system.

Teamworks may remain the downstream publishing/distribution system. CAOV should own the upstream planning, validation, request tracking, and artifact-generation layer.

## Primary Demo Scenario

The first demo scenario is based on **University of Portland Baseball at Santa Clara University**.

This scenario should be used to test:

- Away-series grouping.
- Trip workspace layout.
- Host profile data.
- Practice/game logistics.
- Transportation, hotel, meals, and per diem notes.
- Trip requests/open items.
- Missing-input checklist.
- Coach-ready itinerary output.

## Core Product Model

Real baseball travel workflows show this pattern:

- Host profile = reusable answers.
- Trip workspace = trip-specific execution.
- Trip requests = open operational questions and confirmations.
- AI = parser, router, drafter, recommender, and memory layer.

Trip requests/open items should be first-class objects in the MVP.

## Source-of-Truth Docs

Future Codex sessions should read `AGENTS.md` first, then the project docs:

- `CAOV_MASTER_PROJECT_FILE.md`
- `docs/MVP_SCOPE.md`
- `docs/SANTA_CLARA_SCENARIO.md`
- `docs/DATA_MODEL.md`
- `docs/AI_INTERACTION_MODEL.md`
- `docs/REAL_TRIP_COMMUNICATION_PATTERNS.md`
- `docs/TRIP_ARTIFACT_PATTERNS.md`
- `docs/TRIP_DATA_MAPPING_PATTERNS.md`
- `docs/DECISIONS.md`
- `docs/CHANGELOG.md`
- `docs/CODEX_TASKS.md`

## Working Model

- Planning, strategy, and product direction: ChatGPT.
- Code generation and repo edits: Codex.
- Source of truth for code and documentation: GitHub.
- Frontend and app-building surface: Lovable.
- Backend database and structured data repository: Supabase.

The immediate goal is to prove that a baseball schedule can become a useful away-trip operations workspace before expanding into broader athletics operations workflows.
