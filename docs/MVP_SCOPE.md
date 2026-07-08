# MVP Scope

## MVP Name

**Away-Trip Operations Workspace**

## MVP Promise

Upload a schedule, and CAOV creates an operations workspace for each away trip — showing what’s known, what’s missing, what needs confirmation, who owns it, and what goes into the final itinerary.

## In Scope

MVP v1 should support:

- Schedule upload or manual schedule entry.
- Away-game detection.
- Multi-game series grouping.
- Trip workspace creation.
- Host profile and reusable host data.
- Trip overview.
- Contacts and role owners.
- Trip requests/open items.
- Practice/lift request tracking.
- Laundry/service request tracking.
- Ticket/pass-list notes or basic workflow tracking.
- Per diem/meal funding notes.
- Missing-input checklist.
- Trip documents.
- Coach-ready itinerary/trip packet generation.
- University of Portland at Santa Clara demo scenario.

## Out of Scope for MVP v1

MVP v1 should not attempt:

- Full Teamworks replacement.
- Fully autonomous booking.
- Generic AI chatbot-first interface.
- Full finance system.
- Full ticketing system.
- Full cross-school host network.
- Advanced learning loops.
- Full vendor marketplace.
- Deep integrations with Teamworks.
- Full PII-heavy travel party generation.
- Detailed rooming-list automation.

## First-Class MVP Object

Trip requests/open items should be first-class objects.

Real workflows show that away-trip logistics are request/confirmation workflows, not just notes in an itinerary. The MVP should explicitly represent open questions, owners, statuses, confirmed answers, and follow-up needs.

## SCU Demo Data and Field Prioritization

The University of Portland at Santa Clara demo should follow:

- `docs/SCU_DEMO_DATA_REQUIREMENTS.md` for sanitized demo data categories, treatment types, and priority fields.
- `docs/MVP_FIELD_PRIORITIZATION.md` for progressive-disclosure guidance.

MVP v1 should avoid presenting a long flat checklist or spreadsheet-style setup form. The app should use progressive disclosure so users see confirmed summaries, missing inputs, open requests, upcoming deadlines, and itinerary/trip packet preview first.

## First Itinerary Output Format

MVP v1 should generate a coach-ready web trip packet first. It should be readable in the app and copy/export-friendly as Markdown or printable from the browser.

Do not implement PDF export yet.

The first trip packet should include:

- Trip title.
- Travel party count.
- Key contacts.
- Day-by-day schedule.
- Flights.
- Ground transportation.
- Hotel.
- Meals/per diem.
- Practice/lift.
- Games.
- Requests/open items.
- Missing inputs.
- Notes.

The itinerary/trip packet should be generated from structured data. Unknown or unconfirmed items should remain visible as open items or missing inputs, not hidden or guessed.

## Required Workspace Sections

A trip workspace should eventually include:

- Overview.
- Games.
- Travel.
- Hotel.
- Meals.
- Practice/Lift.
- Host Profile.
- Contacts.
- Requests/Open Items.
- Documents.
- Missing Inputs.
- Itinerary / Trip Packet.

## MVP Success Criteria

A successful MVP demo should show that a user can:

1. Upload or enter a baseball schedule.
2. Identify away games.
3. Group away games into trip workspaces.
4. Open a trip workspace.
5. View known logistics.
6. See missing information.
7. Track operational requests and confirmations.
8. Generate or preview a coach-ready itinerary/trip packet.

The user should understand how CAOV reduces manual coordination work before information is pushed to Teamworks or distributed to athletes/staff.
