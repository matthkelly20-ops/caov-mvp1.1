# AGENTS.md

## Required Context Files

Before making product or code changes, read:

- `README.md`
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

## Product Direction

CAOV stands for College Athletics Operations Venture.

The current MVP wedge is baseball away-trip operations. The MVP should be an **Away-Trip Operations Workspace**, not merely an itinerary builder, generic AI travel planner, static visitor guide, or Teamworks replacement.

Product promise:

> We help college athletics teams execute away trips with less chaos, less manual work, and fewer missed details.

Sharpened MVP wedge:

> Upload a schedule, and CAOV creates an operations workspace for each away trip — showing what’s known, what’s missing, what needs confirmation, who owns it, and what goes into the final itinerary.

Trip requests and open items should be first-class objects in the MVP.

## MVP Flow

Schedule upload/manual entry
→ away-game detection
→ away-trip grouping
→ trip operations workspace
→ host profile/reusable host data
→ trip requests and open items
→ missing-input checklist
→ itinerary/trip packet output

## AI Guardrails

- Do not build a generic chatbot as the primary product surface.
- Build structured trip operations workflows first, with AI assistance layered in later.
- AI should help parse, structure, summarize, draft, recommend, and remember.
- AI is not the source of truth. Verified structured data, user-approved inputs, source documents, and historical trip records are the source of truth.
- Distinguish verified, user-entered, AI-suggested, missing, and mock information.

## Technical Guardrails

- Prefer simple, readable implementation over premature abstraction.
- Do not add major dependencies without explaining why.
- Do not create AI features before the structured trip workspace exists.
- Preserve the University of Portland / Santa Clara baseball scenario as the primary MVP demo case unless explicitly instructed otherwise.
- Do not commit raw private trip documents, personal phone numbers, DOBs, room pairings, payment handles, booking codes, or confirmation numbers.
- Treat travel party and rooming data as sensitive.

## Workflow Rules

- Read source-of-truth docs before coding.
- Make the smallest useful change.
- Update `docs/CHANGELOG.md` after meaningful changes.
- Update `docs/DECISIONS.md` when a product or technical decision is made.
- Do not change app code when the task is docs-only.
