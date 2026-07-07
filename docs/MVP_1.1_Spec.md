# CAOV MVP 1.1 Product Spec

## Purpose of This File

This file defines the product requirements for CAOV MVP 1.1.

It should be used by ChatGPT, Codex, Lovable, and future collaborators to understand what the MVP must do, what is out of scope, and how success should be evaluated.

This file is more tactical than `CAOV_Context.md`.

---

# MVP 1.1 Summary

CAOV MVP 1.1 is a schedule-to-away-trip-workspace product for college baseball operations.

The core product promise is:

> Give CAOV a college baseball schedule, and it will create organized away-trip operations workspaces.

The MVP should help an operations user identify away games, group them into trips or series, and manage the core logistics required for travel planning.

---

# Primary User

The primary user is a college baseball operations staff member responsible for away-trip planning.

This may include:

- Director of Baseball Operations
- Graduate Assistant
- Assistant Coach
- Athletics travel coordinator
- Sport operations coordinator

The user is responsible for keeping logistics organized and making sure nothing falls through the cracks.

---

# Primary Demo Scenario

The initial demo scenario is University of Portland baseball.

The product should be able to support a realistic baseball schedule and create away-trip workspaces from that schedule.

The demo does not need to represent every sport or every school.

It should feel highly relevant to someone familiar with college baseball operations.

---

# Core User Flow

The primary MVP 1.1 user flow is:

1. User lands on the CAOV app.
2. User creates or selects a team.
3. User uploads or enters a baseball schedule.
4. System parses or stores the schedule.
5. System identifies home, away, and neutral games.
6. System groups away games into trips or away series.
7. System generates trip workspaces.
8. User opens a trip workspace.
9. User reviews core trip details.
10. User fills in logistics fields.
11. User tracks missing information and tasks.
12. User saves changes to Supabase.

---

# Required MVP Features

## 1. Team Setup

The app should support a basic team context.

Minimum fields:

- Team name
- School name
- Sport
- Season year

Example:

- Team name: Portland Pilots Baseball
- School name: University of Portland
- Sport: Baseball
- Season year: 2026

---

## 2. Schedule Input

The app should support schedule input.

Acceptable MVP approaches:

- CSV upload
- Manual table entry
- Preloaded demo schedule
- Structured sample data

The MVP does not need to support every schedule format yet.

Minimum schedule fields:

- Date
- Opponent
- Game time
- Location
- Home/away/neutral status
- Venue, if available
- Notes, if available

---

## 3. Schedule Display

The app should display the schedule in a clean table or list.

The user should be able to see:

- Date
- Opponent
- Time
- Location
- Home/away/neutral status
- Whether a trip workspace exists

The schedule view should make it obvious which games are away games.

---

## 4. Away Game Detection

The system should identify away games from the schedule.

Away games should be eligible for trip workspace creation.

Neutral games may be included later, but for MVP 1.1 the primary focus is away games.

---

## 5. Away Series Grouping

For baseball, multiple away games against the same opponent on nearby dates should be grouped into one away series or trip.

Example:

- Friday game at Santa Clara
- Saturday game at Santa Clara
- Sunday game at Santa Clara

These should be grouped into one trip workspace.

Basic grouping logic may use:

- Same opponent
- Away status
- Dates within a close range
- Same location or venue when available

The grouping does not need to be perfect in MVP 1.1, but it should work for the demo scenario.

---

## 6. Trip Workspace Creation

The system should create a trip workspace from an away game or away series.

Each trip workspace should include:

- Trip name
- Team
- Opponent
- Trip start date
- Trip end date
- Games included
- Destination/location
- Logistics sections
- Task checklist
- Missing information indicators

Example trip name:

University of Portland at Santa Clara Baseball Series

---

## 7. Trip Workspace Page

Each trip should have a dedicated workspace page.

The page should organize information into clear sections.

Recommended sections:

- Overview
- Games
- Travel
- Lodging
- Meals
- Transportation
- Contacts
- Documents
- Tasks
- Missing Information
- Notes

The page should feel like an operations command center for that trip.

---

## 8. Editable Logistics Fields

The user should be able to edit and save basic logistics information.

Minimum editable categories:

### Travel

- Departure date
- Return date
- Departure airport
- Arrival airport
- Airline
- Flight notes

### Lodging

- Hotel name
- Hotel address
- Check-in date
- Check-out date
- Rooming notes

### Meals

- Meal date
- Meal type
- Meal provider
- Budget per person
- Notes

### Transportation

- Transportation provider
- Pickup time
- Dropoff time
- Notes

### Contacts

