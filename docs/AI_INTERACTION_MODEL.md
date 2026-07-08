# CAOV AI Interaction Model

**Version:** v0.2  
**Purpose:** Define how CAOV should use AI across the product without becoming a generic chatbot or over-automated planning tool.

## Core Principle

CAOV should use AI to support structured athletics operations workflows.

The product should not be “chat with your trip.”

The product should be:

> A structured away-trip operations workspace with AI assistance layered into the moments where parsing, planning, recommendation, summarization, drafting, and memory are useful.

AI should not be the source of truth. The source of truth should be structured data, verified documents, user-approved inputs, and historical trip records.

## Three AI Layers

### 1. Trip Planning Assistance

AI can help users plan and communicate inside a trip workspace.

Examples:

- Draft host/visitor emails.
- Identify missing trip details.
- Generate itinerary text from structured data.
- Suggest meal/vendor options later.
- Flag timing or logistics conflicts.
- Summarize host information.

For MVP v1, this layer should be limited and grounded in structured trip data.

### 2. Data Parsing and Structuring

AI can help convert messy inputs into structured CAOV data.

Inputs may include:

- Schedule spreadsheets.
- PDF schedules.
- Visitor guides.
- Email threads.
- Itineraries.
- Travel party documents.
- Rooming lists.
- Confirmation documents.

AI should help extract:

- Games.
- Away trips.
- Contacts.
- Requests/open items.
- Host policies.
- Travel details.
- Meals/per diem notes.
- Itinerary events.

All parsed data should require review before becoming verified.

### 3. Learning Loops and Institutional Memory

Over time, CAOV should learn from past trips.

Examples:

- What hotel was used last time.
- Which host contact owned laundry.
- Which vendors worked well.
- What timing was too tight.
- Which details changed year over year.
- Which host answers can be reused.

This should not be overbuilt in MVP v1, but the data model should make it possible later.

## Functional AI Categories

### Extraction AI

Turns unstructured documents into suggested structured fields.

Output should include:

- Extracted value.
- Suggested field.
- Source reference.
- Confidence/review status.

### Recommendation AI

Helps users make planning decisions.

Examples:

- Meal options.
- Hotel/location suggestions.
- Travel timing checks.
- Budget-aware suggestions.

This should come after the structured workspace exists.

### Generation AI

Creates operational artifacts.

Examples:

- Itinerary/trip packet draft.
- Email drafts.
- Missing-input summaries.
- Internal handoff notes.

### Memory AI

Uses prior trip data to improve future planning.

Examples:

- “What did we do last time?”
- “Which host owner handled this?”
- “What should we reuse or avoid?”

## MVP Guardrails

For MVP v1:

- Build the structured trip workspace first.
- Build trip requests/open items before AI chat.
- Do not build a generic chatbot-first UI.
- Do not let AI hide uncertainty.
- Do not mark AI suggestions as verified without review.
- Use AI to assist, not replace, operations judgment.

## One-Sentence Summary

CAOV should use AI to convert messy athletics operations inputs into structured trip workflows, assist staff with planning decisions, and learn from each completed trip so future trips become easier, smarter, and less manual.
