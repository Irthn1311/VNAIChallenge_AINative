# UI Package

## Purpose

Future shared UI components used by the frontend.

## What belongs here

* Reusable buttons, cards, panels, empty states, loading states.
* Shared display components used by more than one screen.

## What does not belong here

* Page-specific business logic.
* Backend API calls.
* Prompt or AI logic.

## Future examples

```text
Button.tsx
MetricCard.tsx
SourceCitationCard.tsx
ErrorState.tsx
```

## Notes for AI coding

Only move components here when reuse is real. Do not over-abstract during the first MVP.

