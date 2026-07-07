# CAOV MVP 1.1 Data Model

## Purpose of This File

This file defines the initial data model for CAOV MVP 1.1.

It should guide Supabase schema design, application data structures, and future migration files.

This is a planning document, not a migration file.

No database changes should be made directly from this file unless a future task explicitly asks for migrations or schema implementation.

---

# Data Model Summary

CAOV MVP 1.1 needs to support the following core product flow:

> Team -> Schedule -> Games -> Away Trips -> Trip Workspace -> Logistics, Tasks, Contacts, Documents, Notes

The data model should stay simple enough for MVP development while remaining extensible for future athletics operations workflows.

---

# Core Entities

The initial core entities are:

1. Teams
2. Schedules
3. Games
4. Trips
5. Trip Games
6. Logistics Items
7. Tasks
8. Contacts
9. Documents
10. Notes

---

# Entity Relationship Overview

Recommended relationship structure:

```text
teams
  └── schedules
        └── games
              └── trip_games
                    └── trips
                          ├── logistics_items
                          ├── tasks
                          ├── contacts
                          ├── documents
                          └── notes
```

A team can have many schedules.

A schedule can have many games.

A trip can include one or more games.

A game can belong to a trip through the `trip_games` join table.

A trip can have many logistics items, tasks, contacts, documents, and notes.

---

# 1. teams

## Purpose

Stores the team or program context.

Example:

University of Portland Baseball.

## Suggested Fields

```text
id uuid primary key
school_name text not null
team_name text not null
sport text not null
season_year integer
created_at timestamp with time zone
updated_at timestamp with time zone
```

## Example Record

```text
school_name: University of Portland
team_name: Portland Pilots Baseball
sport: Baseball
season_year: 2026
```

---

# 2. schedules

## Purpose

Stores a season schedule for a team.

A team may eventually have multiple schedules across seasons.

## Suggested Fields

```text
id uuid primary key
team_id uuid references teams(id)
name text not null
season_year integer
source_type text
source_file_name text
created_at timestamp with time zone
updated_at timestamp with time zone
```

## Source Type Examples

```text
csv_upload
manual_entry
demo_data
pdf_upload
imported
```

## Example Record

```text
name: 2026 Portland Pilots Baseball Schedule
season_year: 2026
source_type: csv_upload
source_file_name: portland_baseball_2026_schedule.csv
```

---

# 3. games

## Purpose

Stores individual games from a schedule.

Games are the raw schedule objects that later become trips.

## Suggested Fields

```text
id uuid primary key
schedule_id uuid references schedules(id)
team_id uuid references teams(id)
opponent text not null
game_date date not null
game_time text
location text
venue text
home_away_neutral text
conference_game boolean
notes text
created_at timestamp with time zone
updated_at timestamp with time zone
```

## home_away_neutral Values

```text
home
away
neutral
unknown
```

## Example Record

```text
opponent: Santa Clara
game_date: 2026-05-08
game_time: 6:00 PM
location: Santa Clara, CA
venue: Stephen Schott Stadium
home_away_neutral: away
conference_game: true
```

---

# 4. trips

## Purpose

Stores generated away-trip workspaces.

A trip may include one game or multiple games.

For baseball, a trip will often represent a weekend away series.

## Suggested Fields

```text
id uuid primary key
team_id uuid references teams(id)
schedule_id uuid references schedules(id)
name text not null
opponent text
destination text
start_date date
end_date date
status text
completion_status text
summary text
created_at timestamp with time zone
updated_at timestamp with time zone
```

## Status Values

```text
draft
active
complete
archived
```

## Completion Status Values

```text
not_started
in_progress
mostly_complete
complete
blocked
```

## Example Record

```text
name: University of Portland at Santa Clara Baseball Series
opponent: Santa Clara
destination: Santa Clara, CA
start_date: 2026-05-07
end_date: 2026-05-09
status: active
completion_status: in_progress
```

---

# 5. trip_games

## Purpose

