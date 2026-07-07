# caov-mvp1.1
6Jul2026 MVP 1.1 Build Out
# CAOV MVP 1.1

CAOV is an AI-native college athletics operations platform.

The initial MVP focuses on helping college baseball programs turn a season schedule into structured away-trip operations workspaces.

The long-term vision is to build a system of action for college athletics operations: a platform that does not just store information, but helps staff plan, coordinate, execute, and continuously improve operational workflows.

---

## MVP 1.1 Goal

The goal of MVP 1.1 is to let a user upload or enter a college baseball schedule and automatically generate organized workspaces for away trips.

Each trip workspace should help an operations user manage the core logistics around an away series, including:

- Game details
- Opponent information
- Travel dates
- Lodging
- Meals
- Transportation
- Contacts
- Documents
- Tasks and checklists
- Missing information

MVP 1.1 should feel like the first useful version of an athletics operations command center.

---

## Initial User

The first target user is a college baseball operations staff member, director of operations, graduate assistant, or coach responsible for away-trip planning.

The initial product is designed around the real-world workflow of a college baseball staff member who needs to coordinate away-game logistics across coaches, players, host schools, travel vendors, and internal athletics staff.

The first demo scenario is based on University of Portland baseball travel.

---

## Core Product Thesis

College athletics operations work is fragmented across PDFs, emails, spreadsheets, texts, shared drives, static visitor guides, and personal knowledge.

CAOV should help turn that fragmented information into a structured, queryable, and actionable workspace.

The MVP starts with away-trip planning because it is a specific, painful, repeated workflow with clear inputs, outputs, and operational stakes.

---

## Product Scope

MVP 1.1 should support:

- Schedule upload or manual schedule entry
- Away-game detection
- Away-series grouping
- Trip creation from away games or away series
- Trip workspace generation
- Editable logistics fields
- Basic task and checklist tracking
- Persistent storage in Supabase
- A polished frontend suitable for demo conversations
- A realistic University of Portland baseball demo flow

MVP 1.1 should not attempt to fully automate:

- Booking travel
- Processing payments
- Managing budgets end-to-end
- Replacing Teamworks
- Coordinating every sport
- Handling enterprise-wide athletics operations
- Running fully autonomous AI agents without human review

The goal is not to build the whole company in this version.

The goal is to prove that a schedule can become an organized, useful operations workspace.

---

## Demo Outcome

A successful MVP 1.1 demo should show that a user can:

1. Upload or enter a college baseball schedule.
2. Automatically identify away games.
3. Group away games into trip workspaces.
4. Open an individual trip workspace.
5. View core trip information.
6. Add or edit logistics details.
7. Track missing information and operational tasks.
8. Save the workspace in Supabase.
9. Understand how this could reduce manual coordination work for athletics staff.

The demo should make the product feel practical, grounded, and immediately understandable to someone who has worked in college athletics operations.

---

## Technical Stack

- Planning, strategy, and product direction: ChatGPT
- Code generation and repo edits: Codex
- Source of truth for code and documentation: GitHub
- Frontend and app-building surface: Lovable
- Backend database and structured data repository: Supabase

---

## Working Model

ChatGPT is used for product thinking, planning, scope control, documentation, and task definition.

Codex is used to implement clearly scoped code changes, create files, refactor code, generate migrations, and push updates to GitHub.

GitHub is the canonical source of truth for the codebase and project documentation.

Lovable is used to build, render, and iterate on the application experience using the connected GitHub repo.

Supabase is used as the system of record for structured product data, including schedules, games, trips, logistics, tasks, contacts, and documents.

---

## Project Structure

```text
/docs
  CAOV_Context.md
  MVP_1.1_Spec.md
  Data_Model.md
  Codex_Instructions.md

/src
  App source code

/supabase
  Migrations, seed data, and database-related files
