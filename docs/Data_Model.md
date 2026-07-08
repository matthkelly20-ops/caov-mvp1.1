# CAOV MVP 1.1 Data Model

This file is retained for compatibility with earlier project docs.

The current source-of-truth data model now lives in:

```text
docs/DATA_MODEL.md
```

## Current Data Model Summary

CAOV MVP 1.1 should support this flow:

```text
Team -> Schedule -> Games -> Away Trips -> Trip Workspace -> Requests/Open Items -> Missing Inputs -> Trip Artifacts
```

## Central Product Entity

`trip_requests` is now a central conceptual entity.

Real trip workflows show that away-trip operations involve requests, confirmations, owners, status, follow-ups, and day-of handoffs. These should not be buried as freeform notes.

## Core MVP Entities

See `docs/DATA_MODEL.md` for current details on:

- schools
- teams
- seasons
- schedules
- games
- trips
- contacts
- host_profiles
- trip_requests
- trip_tasks
- trip_documents
- trip_meals
- itinerary_events
- future trip artifact entities

## Privacy Note

Travel party and rooming list data are sensitive and should not be committed as raw examples.