- Contact name
- Role
- Organization
- Email
- Phone
- Notes

### Notes

- General trip notes

---

## 9. Tasks and Checklist

Each trip workspace should include a basic task list.

Example tasks:

- Confirm hotel reservation
- Confirm bus transportation
- Confirm flight details
- Confirm practice time
- Confirm game-day contact
- Confirm postgame meal
- Confirm pass list
- Confirm laundry plan
- Confirm travel party count
- Confirm itinerary

Each task should support:

- Title
- Status
- Due date, if available
- Notes, if available

Recommended statuses:

- Not started
- In progress
- Complete
- Blocked

---

## 10. Missing Information

The product should make missing information visible.

Examples of missing information:

- Missing hotel
- Missing bus provider
- Missing meal plan
- Missing practice time
- Missing host contact
- Missing pass list
- Missing travel party count

The MVP should not hide incomplete planning data.

A key product value is showing what still needs attention.

---

## 11. Supabase Persistence

The MVP should persist core data in Supabase.

At minimum, the following should be stored:

- Team
- Schedule
- Games
- Trips
- Trip logistics
- Tasks
- Contacts
- Notes

The user should be able to refresh the app and still see previously saved trip workspace data.

---

# Recommended Screens

MVP 1.1 should eventually include the following screens:

## 1. Home / Dashboard

Purpose:

Show the user the current team, schedule status, and generated trips.

Key elements:

- Team name
- Season
- Schedule upload or entry prompt
- List of generated trip workspaces
- Basic status indicators

---

## 2. Schedule Page

Purpose:

Show the uploaded or entered schedule.

Key elements:

- Schedule table
- Home/away/neutral status
- Away game indicators
- Trip creation status
- Button to generate trips, if needed

---

## 3. Trips Page

Purpose:

Show all generated trip workspaces.

Key elements:

- Trip list
- Opponent
- Date range
- Destination
- Completion or missing-info status
- Link to open trip workspace

---

## 4. Trip Workspace Page

Purpose:

Manage the operational details for one away trip.

Key elements:

- Trip overview
- Included games
- Travel logistics
- Lodging logistics
- Meal logistics
- Transportation logistics
- Contacts
- Tasks
- Missing information
- Notes

---

# Out of Scope for MVP 1.1

MVP 1.1 should not include:

- Full travel booking
- Payment processing
- Budget reconciliation
- Expense management
- Full Teamworks replacement functionality
- Multi-department enterprise administration
- Fully autonomous AI agents
- Complex role-based permissions
- Native mobile app
- Real-time chat
- Vendor marketplace
- Contracting workflows
- Compliance workflows
- Advanced reporting dashboards

These may be future opportunities, but they should not distract from the MVP.

---

# Acceptance Criteria

MVP 1.1 should be considered functionally successful when:

1. A team can be created or selected.
2. A schedule can be uploaded, entered, or loaded from demo data.
3. The schedule can be displayed to the user.
4. Away games can be identified.
5. Away games can be grouped into trips or series.
6. Trip workspaces can be generated.
7. A trip workspace can be opened.
8. The user can edit logistics details.
9. The user can create or update tasks.
10. Missing information is visible.
11. Data persists in Supabase.
12. The app can support a realistic University of Portland baseball demo.

---

# Demo Success Criteria

The demo should succeed if a college baseball operations user can understand the product within a few minutes.

The product should make it clear that:

- The schedule is the starting point.
- Away trips are automatically organized.
- Each trip becomes a workspace.
- Missing information is visible.
- The user can manage logistics in one place.
- The workflow could reduce manual coordination burden.

The demo should feel useful, not theoretical.

---

# Product Quality Bar

The MVP should be:

- Simple
- Clear
- Fast to understand
- Grounded in real operations work
- Demo-ready
- Narrow in scope
- Easy to iterate
- Connected to Supabase
- Structured enough for future AI features

The MVP should avoid:

- Overbuilt abstractions
- Complex enterprise features
- Unclear navigation
- Fake AI magic
- Unnecessary dashboards
- Too many user roles
- Scope creep

---

# Initial Build Priority

The recommended initial build priority is:

1. Create team context.
2. Add schedule input or demo schedule data.
3. Display schedule.
4. Identify away games.
5. Group away games into trips.
6. Generate trip workspaces.
7. Display trip workspace page.
8. Add editable logistics sections.
9. Add task checklist.
10. Persist data in Supabase.
11. Polish University of Portland baseball demo.

---

# Key MVP Question

The key MVP question is:

> Can CAOV turn a baseball schedule into useful away-trip operations workspaces?

Everything in MVP 1.1 should support answering that question.
