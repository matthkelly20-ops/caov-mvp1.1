# CAOV AI Interaction Model

**Version:** v0.1
**Purpose:** Define how CAOV should use AI across the product without becoming a generic chatbot or over-automated planning tool.

---

## 1. Core Principle

CAOV should use AI to support structured athletics operations workflows.

The product should not be “chat with your trip.”

The product should be:

> A structured away-trip operating workspace with AI assistance layered into the moments where parsing, planning, recommendation, summarization, and institutional memory are useful.

AI should help users:

* Understand uploaded documents.
* Extract useful data.
* Create structured trip records.
* Recommend logistics options.
* Identify missing information.
* Generate coach-ready outputs.
* Learn from prior trips.
* Reduce repeated manual work.

AI should not be treated as the source of truth.

The source of truth should be structured data, verified documents, user-approved inputs, and historical trip records.

---

## 2. High-Level AI Layers

CAOV should think about AI in three major layers:

1. **Trip Planning Assistance**
2. **Data Parsing and Structuring**
3. **Learning Loops and Institutional Memory**

Over time, these layers can combine into a more powerful AI-native operating system for college athletics operations.

---

# Layer 1: Trip Planning Assistance

## Description

This layer uses AI to help with general trip planning tasks once a trip workspace exists.

This is the most user-visible layer. It helps the operations person, coach, GA, or travel coordinator make better decisions faster.

Examples include:

* Recommending flight options.
* Recommending hotels near the host venue.
* Finding food options within budget.
* Suggesting catered meal options.
* Identifying restaurants that can handle large groups.
* Estimating drive times between airport, hotel, field, and restaurants.
* Recommending practice windows.
* Drafting emails to host-school contacts.
* Drafting itinerary language.
* Creating day-by-day trip summaries.
* Identifying missing logistics details.
* Flagging unrealistic timing.
* Summarizing host-school visitor information.

## Product Role

This layer should feel like an assistant inside the trip workspace.

It should not replace the structured workspace. It should enhance it.

Example user questions:

* “Find dinner options within 15 minutes of the hotel under $20/person.”
* “Draft an email to Santa Clara asking about practice time and laundry.”
* “What information are we still missing before this trip is complete?”
* “Create a coach-ready itinerary for May 6.”
* “Does this schedule leave enough time between landing and practice?”
* “Suggest airport lunch options at PDX within $10/person.”

## Data Sources

This layer may use:

* Structured trip data.
* Uploaded schedule.
* Host-school profile.
* Team preferences.
* Budget rules.
* Travel party size.
* Prior trip history.
* Public location/vendor information.
* User-entered constraints.

## Trust Model

All recommendations should be clearly marked as recommendations until approved.

The product should distinguish between:

* Verified information.
* User-entered information.
* AI-suggested information.
* Placeholder/mock information.
* Missing information.

Example labels:

* `Verified`
* `Needs review`
* `AI suggestion`
* `Missing`
* `Mock data`

## Near-Term MVP Use

This should not be the first thing overbuilt.

For the first MVP, Layer 1 should be limited to:

* Generate itinerary from existing structured data.
* Identify missing trip inputs.
* Draft simple emails.
* Suggest meal/vendor options manually or semi-manually.
* Answer questions only from verified trip data.

---

# Layer 2: Data Parsing and Structuring

## Description

This layer uses AI to ingest messy inputs and turn them into structured CAOV data.

This may become one of the most important layers because college athletics data is fragmented across formats.

Inputs may include:

* PDF schedules.
* CSV schedules.
* Website schedules.
* Uploaded itineraries.
* Visitor guides.
* Hotel confirmations.
* Flight confirmations.
* Bus confirmations.
* Meal plans.
* Roster pages.
* Staff lists.
* Host-school documents.
* Email threads.
* Spreadsheets.

The AI should recognize what the document is, extract relevant information, map it to the correct data types, and identify missing or ambiguous fields.

## Examples

### Schedule Upload

A user uploads a baseball schedule.

AI should extract:

