# Codex Instructions for CAOV MVP 1.1

## Purpose of This File

This file defines how Codex should work inside the CAOV MVP 1.1 GitHub repo.

Codex should use this file to understand project rules, implementation expectations, documentation standards, and scope boundaries.

---

# Core Principle

Codex is the implementation engine.

Codex should not independently redefine the product strategy, expand the MVP scope, or invent major architecture without explicit instruction.

Product direction should come from:

1. `README.md`
2. `/docs/CAOV_Context.md`
3. `/docs/MVP_1.1_Spec.md`
4. `/docs/Data_Model.md`
5. The current user task

When there is conflict, prioritize the current explicit user task, then the MVP spec, then the context file, then README.

---

# Project Summary

CAOV is an AI-native college athletics operations platform.

MVP 1.1 focuses on turning a college baseball schedule into structured away-trip operations workspaces.

The primary product flow is:

```text
Team -> Schedule -> Games -> Away Trips -> Trip Workspace -> Logistics, Tasks, Contacts, Documents, Notes
```

The current goal is to build a narrow, demo-ready MVP.

Do not expand into a full athletics department management platform unless explicitly instructed.

---

# Tool Workflow

The committed workflow is:

```text
ChatGPT = planning, strategy, product scope, task definition
Codex = code generation, implementation, refactoring, GitHub commits
GitHub = source of truth for code and documentation
Lovable = frontend/app-building and UI iteration surface
Supabase = backend database and structured data repository
```

Codex should write code and documentation in a way that works well with Lovable and Supabase.

---

# General Rules

Codex should:

- Follow the documented MVP scope.
- Make small, focused changes.
- Avoid large rewrites unless explicitly requested.
- Preserve existing working functionality.
- Keep code readable and simple.
- Prefer clear names over clever abstractions.
- Update documentation when behavior changes.
- Add comments only where helpful.
- Avoid unnecessary dependencies.
- Avoid speculative architecture.
- Keep the University of Portland baseball demo in mind.
- Confirm what changed after each task.

Codex should not:

- Redesign the whole app without permission.
- Add unrelated features.
- Create enterprise admin systems prematurely.
- Add complex auth unless requested.
- Add payment processing.
- Add vendor marketplace functionality.
- Add budget management unless requested.
- Replace the MVP flow with a generic project management app.
- Ignore existing documentation.
- Modify Supabase schema without explicit permission.
- Touch files outside the task scope without explaining why.

---

# Documentation Rules

When asked to create or update documentation:

- Use Markdown.
- Keep headings clear.
- Use plain language.
- Avoid unnecessary jargon.
- Preserve existing project terminology.
- Keep MVP 1.1 narrow.
- Do not add unsupported claims.
- Do not remove important context unless instructed.
- Summarize changes after completion.

Important documentation files:

```text
README.md
/docs/CAOV_Context.md
/docs/MVP_1.1_Spec.md
/docs/Data_Model.md
/docs/Codex_Instructions.md
```

---

# Code Rules

When asked to implement code:

- Inspect the existing repo structure first.
- Identify the framework and package manager before editing.
- Make the smallest reasonable change.
- Keep components focused.
- Use existing styling conventions.
- Use existing file organization when present.
- Avoid introducing unnecessary libraries.
- Avoid breaking Lovable compatibility.
- Avoid hardcoding secrets.
- Use environment variables for Supabase config.
- Prefer typed data structures when the project supports TypeScript.
- Preserve existing build behavior.

Before finishing a code task, Codex should check:

- Did the requested feature get implemented?
- Did I modify only relevant files?
- Did I avoid scope creep?
- Did I preserve existing behavior?
- Are there obvious lint or type issues?
- Does the change align with the MVP spec?

---

# Supabase Rules

Supabase is the system of record for structured product data.

Codex should not modify Supabase schema, migrations, or database configuration unless the task explicitly asks for it.

When asked to work with Supabase, Codex should follow `/docs/Data_Model.md`.

Recommended Supabase-related files may include:

```text
/supabase/migrations
/supabase/seed
/src/lib/supabaseClient.ts
/src/types/database.ts
/src/services
```

Codex should never commit real secrets.

Supabase environment variables should use names such as:

```text
VITE_SUPABASE_URL
VITE_SUPABASE_ANON_KEY
```

or the appropriate framework-specific equivalent.

Codex may create example environment files if requested, but should not include real project keys.

---

# Git and Commit Rules

Codex should make focused commits.

Commit messages should be clear and specific.

Examples:

```text
Add CAOV context documentation
Add MVP 1.1 product spec
Add MVP data model documentation
Add Codex workflow instructions
Create initial Supabase client
Add schedule display component
Add trip workspace layout
```

Avoid vague commit messages such as:

```text
updates
changes
fix stuff
misc
```

When completing a task, Codex should report:

