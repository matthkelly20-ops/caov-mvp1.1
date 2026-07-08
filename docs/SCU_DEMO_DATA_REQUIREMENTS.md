# SCU Demo Data Requirements

## Purpose

This file defines the sanitized demo data requirements for the University of Portland Baseball at Santa Clara University MVP trip.

The goal is not to create a 90-field user-facing form. The goal is to identify what data the app needs to represent internally so it can generate:

- a useful trip operations workspace
- a missing-input checklist
- trip requests/open items
- a coach-ready itinerary/trip packet

The original internal spreadsheet should not be committed, converted to CSV, or reproduced row-for-row in the repository.

## Source Spreadsheet Structure

The original spreadsheet used three columns:

- Field
- MVP Inputs
- Notes for development

Interpret the columns this way:

- Field = the operational data point or workflow concept.
- MVP Inputs = demo seed value, placeholder behavior, calculation instruction, mock value, or default assumption.
- Notes for development = future architecture notes, automation opportunities, learned-default logic, or AI assistance ideas.

Do not treat every row as a required user-facing field.

## MVP Inputs Column Treatment

Treat the MVP Inputs column as demo seed/default behavior, not as a required user-facing form.

Classify MVP Inputs into these treatment types:

| Treatment | Meaning | Example |
|---|---|---|
| actual_demo_value | Safe known value used in the demo | travel party count = 37, uniform colors = all black |
| mock_randomized_value | Placeholder value for sensitive or not-yet-known data | phone number, record locator, confirmation number |
| user_entered_value | Value a user/admin should provide or confirm | selected hotel, final roster, meal preference |
| calculated_value | Value derived from other inputs | room count, per diem total, meal budget total |
| ai_suggested_value | Value AI may recommend but user must verify | flight options, hotel policy, local vendor options |
| parsed_from_document | Value extracted from uploaded host docs or PDFs | laundry policy, athletic training contact |
| learned_default | Value reused from prior trips or team preferences | preferred bus vendor, per diem method |
| future_or_collapsed | Useful later but hidden in MVP by default | tax-exempt process, folio process, post-trip closeout |
| delete_or_not_applicable | Should not become an MVP field | irrelevant fields marked delete, remove, or N/A |

Rules:

- Safe demo values can be included when not sensitive.
- Sensitive values should be marked `mock_randomized_value` or omitted.
- Values marked calculate should be documented as `calculated_value`.
- Values marked find on web or find real flight should be documented as `ai_suggested_value` or future research, not hardcoded.
- Values marked pull from PDF should be documented as `parsed_from_document`.
- Values marked learned for future trips should be documented as `learned_default`.
- Values marked delete, remove field, or N/A should be documented as `delete_or_not_applicable`.

## Demo Trip Overview

Use the known Santa Clara scenario:

- Visiting team: University of Portland Baseball
- Host school: Santa Clara University
- Series dates: May 7-9, 2027
- Arrival: May 6, 2027
- Departure: May 9, 2027
- Travel party count: 37
- Uniform colors: all black
- Arrival airport: SJC
- Departure airport: SJC
- Home airport: PDX
- Practice: May 6, 2027, 7:00-9:00 PM at Santa Clara baseball field
- Game 1: May 7, 2027 at 6:00 PM
- Game 2: May 8, 2027 at 6:00 PM
- Game 3: May 9, 2027 at 12:00 PM
- Meal assumptions: hotel breakfast included, $10 lunch budget, $20 dinner budget, catered dinners after practice/games, per diem lunches before night games, airport dinner on return day
- Some values may be mock/randomized for demo purposes and must be clearly labeled as mock.

## Demo Data Categories

The spreadsheet groups data into these categories:

1. Trip party / roster
2. Flight details
3. Ground transportation
4. Hotel
5. Practice / facility / host logistics
6. Meals
7. Budget / finance / closeout
8. Documents / forms

For each category below, the MVP should distinguish:

- representative fields
- MVP treatment
- what should be primary
- what should be derived/calculated
- what should be collapsed/future
- what should be mocked or omitted

## Category 1: Trip Party / Roster

Representative fields include:

- final travel party count
- player roster traveling
- staff roster traveling
- rooming list status
- pass list / guest list status
- day-of-game travel party contact
- day-of-game contact phone
- visiting team uniform colors

MVP treatment:

- Travel party count should be primary.
- Uniform colors should be primary.
- Day-of-game contact should be primary.
- Player/staff roster details should be collapsed or future unless needed for a controlled demo.
- Phone numbers and personal details should be mocked or omitted.
- Rooming list and pass list should be tracked as artifacts/statuses, not fully built in MVP v1.

## Category 2: Flight Details

Representative fields include:

- outbound airline
- outbound flight number
- outbound departure airport
- outbound arrival airport
- outbound departure time
- outbound arrival time
- return airline
- return flight number
- return departure airport
- return arrival airport
- return departure time
- return arrival time
- group confirmation / ticketing record locator

MVP treatment:

- Flight information should appear in the Travel section and feed itinerary events.
- Flight times should drive suggested ground transportation timing.
- Confirmation/record locator should be mocked or omitted in demo.
- AI-suggested flight options are future/needs-review. MVP should allow user-entered or mock confirmed flight data.

## Category 3: Ground Transportation

Representative fields include:

- charter bus vendor for campus to airport
- campus pickup time
- airport drop-off time
- local charter bus vendor at destination
- destination airport pickup time
- bus size / number of buses
- driver name/contact
- local bus schedule for hotel to practice/games
- ballpark to airport pickup time
- return airport to campus vendor
- return airport pickup time
- emergency/after-hours bus contact