* Opponent.
* Date.
* Game time.
* Location.
* Home/away/neutral status.
* Conference game status.
* Multi-game series grouping.
* Venue if available.
* City/state if available.

Then the system should create:

* Games.
* Away trips.
* Trip date windows.
* Opponent school records if needed.
* Missing-input checklist.

### Host Visitor Guide Upload

A user uploads a host-school visitor guide.

AI should extract:

* Facility location.
* Parking instructions.
* Practice policy.
* Laundry policy.
* Locker room access.
* Athletic training contact.
* Equipment contact.
* Pass list policy.
* Game-day contact.
* Emergency information.
* Important deadlines.
* Host-school rules.

Then the system should map this into:

* Host profile.
* Contacts.
* Policies.
* Tasks.
* Trip-specific notes.

### Itinerary Upload

A user uploads an old itinerary.

AI should extract:

* Travel party size.
* Flight details.
* Hotel information.
* Bus schedule.
* Meal schedule.
* Practice times.
* Game times.
* Contacts.
* Budget assumptions.
* Reusable planning patterns.

Then the system should identify which items are reusable for future trips.

## Product Role

This layer is the bridge between messy athletics operations reality and a clean CAOV workspace.

The product should not expect users to manually enter everything.

The value is:

> Upload messy files → CAOV turns them into structured trip data → user reviews and approves.

## Trust Model

Parsing should always include human review.

The system should show:

* Extracted value.
* Source document.
* Confidence level.
* Suggested destination field.
* Review status.

Example:

| Extracted Data             | Source            | Suggested Field     | Confidence | Status       |
| -------------------------- | ----------------- | ------------------- | ---------- | ------------ |
| May 7, 2027, 6:00 PM       | Uploaded schedule | Game 1 start time   | High       | Needs review |
| Laundry available postgame | Visitor guide     | Laundry policy      | Medium     | Needs review |
| Henry Muench               | User input        | Day-of-game contact | High       | Verified     |

The user should approve before AI-parsed data becomes verified.

## Near-Term MVP Use

This layer should be an early priority.

The first build should support:

* CSV schedule upload.
* Manual schedule fallback.
* Away-game detection.
* Trip grouping.
* Santa Clara scenario seed data.
* Basic document upload with manual extraction or semi-automated extraction later.

PDF parsing can come after the CSV/manual workflow is stable.

---

# Layer 3: Learning Loops and Institutional Memory

## Description

This layer turns past trips into future planning context.

This is where CAOV can become more than a trip-planning tool. It can become a memory layer for athletics operations.

Every completed trip should create reusable knowledge.

Examples:

* Which hotel worked well?
* Which restaurants handled the group successfully?
* Which vendors were reliable?
* What timing was too tight?
* What did the coach complain about?
* What did players like?
* What information was missing?
* What changed from the prior year?
* Which host contacts were responsive?
* What should be done differently next time?
* What sport-specific differences mattered?

## Learning Scope

CAOV should learn at several levels.

### Within One Trip

During the trip planning process, CAOV should remember:

* Open tasks.
* Missing inputs.
* Confirmed details.
* Changed details.
* Key decisions.
* User preferences.

### Within One Season

Across multiple trips in the same season, CAOV should learn:

* Team travel preferences.
* Common meal budgets.
* Preferred hotels.
* Common bus timing.
* Coach preferences.
* Repeated itinerary structure.
* Standard packing or equipment needs.
* Recurring contacts.

### Year Over Year

Across seasons, CAOV should learn:

* What happened last time this team visited the same opponent.
* What host-school details changed.
* What vendors were used.
* What timing worked.
* What should be repeated or avoided.

### Across Sports

Across sports at the same school, CAOV should learn:

* Shared vendors.
* Shared host-school contacts.
* Department-level policies.
* Common travel providers.
* Facility-specific differences.
* Sport-specific needs.

### Across Schools

Over time, if host profiles become verified, CAOV may learn:

* Standard host-school procedures.
* Visitor policies by venue.
* Reliable local vendors.
* Cross-school logistics patterns.
* Common pain points for visiting teams.

This is the long-term data moat.

## Product Role

This layer should appear as suggestions and memory prompts.

