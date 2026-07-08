# CAOV Master Project File

**Project:** CAOV MVP 1.1  
**Working meaning:** College Athletics Operations Venture  
**Current wedge:** Baseball away-trip operations  
**Primary product surface:** Away-Trip Operations Workspace  
**Use:** Durable project context for ChatGPT, Codex, GitHub, Lovable, and future collaborators.

---

## Executive Summary

CAOV is an early-stage venture exploring an AI-native operating layer for college athletics operations.

The initial MVP focuses on baseball away-trip operations. CAOV should let a user upload or enter a season schedule, detect away games, group away games into trips, and generate structured operations workspaces for each trip.

The product is not just an itinerary builder. Real baseball travel workflows show that away trips are managed through requests, confirmations, handoffs, service coordination, internal finance details, host communication, and final artifact generation.

The current MVP promise is:

> We help college athletics teams execute away trips with less chaos, less manual work, and fewer missed details.

The sharpened MVP wedge is:

> Upload a schedule, and CAOV creates an operations workspace for each away trip — showing what’s known, what’s missing, what needs confirmation, who owns it, and what goes into the final itinerary.

---

## What CAOV Is

CAOV is intended to become a structured operations workspace for college athletics staff.

The MVP should support:

- Schedule upload or manual schedule entry.
- Away-game detection.
- Away-series/trip grouping.
- Trip workspace creation.
- Host profile and reusable host-school data.
- Contacts and role owners.
- Trip requests/open items.
- Missing-input checklist.
- Itinerary/trip packet generation.
- Basic trip artifact planning.

---

## What CAOV Is Not Yet

CAOV should not start as:

- A Teamworks replacement.
- A generic AI travel planner.
- A chatbot-first product.
- A static visitor guide.
- A full finance system.
- A full ticketing system.
- A full rooming-list automation system.
- A fully autonomous booking or vendor marketplace.

The first product should prove the trip operations workflow before expanding.

---

## MVP Flow

```text
Schedule upload/manual entry
  -> game records
  -> away-game detection
  -> away-series grouping
  -> trip operations workspace
  -> host profile / reusable answers
  -> trip requests and open items
  -> missing-input checklist
  -> itinerary / trip packet output
```

---

## Primary Demo Scenario

The primary MVP demo case is University of Portland Baseball at Santa Clara University.

Known scenario structure:

- Series dates: May 7–9, 2027.
- Arrival: May 6, 2027.
- Departure: May 9, 2027.
- Travel party: 37.
- Flights: United Airlines between PDX and SJC.
- Transportation: charter bus to PDX, throughout the Santa Clara trip, and back to campus.
- Practice: May 6, 2027, 7:00–9:00 pm at Santa Clara baseball field.
- Game 1: May 7, 2027 at 6:00 pm.
- Game 2: May 8, 2027 at 6:00 pm.
- Game 3: May 9, 2027 at 12:00 pm.
- Meals: airport lunch, catered dinners, per diem lunches, hotel breakfast, airport dinner.
- Budget assumptions: $10 lunch, $20 dinner, hotel breakfast included.
- Some details may be mock/randomized for demo purposes and must be clearly labeled as mock.

---

## Key Product Insight From Real Workflows

Real trip communication showed these workflow types:

- Practice/lift = facility access workflow.
- Laundry = service/payment/handoff workflow.
- Tickets/pass list = game-day guest access workflow.
- Per diem = internal finance/roster/meal workflow.
- Visiting-team intake = bundled host/visitor operations workflow.

The larger product model is:

- Host profile = reusable answers.
- Trip workspace = trip-specific execution.
- Trip requests = open operational questions and confirmations.
- AI = parser, router, drafter, recommender, and memory layer.

---

## Artifact Layer

Example travel documents show that coaches/staff produce final artifacts before uploading to Teamworks or distributing to the team/staff.

CAOV should eventually help generate:

- Travel party documents.
- Hotel rooming lists.
- Day-by-day itineraries/trip packets.
- Export-ready artifacts for downstream distribution.

For MVP v1, the itinerary/trip packet is the first artifact priority. Full travel party and rooming-list automation should be treated as near-future features because they involve sensitive PII.

---

## AI Interaction Model Summary

CAOV should use AI in three layers:

1. Trip Planning Assistance.
2. Data Parsing and Structuring.
3. Learning Loops and Institutional Memory.

For MVP v1, AI should be constrained. The workspace is the product. AI should assist with parsing, drafting, missing-input detection, and itinerary generation after structured workflow foundations exist.

---

## Current Build Priorities

1. Confirm repo/app structure.
2. Establish documentation foundation.
3. Define minimal Supabase schema around schedules, games, trips, contacts, host profiles, trip requests, trip tasks, trip documents, and trip meals.
4. Seed the Santa Clara demo scenario.
5. Build the trip workspace page.
6. Add trip requests/open items.
7. Add missing-input checklist.
8. Add itinerary/trip packet generation placeholder.
9. Add AI parsing/drafting later.

---

## Founder Operating Principle

> Manually prove the job. Then build the system.

The next milestone is not building the full AI operating system for college athletics. The next milestone is proving that one baseball away trip can become a structured operations workspace that saves time, reduces missed details, and creates better trip artifacts.