1. Files created or modified.
2. Summary of changes.
3. Whether app code was changed.
4. Whether database or migration files were changed.
5. Any assumptions made.
6. Any follow-up recommendations.

---

# MVP Scope Guardrails

MVP 1.1 should focus on:

- Team context
- Schedule upload or entry
- Schedule display
- Away game detection
- Away series grouping
- Trip workspace generation
- Editable trip logistics
- Tasks and checklist tracking
- Missing information visibility
- Supabase persistence
- University of Portland baseball demo flow

MVP 1.1 should not focus on:

- Multi-sport enterprise rollout
- Full Teamworks replacement
- Payment processing
- Expense reconciliation
- Vendor marketplace
- Advanced permissions
- Native mobile app
- Real-time messaging
- Autonomous booking agents
- Complex AI workflows before the base workflow works

---

# Preferred Build Sequence

When implementing the MVP, the preferred sequence is:

1. Establish documentation and repo structure.
2. Create basic app shell.
3. Create team context.
4. Add schedule input or demo schedule data.
5. Display schedule.
6. Identify away games.
7. Group away games into trips.
8. Generate trip workspace records.
9. Display trip workspace page.
10. Add editable logistics sections.
11. Add tasks/checklist.
12. Persist data in Supabase.
13. Polish demo flow.

Codex should not skip ahead into advanced features unless instructed.

---

# Schedule-to-Trip Logic

The most important product workflow is:

```text
Schedule in -> away trips out
```

For MVP 1.1, trip generation should:

1. Read games from the schedule.
2. Identify games marked as away.
3. Group away games by opponent and nearby dates.
4. Create one trip for each grouped away series.
5. Link included games to that trip.
6. Create default logistics placeholders.
7. Create default task checklist items.
8. Show missing information clearly.

This logic should remain understandable and easy to debug.

---

# Default Trip Workspace Sections

A trip workspace should generally include:

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

Do not remove these sections unless the task explicitly asks for a simplified version.

---

# Default Tasks for a New Trip

When creating a default trip workspace, consider using tasks such as:

- Confirm travel party count
- Confirm flight or bus details
- Confirm hotel reservation
- Confirm ground transportation
- Confirm practice time
- Confirm pregame meal plan
- Confirm postgame meal plan
- Confirm laundry plan
- Confirm pass list
- Confirm host school contact
- Finalize itinerary

These can be adjusted as the product evolves.

---

# Missing Information Philosophy

Missing information should be visible.

Do not hide incomplete logistics.

The product should help users identify what still needs to be completed.

Examples:

- Hotel missing
- Transportation missing
- Meal plan missing
- Practice time missing
- Host contact missing
- Pass list missing
- Travel party count missing

This is a key part of the product value.

---

# AI Usage Guidance

CAOV should eventually become AI-native, but MVP 1.1 should not force AI into places where basic structure is more important.

Use AI only when explicitly requested or when it clearly supports the workflow.

Good future AI use cases:

- Parse uploaded documents
- Extract game details
- Generate draft itineraries
- Identify missing logistics
- Summarize visitor guides
- Suggest checklist items
- Answer questions from trip documents

Do not add AI features prematurely.

---

# Error Handling Expectations

When implementing product features, Codex should include basic error handling.

Examples:

- Schedule upload fails
- CSV has missing columns
- No away games are found
- Trip generation fails
- Supabase insert fails
- Supabase read fails
- Required environment variables are missing

Error messages should be understandable to a non-technical user when displayed in the UI.

---

# Environment Variable Rules

Do not hardcode secrets.

Use environment variables for external services.

For Supabase, use appropriate environment variables such as:

```text
VITE_SUPABASE_URL
VITE_SUPABASE_ANON_KEY
```

If creating `.env.example`, include placeholder values only.

Example:

```text
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

Do not commit `.env` files containing real secrets.

---

# Testing and Validation

When practical, Codex should validate changes by running available checks.

Examples:

```text
npm install
npm run dev
npm run build
npm run lint
npm run test
```

Only run commands that make sense for the discovered project.

If checks are unavailable, Codex should say so.

If checks fail, Codex should summarize the issue and avoid claiming success.

---

# Communication Style

After each task, Codex should provide a concise completion summary.

Recommended format:

```text
Completed.

Files changed:
- path/to/file

Summary:
- Added X
- Updated Y
- Preserved Z

App code changed: Yes/No
Database changes made: Yes/No
Follow-up:
- Optional next step
```

Codex should be direct and specific.

---

# Current Priority

The current priority is to create a clean foundation for CAOV MVP 1.1.

Before major feature development, the repo should contain:

- README.md
- /docs/CAOV_Context.md
- /docs/MVP_1.1_Spec.md
- /docs/Data_Model.md
- /docs/Codex_Instructions.md

Once the documentation foundation is in place, implementation should begin with the schedule-to-trip-workspace flow.
