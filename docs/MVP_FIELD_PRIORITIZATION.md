# MVP Field Prioritization

## Purpose

This file explains how CAOV should avoid turning the Santa Clara demo data sheet into a long user-facing setup form.

The internal product model may need to manage many operational details, but the user should not see a 90-field trip setup form.

## Product Principle

Use progressive disclosure.

The MVP should surface the information an operations user needs to act:

- what is confirmed
- what is missing
- what needs follow-up
- who owns it
- what goes into the itinerary/trip packet

Detailed fields should appear only when relevant, when a user expands a section, or when a field is needed to resolve an open item.

## Primary Sections

The primary MVP sections should be:

- Trip Setup
- Schedule / Games
- Travel
- Hotel
- Meals / Per Diem
- Host Logistics
- Requests / Open Items
- Contacts
- Documents
- Missing Inputs
- Itinerary / Trip Packet

## Default View

The default trip workspace view should show:

- confirmed summary
- missing inputs
- open requests
- upcoming deadlines
- itinerary preview

This gives the user a useful operational dashboard without forcing them through every possible field.

## Hide By Default

Hide these by default:

- low-priority future fields
- internal calculations
- not-applicable fields
- detailed PII-heavy artifacts
- finance closeout fields until needed

## Field Visibility Guidance

Use these visibility levels:

- `primary`: shown in the default workspace because it affects current planning or the trip packet.
- `collapsed`: available inside an expanded section when relevant.
- `internal`: used for calculations, status, parsing, or review but not presented as a normal input.
- `future`: retained as product direction but not implemented in MVP v1.
- `not_applicable`: hidden or removed for the current trip.

## MVP User Experience Rule

The MVP should feel like an operations workspace, not a spreadsheet recreated as a form.

The product should help the user move from scattered trip information to:

- structured sections
- clear missing inputs
- request/confirmation tracking
- reusable host knowledge
- a coach-ready trip packet

If a field does not help the user understand the trip, resolve an open item, or generate the trip packet, it should usually be collapsed, internal, future, or not applicable.
