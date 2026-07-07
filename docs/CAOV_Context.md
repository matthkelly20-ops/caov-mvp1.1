# CAOV Context

## Purpose of This File

This file captures the strategic and product context behind CAOV MVP 1.1.

It is intended to help ChatGPT, Codex, Lovable, future collaborators, and the founder stay aligned on what CAOV is, why it exists, what problem it is solving, and how the current MVP should be approached.

This file should be treated as project context, not as a detailed product requirements document. Specific implementation requirements should live in `MVP_1.1_Spec.md`, `Data_Model.md`, and `Codex_Instructions.md`.

---

# What Is CAOV?

CAOV is an AI-native college athletics operations platform.

The long-term vision is to become a system of action for college athletics operations: a platform that helps athletics staff plan, coordinate, execute, and improve operational workflows.

Unlike a static document repository, CAOV should help users move from fragmented information to structured action.

The initial MVP focuses on one narrow but painful workflow:

> Turning a college baseball schedule into structured away-trip operations workspaces.

---

# Why CAOV Exists

College athletics operations work is fragmented, manual, and highly dependent on individual staff knowledge.

Important information often lives across:

- PDFs
- Emails
- Spreadsheets
- Text messages
- Shared drives
- Static visitor guides
- Prior itineraries
- Coach preferences
- Personal relationships
- Institutional memory

This creates operational burden for staff members responsible for travel, game-day logistics, host-school coordination, player movement, meals, hotels, transportation, pass lists, laundry, practice windows, and internal communication.

The problem is not simply that information is hard to find.

The deeper problem is that information is not organized into an actionable workflow.

CAOV exists to help athletics staff turn operational information into structured, useful, repeatable workspaces.

---

# Founder Context

The founder has direct experience with the target workflow through college baseball operations.

As a former University of Portland baseball graduate assistant, the founder helped coordinate travel and operations tasks such as:

- Bus travel
- Flights
- Hotels
- Host-school logistics
- Laundry
- Practice times
- Pregame timing
- Meals
- Pass lists
- Internal communication
- Day-of-game coordination

This firsthand experience is central to the initial product thesis.

CAOV should not be built as a generic travel app. It should be built from the specific reality of college athletics operations.

---

# Initial Wedge

The initial product wedge is away-trip planning for college baseball.

This is a strong starting point because it is:

- Repeated every season
- Operationally important
- Time-sensitive
- Communication-heavy
- Often manually coordinated
- Easy to understand in a demo
- Familiar to the founder
- Narrow enough for an MVP

The first version should not try to solve all of athletics operations.

It should prove that one repeated workflow can be made meaningfully better.

---

# MVP 1.1 Focus

MVP 1.1 focuses on taking a college baseball schedule and generating organized away-trip workspaces.

The core flow is:

1. A user uploads or enters a schedule.
2. The system identifies away games.
3. The system groups relevant away games into trips or away series.
4. The system creates a workspace for each trip.
5. The user can view, edit, and manage trip logistics.
6. The data persists in Supabase.

The goal is to create a useful and demo-ready first product experience.

The MVP should feel practical before it feels magical.

---

# Target User

The initial target user is a college baseball staff member responsible for operations and travel planning.

This may include:

- Director of Baseball Operations
- Graduate Assistant
- Assistant Coach
- Operations Coordinator
- Athletics travel coordinator
- Sport administrator involved in team travel

This user is typically responsible for coordinating logistics across many people and systems.

They may not own every final decision, but they are often responsible for making sure nothing falls through the cracks.

---

# Initial Demo Scenario

The first demo scenario is based on University of Portland baseball.

The goal is to show how CAOV can help a baseball operations user turn a real or realistic schedule into away-trip planning workspaces.

The demo should feel grounded in actual college baseball operations rather than abstract project management.

A successful demo should make someone with athletics operations experience think:

> "Yes, I understand this. I can see how this would have helped me."

---

# Core Product Thesis

CAOV's core thesis is:

> College athletics operations need a system of action, not just another place to store information.

Most existing workflows rely on scattered documents, manual reminders, and repeated institutional knowledge transfer.

CAOV should help turn fragmented information into:

