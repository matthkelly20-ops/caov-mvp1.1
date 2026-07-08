# CAOV MVP 1.1 Product Spec

This file is retained for compatibility with earlier project docs.

The current source-of-truth MVP scope now lives in:

```text
docs/MVP_SCOPE.md
```

## Current MVP Name

**Away-Trip Operations Workspace**

## MVP Promise

> Upload a schedule, and CAOV creates an operations workspace for each away trip — showing what’s known, what’s missing, what needs confirmation, who owns it, and what goes into the final itinerary.

## Core Flow

```text
Schedule upload/manual entry
  -> away-game detection
  -> away-trip grouping
  -> trip operations workspace
  -> host profile / reusable host data
  -> trip requests and open items
  -> missing-input checklist
  -> itinerary / trip packet output
```

## Required MVP Concept

Trip requests/open items are first-class MVP objects. The product should not bury operational questions and confirmations as notes inside an itinerary.

For current scope, read:

- `docs/MVP_SCOPE.md`
- `docs/SANTA_CLARA_SCENARIO.md`
- `docs/DATA_MODEL.md`
- `docs/CODEX_TASKS.md`
