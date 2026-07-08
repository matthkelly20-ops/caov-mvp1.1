# Changelog

## 2026-07-07 — Docs foundation for CAOV MVP 1.1

Docs-only update.

Added/updated MVP context around the away-trip operations workspace wedge:

- Added root `AGENTS.md` with durable Codex instructions.
- Added `CAOV_MASTER_PROJECT_FILE.md` as source-of-truth project context.
- Updated `README.md` around the current MVP wedge.
- Added `docs/MVP_SCOPE.md`.
- Added `docs/SANTA_CLARA_SCENARIO.md`.
- Added `docs/DATA_MODEL.md`.
- Updated `docs/AI_INTERACTION_MODEL.md`.
- Added `docs/REAL_TRIP_COMMUNICATION_PATTERNS.md`.
- Added `docs/TRIP_ARTIFACT_PATTERNS.md`.
- Added `docs/TRIP_DATA_MAPPING_PATTERNS.md`.
- Added `docs/DECISIONS.md`.
- Added `docs/CODEX_TASKS.md`.

Product conclusions added:

- CAOV MVP should be an Away-Trip Operations Workspace.
- Trip requests/open items should be first-class MVP objects.
- Real trip communication should be modeled as request/confirmation workflows.
- Practice/lift, laundry, tickets/pass list, per diem, and visiting-team intake each represent distinct workflow categories.
- CAOV should own upstream trip planning, validation, and artifact generation before Teamworks upload/distribution.
- AI should be embedded into structured workflows, not used as the primary product surface before the workspace is validated.

Privacy/safety notes:

- Raw emails and raw trip documents were not committed.
- Sensitive PII such as player names, DOBs, phone numbers, room assignments, payment handles, booking codes, and confirmation numbers should not be committed.
- Travel party and rooming data should be treated as sensitive.