Join table connecting games to trips.

This supports one trip containing multiple games.

## Suggested Fields

```text
id uuid primary key
trip_id uuid references trips(id)
game_id uuid references games(id)
created_at timestamp with time zone
```

## Example

A Santa Clara away series trip may include three games:

- Friday game
- Saturday game
- Sunday game

Each game gets one `trip_games` record linking it to the same trip.

---

# 6. logistics_items

## Purpose

Stores structured logistics details for a trip.

This allows flexible logistics categories without creating too many separate tables during the MVP.

## Suggested Fields

```text
id uuid primary key
trip_id uuid references trips(id)
category text not null
title text not null
status text
date date
time text
provider text
location text
details text
cost_per_person numeric
total_cost numeric
created_at timestamp with time zone
updated_at timestamp with time zone
```

## Category Values

```text
travel
lodging
meal
transportation
practice
laundry
pass_list
equipment
other
```

## Status Values

```text
missing
planned
confirmed
complete
blocked
```

## Example Records

```text
category: lodging
title: Team Hotel
status: missing
details: Hotel information still needed.
```

```text
category: meal
title: Postgame Dinner
status: planned
date: 2026-05-08
provider: TBD
cost_per_person: 20
details: Catered dinner after game.
```

---

# 7. tasks

## Purpose

Stores trip-specific task checklist items.

Tasks help make CAOV a system of action instead of just a system of record.

## Suggested Fields

```text
id uuid primary key
trip_id uuid references trips(id)
title text not null
description text
status text
priority text
due_date date
assigned_to text
created_at timestamp with time zone
updated_at timestamp with time zone
```

## Status Values

```text
not_started
in_progress
complete
blocked
```

## Priority Values

```text
low
medium
high
urgent
```

## Example Tasks

```text
title: Confirm hotel reservation
status: not_started
priority: high
```

```text
title: Confirm practice time with host school
status: in_progress
priority: high
```

```text
title: Finalize pass list
status: not_started
priority: medium
```

---

# 8. contacts

## Purpose

Stores trip-related contacts.

Contacts may include host school contacts, hotel contacts, transportation providers, internal staff, or travel vendors.

## Suggested Fields

```text
id uuid primary key
trip_id uuid references trips(id)
name text not null
role text
organization text
email text
phone text
notes text
created_at timestamp with time zone
updated_at timestamp with time zone
```

## Example Records

```text
name: Henry Muench
role: Day-of-game travel party contact
organization: University of Portland Baseball
```

```text
name: TBD
role: Host school operations contact
organization: Santa Clara Athletics
```

---

# 9. documents

## Purpose

Stores metadata for trip-related documents.

Actual file storage may use Supabase Storage later.

For MVP 1.1, this table can store document references, links, or placeholders.

## Suggested Fields

```text
id uuid primary key
trip_id uuid references trips(id)
title text not null
document_type text
url text
storage_path text
status text
notes text
created_at timestamp with time zone
updated_at timestamp with time zone
```

## Document Type Examples

```text
schedule
itinerary
visitor_guide
pass_list
rooming_list
meal_order
travel_manifest
host_policy
other
```

## Status Values

```text
missing
uploaded
linked
reviewed
approved
```

## Example Records

```text
title: Santa Clara Visitor Guide
document_type: visitor_guide
status: missing
```

```text
title: Travel Party Manifest
document_type: travel_manifest
status: missing
```

---

# 10. notes

## Purpose

Stores general trip notes.

Notes allow users to capture unstructured information without forcing everything into a rigid schema.

## Suggested Fields

```text
id uuid primary key
trip_id uuid references trips(id)
title text
body text not null
created_by text
created_at timestamp with time zone
updated_at timestamp with time zone
```

## Example Record

```text
title: Coach preference
body: Team prefers postgame catered meals at the hotel when possible.
```

---

# MVP Data Priorities

For MVP 1.1, prioritize getting these objects working:

