# Codex Instructions for CAOV MVP 1.1

This file is retained for compatibility with earlier project docs.

The primary Codex instruction file is now:

```text
/AGENTS.md
```

Codex should read `AGENTS.md` first, then follow the current source-of-truth docs listed there.

## Current Product Direction

CAOV stands for College Athletics Operations Venture.

The current MVP wedge is baseball away-trip operations.

The MVP should be an **Away-Trip Operations Workspace** that turns a schedule into structured away-trip workspaces with known details, missing inputs, owners, confirmations, trip requests/open items, and itinerary/trip packet output.

## Do Not

- Do not reposition CAOV as a Teamworks replacement.
- Do not build a generic chatbot-first product.
- Do not treat the MVP as only an itinerary builder.
- Do not commit raw private travel docs or sensitive PII.

## Required Context

Read:

- `AGENTS.md`
- `CAOV_MASTER_PROJECT_FILE.md`
- `docs/MVP_SCOPE.md`
- `docs/DATA_MODEL.md`
- `docs/AI_INTERACTION_MODEL.md`
- `docs/REAL_TRIP_COMMUNICATION_PATTERNS.md`
- `docs/TRIP_ARTIFACT_PATTERNS.md`
- `docs/TRIP_DATA_MAPPING_PATTERNS.md`
- `docs/DECISIONS.md`
- `docs/CODEX_TASKS.md`

## Build Order

Build the structured trip operations workspace before AI features.