- Structured data
- Clear trip workspaces
- Visible missing information
- Operational checklists
- Reusable workflows
- Searchable institutional knowledge
- Eventually, AI-assisted planning and execution

The MVP begins with away-trip planning because it has clear inputs and outputs.

---

# What CAOV Is Not Yet

MVP 1.1 is not trying to be:

- A full Teamworks replacement
- A complete travel booking platform
- A payments platform
- A budget management platform
- A vendor marketplace
- A fully autonomous AI agent
- A communication system for every stakeholder
- A multi-sport enterprise athletics platform
- A compliance management system

Those may become future opportunities, but they are out of scope for MVP 1.1.

The current product should stay narrow.

---

# Long-Term Vision

The long-term vision is for CAOV to become an AI-native operating layer for athletics departments.

Future versions may support:

- Multi-sport operations
- Host-school logistics profiles
- Verified visitor information
- Travel party management
- Vendor coordination
- Itinerary generation
- Document extraction
- Communication workflows
- Task automation
- Budget visibility
- Institutional knowledge capture
- AI-assisted decision support
- Cross-school operational coordination

The long-term company may eventually compete with or complement existing athletics operations platforms.

However, the current goal is not to build the full future product.

The current goal is to validate a narrow, high-friction workflow.

---

# AI-Native Product Philosophy

CAOV should be built as an AI-native product, but the MVP should not overuse AI for the sake of AI.

The first principle is:

> Make the workflow structured and useful first. Add intelligence where it clearly reduces burden.

AI should eventually help with:

- Parsing documents
- Extracting logistics details
- Identifying missing information
- Generating trip plans
- Summarizing host-school requirements
- Creating checklists
- Suggesting next steps
- Preserving institutional knowledge
- Answering operational questions

But MVP 1.1 should prioritize reliable structure over impressive automation.

A simple product that correctly turns a schedule into a trip workspace is more valuable than a flashy product that feels unreliable.

---

# System of Action vs. System of Record

CAOV should not only store information.

A basic system of record answers:

> "Where is the information?"

A system of action answers:

> "What needs to happen next?"

CAOV should move toward becoming a system of action by helping users:

- See what trips exist
- See what information is missing
- Know what needs to be completed
- Track logistics by trip
- Reuse prior workflows
- Reduce manual coordination burden
- Eventually trigger or recommend next actions

MVP 1.1 should begin this direction through trip workspaces, task visibility, and missing information fields.

---

# Key Workflow: Schedule to Trip Workspace

The most important MVP workflow is:

> Schedule in -> away trips out.

This means the product should take a schedule and produce structured operational objects.

The user should not have to manually create every trip from scratch.

The product should help identify:

- Which games are away
- Which games belong together
- Which opponent the trip is for
- Which dates the trip covers
- What logistics categories need to be completed
- What information is still missing

This is the core product promise of MVP 1.1.

---

# Product Principles

CAOV should follow these product principles:

1. Start narrow.
2. Build around real athletics operations pain.
3. Make the product useful before making it complex.
4. Treat the schedule as the entry point.
5. Turn fragmented information into structured workspaces.
6. Make missing information visible.
7. Keep the user in control.
8. Avoid fake automation.
9. Optimize for demo clarity.
10. Build toward repeatable workflows.
11. Preserve long-term AI-native direction.
12. Do not overbuild before validation.

---

# Build Principles

CAOV MVP 1.1 should follow these build principles:

1. GitHub is the source of truth for code and documentation.
2. Supabase is the source of truth for structured product data.
3. Lovable is the app-building and frontend iteration surface.
4. Codex is the implementation engine.
5. ChatGPT is the product planning and strategy layer.
6. Product decisions should be documented before implementation.
7. Codex should receive clear, scoped instructions.
8. Avoid large, unfocused rewrites.
9. Keep the data model simple but extensible.
10. Keep demo quality high.
11. Do not let tools invent product architecture independently.
12. Preserve clean documentation as the project evolves.

---

# Current Tool Workflow

The current committed workflow is:

```text
ChatGPT for planning, product strategy, ideation, and task definition
Codex for code generation, implementation, and GitHub pushes
GitHub as the clean source of truth
Lovable for frontend/app building from the GitHub repo
Supabase as the backend database and structured data repository
```
