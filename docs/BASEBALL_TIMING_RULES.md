# Baseball Timing Rules

## Purpose

CAOV should support reusable baseball timing templates.

Many baseball programs follow a predictable pre-game countdown based on first pitch time. CAOV can use this to generate default itinerary events, suggest arrival/departure timing, and identify missing host confirmations.

The timing rules should be treated as suggested defaults, not verified facts. Users should be able to edit or override them.

## Source Pattern

A Portland Baseball pre-game countdown sheet shows a consistent pre-game structure across game times.

The pattern includes:

- Home team stretch
- Home team batting practice
- Visiting team batting practice
- Home team infield
- Visiting team infield
- Umpire meeting
- National anthem
- First pitch

## Standard Countdown Template

Use first pitch as `T`.

Suggested default rules:

- Home team stretch: `T - 2 hours 30 minutes`
- Home team batting practice: `T - 2 hours` to `T - 1 hour 20 minutes`
- Visiting team batting practice: `T - 1 hour 20 minutes` to `T - 40 minutes`
- Home team infield: `T - 35 minutes`
- Visiting team infield: `T - 25 minutes`
- Umpire meeting: `T - 10 minutes`
- National anthem: `T - 5 minutes`
- First pitch: `T`

## Away-Team MVP View

For the CAOV away-trip MVP, prioritize away-team timing:

- Team arrival at field: user/team preference, often around `T - 3 hours`
- Visiting team batting practice: `T - 1 hour 20 minutes` to `T - 40 minutes`
- Visiting team infield: `T - 25 minutes`
- Umpire meeting: `T - 10 minutes`
- National anthem: `T - 5 minutes`
- First pitch: `T`

## Example: 6:00 PM First Pitch

If first pitch is 6:00 PM, CAOV may suggest:

- 3:00 PM arrive at field, if team preference is 3 hours before first pitch
- 4:40 PM visiting team batting practice begins
- 5:20 PM visiting team batting practice ends
- 5:35 PM visiting team infield
- 5:50 PM umpire meeting
- 5:55 PM national anthem
- 6:00 PM first pitch

## Product Behavior

CAOV should use baseball timing rules to:

- Generate default itinerary events from game time
- Suggest hotel-to-field departure timing
- Create missing-input prompts for host-specific pre-game timing
- Pre-fill pre-game schedule assumptions
- Highlight uncertain timing items for user review

## Verification Rule

Generated timing should be marked as `suggested` or `needs_review` until confirmed by the host school, official game sheet, or user.

Do not represent generated timing as confirmed unless confirmed.

## Data Model Implications

Add conceptual support for timing templates.

Possible future entities:

- `timing_templates`
- `timing_template_events`
- `team_timing_preferences`

Suggested fields for timing template events:

- `sport`
- `template_name`
- `event_type`
- `offset_from_game_start_minutes`
- `duration_minutes`
- `applies_to`
- `source_type`
- `review_status`

Suggested values for `applies_to`:

- `home_team`
- `visiting_team`
- `both`
- `staff`
- `officials`

## MVP Use

For MVP v1, do not overbuild a timing-template system.

Instead:

- Use the baseball timing rules as internal guidance.
- Generate default itinerary events for the Santa Clara demo.
- Mark generated pre-game timing as `needs_review`.
- Allow the user to edit or override timing.