Examples:

* “Last time UP visited Santa Clara, the team used this hotel.”
* “The 2026 trip had a tight turnaround between landing and practice.”
* “Baseball usually uses catered postgame meals for night games.”
* “Women’s soccer used the same hotel last fall and rated it positively.”
* “This host-school contact was verified 14 months ago and may need reconfirmation.”
* “You usually budget $20/person for postgame dinner.”

## Trust Model

Learning loops should not silently overwrite current plans.

They should suggest, compare, and remind.

The system should distinguish:

* Historical fact.
* Current verified detail.
* Suggested reuse.
* Changed information.
* User preference.
* Department policy.

Example:

> “Historical note: UP Baseball used Hotel X for the 2026 Santa Clara trip. This has not been verified for the 2027 trip.”

## Near-Term MVP Use

This does not need to be fully built in the first MVP.

But the data model should be designed so this becomes possible later.

For MVP, capture:

* Trip notes.
* Post-trip feedback.
* Vendor used.
* What went well.
* What went wrong.
* What should be reused.
* What should be avoided.

A simple post-trip review form could become the first version of the learning loop.

---

# 3. Proposed AI Architecture

CAOV should separate AI interaction into four functional categories.

## 3.1 Extraction AI

Purpose:

> Turn unstructured documents into structured data.

Used for:

* Schedule parsing.
* Visitor guide parsing.
* Itinerary parsing.
* Roster parsing.
* Confirmation parsing.
* Contact extraction.

Output:

* Suggested structured fields.
* Confidence score.
* Source reference.
* Review status.

## 3.2 Recommendation AI

Purpose:

> Help users make planning decisions.

Used for:

* Flights.
* Hotels.
* Meals.
* Local vendors.
* Timing checks.
* Budget-aware suggestions.
* Practice schedule suggestions.

Output:

* Ranked options.
* Rationale.
* Constraints considered.
* Data needed before approval.

## 3.3 Generation AI

Purpose:

> Create useful operational artifacts.

Used for:

* Coach-ready itinerary.
* Email drafts.
* Trip summary.
* Missing-input checklist.
* Day-by-day schedule.
* Vendor outreach messages.
* Internal handoff notes.

Output:

* Draft artifacts requiring review.
* Editable text.
* Source-linked assumptions.

## 3.4 Memory AI

Purpose:

> Use prior trips and decisions to improve future planning.

Used for:

* “What did we do last time?”
* “What usually works for this team?”
* “What changed from last year?”
* “Which vendor did we use?”
* “What should we avoid?”
* “What does this coach prefer?”

Output:

* Historical context.
* Suggested reuse.
* Warnings.
* Comparison to prior trips.

---

# 4. AI Should Be Embedded in Workflows

AI should appear where it helps the user complete a task.

It should not only live in a chat box.

Examples:

## Schedule Upload Page

AI function:

* Detect columns.
* Map fields.
* Identify away games.
* Group trips.
* Ask for missing information.

## Trip Workspace

AI function:

* Show missing inputs.
* Generate itinerary.
* Answer trip-specific questions.
* Draft emails.
* Flag timeline issues.

## Host Profile

AI function:

* Extract policies from documents.
* Summarize visitor guide.
* Identify contacts.
* Compare current host data to last verified version.

## Meals Section

AI function:

* Recommend options within budget.
* Consider travel party size.
* Consider distance from hotel/venue.
* Reuse past successful vendors.

## Post-Trip Review

AI function:

* Summarize what happened.
* Capture lessons learned.
* Update reusable memory.
* Flag changes needed for next year.

---

# 5. Staged Implementation Plan

## Stage 1: Structured Workspace First

Build:

* Trip workspace.
* Schedule upload/manual entry.
* Away-game detection.
* Santa Clara scenario.
* Host profile.
* Contacts.
* Meals.
* Travel.
* Hotel.
* Missing inputs.
* Itinerary generation from structured data.

AI use:

* Minimal.
* Mostly generation from existing structured fields.
* No heavy autonomy.

Goal:

> Prove the workflow.

## Stage 2: Parsing Intelligence