1. teams
2. schedules
3. games
4. trips
5. trip_games
6. logistics_items
7. tasks

Contacts, documents, and notes are important, but they can be simpler in the first version.

---

# Recommended Initial Supabase Tables

The initial Supabase implementation should likely include:

```text
teams
schedules
games
trips
trip_games
logistics_items
tasks
contacts
documents
notes
```

This is enough to support the MVP while avoiding excessive complexity.

---

# Recommended TypeScript Concepts

The application should eventually define TypeScript types for the core entities.

Recommended types:

```text
Team
Schedule
Game
Trip
TripGame
LogisticsItem
Task
Contact
Document
Note
```

These types should align with Supabase table fields.

---

# Schedule Parsing Requirements

When schedule data is uploaded or entered, the system should attempt to extract:

- Date
- Opponent
- Time
- Location
- Venue
- Home/away/neutral status
- Notes

The system should not assume every field will be present.

Missing fields should be allowed and surfaced to the user.

---

# Trip Generation Requirements

Trip generation should use games where:

```text
home_away_neutral = away
```

Basic trip grouping logic:

1. Find away games.
2. Group games by opponent.
3. Group nearby dates together.
4. Create one trip for each grouped away series.
5. Link games to trips through `trip_games`.
6. Create default logistics items and tasks for each trip.

---

# Default Logistics Items for New Trips

When a new trip is created, the system may create placeholder logistics items.

Recommended defaults:

```text
Travel Details
Team Hotel
Ground Transportation
Pregame Meal
Postgame Meal
Practice Time
Laundry Plan
Pass List
Travel Party Count
```

These can start with status:

```text
missing
```

or:

```text
not_started
```

depending on the category.

---

# Default Tasks for New Trips

When a new trip is created, the system may create default tasks.

Recommended default tasks:

```text
Confirm travel party count
Confirm flight or bus details
Confirm hotel reservation
Confirm ground transportation
Confirm practice time
Confirm pregame meal plan
Confirm postgame meal plan
Confirm laundry plan
Confirm pass list
Confirm host school contact
Finalize itinerary
```

These tasks should start with status:

```text
not_started
```

---

# Missing Information Philosophy

Missing information is not a bug.

It is part of the product.

The system should make missing fields visible so the user knows what still needs to be completed.

Examples:

- No hotel listed
- No transportation provider listed
- No meal plan listed
- No contact listed
- No practice time listed
- No pass list uploaded
- No travel party count entered

The product should help the user see what is incomplete.

---

# Data Model Constraints

For MVP 1.1:

- Keep the schema simple.
- Avoid premature enterprise complexity.
- Avoid complex role-based permissions at first.
- Avoid too many specialized logistics tables.
- Use flexible logistics items where possible.
- Keep records tied to trips.
- Prioritize demo usefulness.
- Preserve a path to future expansion.

---

# Future Data Model Opportunities

Future versions may add:

- Users
- Organizations
- Departments
- Sports
- Rosters
- Travel parties
- Rooming lists
- Vendors
- Host-school profiles
- Venues
- Budgets
- Payments
- Messages
- Approvals
- AI-generated recommendations
- Audit logs
- Permissions
- Multi-school collaboration

These should not be implemented in MVP 1.1 unless explicitly required.

---

# Open Questions

The following questions should be resolved as the MVP matures:

1. Should schedules support multiple file types beyond CSV?
2. Should neutral-site games create trips in MVP 1.1?
3. Should trips belong to one team only, or eventually multiple teams?
4. Should contacts be reusable across trips?
5. Should documents use Supabase Storage immediately or later?
6. Should logistics items remain flexible or become separate tables over time?
7. Should trip completion score be calculated or manually set?
8. Should default tasks be customizable by team or sport?

---

# Implementation Reminder

This file should guide schema creation, but it should not itself create database changes.

Before implementing migrations, review this file against `MVP_1.1_Spec.md`.

The first implemented schema should support the schedule-to-trip-workspace demo and avoid unnecessary complexity.
