# Decisions

This file records durable CAOV product and technical decisions.

## Decision: MVP wedge is away-trip operations workspace

CAOV’s MVP should focus on turning uploaded schedules into away-trip operations workspaces.

Reason: the clearest near-term wedge is schedule upload -> away-trip detection -> operations workspace with known details, missing inputs, owners, confirmations, and itinerary output.

## Decision: Trip requests/open items are first-class MVP objects

Trip requests and open items should be modeled explicitly.

Reason: real trip communication shows that away-trip logistics are request/confirmation workflows involving role handoffs, changing schedules, confirmations, day-of details, and relationship management.

## Decision: CAOV should not start as a generic chatbot

AI should be embedded into structured trip workflows rather than becoming the primary product surface.

Reason: the product value comes from organizing and executing trip operations, not from open-ended chat.

## Decision: CAOV should not position as a Teamworks replacement in MVP

CAOV should initially complement existing athletics systems by focusing on work that still happens outside them.

Reason: the first wedge is cross-school and pre-itinerary operational coordination, not replacing department-wide athletics software.

## Decision: Services like laundry should be modeled as workflows

Services should include request status, owner, cost, payment method, receipt requirements, pickup/drop-off logistics, and day-of execution details.

Reason: real away-trip communication shows that services are negotiated and confirmed through back-and-forth communication, not simply listed as static host-school information.

## Decision: Pass lists and ticket allotments should be modeled as handoff workflows

Pass lists and ticket allotments should be represented as game-day workflows.

Reason: ticket access involves per-game allotments, pass-list preparation, host ticketing ownership, physical handoff location, timing, and repeated execution across each game day.

## Decision: Per diem and travel finance should be modeled as internal workflows

Per diem and trip finance should not be treated as static budget fields.

Reason: per diem depends on travel roster, catered meals, funding method, business-office deadlines, and late-stage trip changes.

## Decision: CAOV should include a structured visiting-team operations intake workflow

Visiting-team operations requests should be categorized, routed, answered, tracked, and reused.

Reason: real host/visitor communication shows that visiting teams ask a recurring bundle of questions about practice, bat testing, laundry, pregame times, parking, meals, tickets, seating, showers, and contacts.

## Decision: CAOV should support generation of final trip artifacts before Teamworks upload or team/staff distribution

CAOV should eventually generate export-ready travel party, rooming list, and itinerary/trip packet artifacts.

Reason: real trip documents show that coaches and staff create travel party, rooming list, and itinerary artifacts before pushing information to Teamworks and the team. CAOV can own the upstream planning, validation, and artifact-generation workflow while treating Teamworks as a downstream distribution system.

## Decision: CAOV should map trip inputs into structured data before generating final artifacts

CAOV should parse and structure schedule files, communications, travel party inputs, rooming needs, meal/per diem plans, and host confirmations before generating final trip artifacts.

Reason: real trip documents show that coaches and staff produce travel party, rooming list, and itinerary artifacts before uploading to Teamworks or distributing to team/staff. CAOV can own the upstream planning, validation, and artifact-generation workflow.

## Decision: Travel party and rooming data should be treated as sensitive

Travel party and rooming list data should require privacy-aware handling.

Reason: these artifacts can include player/staff names, DOBs, mobile numbers, room assignments, and other sensitive travel details.