MVP treatment:

- Ground transportation should appear in the Travel section and feed itinerary events.
- Some transportation times can be calculated/suggested from flight times, airport buffers, and venue/hotel locations.
- Vendor names can be user-entered, learned defaults, or mocked.
- Driver personal contact details should be mocked or omitted.
- Emergency contacts should be tracked as contacts or open items.

## Category 4: Hotel

Representative fields include:

- selected hotel partner
- hotel contact
- hotel contact phone/email
- room block confirmation number
- number of rooms
- room types
- check-in time
- check-out time
- breakfast confirmation
- tax-exempt/payment process
- hotel cancellation deadline
- hotel invoice/folio process

MVP treatment:

- Selected hotel, address, check-in, check-out, breakfast status, and room count summary should be visible.
- Room count can be calculated or estimated from travel party count and rooming assumptions.
- Rooming list generation should be future/collapsed.
- Hotel contact and confirmation data can be optional.
- Tax-exempt, cancellation, folio, and invoice workflows should be future/collapsed unless explicitly needed.

## Category 5: Practice / Facility / Host Logistics

Representative fields include:

- host confirmation of practice time
- exact practice location / field access instructions
- batting practice details
- cage availability
- equipment storage availability
- locker room access timing
- laundry availability
- laundry contact/process
- athletic training needs
- athletic training contact confirmation
- bus drop-off/pick-up instructions
- parking permit/pass needs

MVP treatment:

- Practice time/location should be primary.
- Host logistics should primarily be represented through `trip_requests`/open items.
- Batting practice, laundry, athletic training, bus instructions, showers, and parking should be request categories.
- Fields like cage availability, equipment storage, and locker room access should be collapsed or represented as host logistics requests only when relevant.
- Fields marked delete/remove/N/A should not become MVP UI fields.
- Do not create a long static form for every possible host logistics field.

## Category 6: Meals

Representative fields include:

- final travel party count for meal budgeting
- catered meal vendor/contact/order method
- menu selections for catered meals
- delivery/pickup location
- delivery/pickup time
- dietary restrictions/allergies
- payment method
- receipt/invoice process
- per diem distribution method for lunches
- per diem distribution method for airport dinner
- per diem approval owner

MVP treatment:

- Meals should be displayed in the Meals / Per Diem section and feed itinerary events.
- Meal type should distinguish hotel-provided, per diem, catered, boxed, airport, and team-paid.
- Meal budget should be calculated from travel party count and per-person budget.
- Vendor/menu/payment/receipt details can be optional or collapsed.
- Dietary restrictions are important but can be future/collapsed for MVP unless needed in the demo.

## Category 7: Budget / Finance / Closeout

Representative fields include:

- airfare cost
- hotel estimated cost
- charter bus quotes
- catered meal estimated total
- per diem total
- tips/gratuity budget
- miscellaneous/incidentals budget
- sport budget code
- P-card holder
- approval owner
- receipt collection process
- invoice submission process
- post-trip reconciliation format

MVP treatment:

- MVP should not become a full finance system.
- Show basic budget/per diem notes only where they impact itinerary or missing inputs.
- Per diem total can be calculated from travel party count and meals.
- Budget code, receipts, invoices, P-card, and closeout should be future/collapsed.
- Finance items can be represented as `trip_requests`/open items when needed.

## Category 8: Documents / Forms

Representative fields include:

- visiting team travel information form
- pass list
- hotel contract or confirmation
- bus contract or confirmation
- flight/group travel confirmation
- catered meal order confirmations
- tax-exempt form
- final coach itinerary
- final athlete itinerary
- post-trip closeout packet

MVP treatment:

- Documents should appear in the Documents section.
- Each document should have status: `missing`, `draft`, `uploaded`, `reviewed`, `final`, or `not_applicable`.
- Final coach itinerary/trip packet should be the first generated artifact.
- Athlete itinerary, travel party, rooming list, and closeout packet can be future artifacts.

## Progressive Disclosure Rule

The app should not show all demo fields at once.

Default user view should show:

- confirmed summary
- missing inputs
- open requests
- upcoming deadlines
- itinerary/trip packet preview

Detailed fields should be collapsed by section or visible only when relevant.

## Data Source / Review Metadata

Where useful, fields should eventually support:

`source_type`:

- `user_input`
- `schedule_upload`
- `parsed_document`
- `host_profile`
- `learned_default`
- `ai_suggested`
- `calculated`
- `mock`

`review_status`:

- `missing`
- `needs_review`
- `confirmed`
- `not_applicable`

`visibility`:

- `primary`
- `collapsed`
- `internal`
- `future`

## MVP Priority From This Spreadsheet

For the first demo, prioritize:

1. Travel party count
2. Uniform colors
3. Day-of-game contact
4. Flights
5. Ground transportation
6. Hotel summary
7. Practice time/location
8. Games
9. Meals/per diem
10. Host logistics requests/open items
11. Documents/statuses
12. Missing inputs
13. Coach-ready itinerary/trip packet

Do not prioritize:

- full rooming list automation
- detailed travel party PII
- full budget/finance system
- post-trip reconciliation
- tax-exempt workflows
- invoice/folio workflows
- exhaustive host logistics checklist
- AI-powered vendor selection before structured workflow exists

## Product Conclusion

The internal data model can support rich operational data, but the MVP experience should stay focused on:

- what is confirmed
- what is missing
- what needs follow-up
- who owns it
- what goes into the final trip packet