Build:

* CSV schedule parser.
* PDF schedule parser.
* Visitor guide parser.
* Itinerary parser.
* Column mapping.
* Human review interface.

AI use:

* Extraction.
* Data classification.
* Suggested field mapping.
* Missing data detection.

Goal:

> Reduce manual data entry.

## Stage 3: Planning Recommendations

Build:

* Meal recommendation assistant.
* Hotel/location suggestion assistant.
* Flight/travel timing checker.
* Budget-aware planning assistant.
* Email drafting assistant.

AI use:

* Recommendations.
* Drafting.
* Constraint checking.
* Source-aware suggestions.

Goal:

> Help staff make better planning decisions faster.

## Stage 4: Learning Loops

Build:

* Post-trip review.
* Prior-trip comparison.
* Vendor memory.
* Coach preference memory.
* Host-school change detection.
* Year-over-year planning suggestions.

AI use:

* Memory retrieval.
* Pattern recognition.
* Reuse suggestions.
* Warnings based on prior trips.

Goal:

> Make every trip improve the next one.

## Stage 5: System of Action

Build:

* Task automation.
* Vendor outreach workflows.
* Host-school confirmation workflows.
* Calendar generation.
* Approval workflows.
* Multi-user collaboration.
* Cross-school verified profiles.

AI use:

* Semi-autonomous execution.
* Human approval gates.
* Workflow orchestration.

Goal:

> Move from planning assistant to operational execution layer.

---

# 6. What To Build First

The first MVP should prioritize:

1. Structured trip workspace.
2. Santa Clara scenario seed data.
3. Schedule upload/manual entry.
4. Away-trip grouping logic.
5. Missing-input checklist.
6. Itinerary generation.
7. Basic document upload.
8. Manual host profile entry.
9. Simple AI-generated itinerary draft from verified fields.

Do not build first:

* Fully autonomous travel booking.
* General chatbot.
* Complex multi-school network.
* Full Teamworks integration.
* Overbuilt recommendation engine.
* Advanced memory layer.
* Automated vendor outreach.

---

# 7. Key Product Guardrails

## Guardrail 1: AI does not equal truth

AI can suggest, extract, summarize, and draft.

Users verify.

## Guardrail 2: The workspace is the product

The core product is the structured trip workspace.

AI enhances it.

## Guardrail 3: Every AI output needs context

AI should show what data it used and what assumptions it made.

## Guardrail 4: Missing data should stay visible

The system should never hide uncertainty.

## Guardrail 5: Build memory deliberately

Do not create vague memory. Capture structured trip outcomes, vendor history, and user-approved lessons.

## Guardrail 6: Start with one trip

The first proof point is one real trip, not the whole athletics department.

---

# 8. Strategic Importance

This AI interaction model matters because it keeps CAOV from becoming either:

1. A static guide with light AI decoration, or
2. A generic chatbot with no operational structure.

The correct path is between those extremes:

> Structured athletics operations workflows powered by AI at the right moments.

The long-term moat is not just AI.

The moat is:

* Verified host-school data.
* Real trip history.
* Workflow-specific context.
* Cross-season memory.
* Cross-sport operating patterns.
* Human-approved institutional knowledge.
* Repeated execution loops.

---

# 9. Current Working Thesis

CAOV should use AI in three escalating ways:

1. **Assist the current trip**

   * Generate itinerary.
   * Recommend options.
   * Draft communication.
   * Identify missing information.

2. **Structure messy inputs**

   * Parse schedules.
   * Read PDFs.
   * Map columns.
   * Extract host policies.
   * Convert documents into trip data.

3. **Improve future trips**

   * Learn from past trips.
   * Reuse successful vendors.
   * Remember coach/team preferences.
   * Compare year-over-year data.
   * Build institutional memory.

The first MVP should be built so all three layers are possible, but only the first two need to be lightly functional at the beginning.

---

# 10. One-Sentence Summary

CAOV should use AI to convert messy athletics operations inputs into structured trip workflows, assist staff with planning decisions, and learn from each completed trip so future trips become easier, smarter, and less manual.
