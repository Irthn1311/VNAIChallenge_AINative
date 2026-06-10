# AGENTS.md

You are assisting a student hackathon team preparing for Vietnam AI Innovation Challenge 2026.

Current repository phase:

```text
Preparation and documentation only.
```

Do not scaffold real Next.js, FastAPI, Supabase, or application code until the team explicitly switches to implementation phase.

---

## Core Mission

Help the team keep architecture, module contracts, API contracts, AI coding prompts, and demo workflow consistent.

The future stack is:

* Next.js frontend
* FastAPI backend
* Supabase PostgreSQL
* Supabase pgvector first
* Optional CV/OCR
* Vercel frontend deployment
* Railway/Render backend deployment

---

## Core Rules

1. Follow `PROJECT_CONTEXT.md`, `CODING_RULES.md`, `MODULE_MAP.md`, and the relevant context pack.
2. Respect `docs/api-contract.md`.
3. Keep changes minimal and localized.
4. Do not create duplicate modules, routes, services, or components.
5. Do not change unrelated files.
6. Do not hard-code secrets, tokens, API keys, or private data.
7. Do not break demo-critical flows.
8. If requirements are unclear, make the safest minimal assumption and document it.
9. Prefer documentation, contracts, and planning in preparation phase.
10. Do not install packages unless explicitly requested.

---

## Before Editing

Always identify:

* What phase is the repo in?
* What module is affected?
* Who owns the module?
* What files are related?
* What API contract applies?
* What input and output are expected?
* What should not be changed?
* What manual test or review is needed?

For complex tasks, ask for or generate a context pack first.

---

## After Editing

Always provide:

* Changed files.
* Summary of changes.
* How to review or test.
* Risks or follow-up tasks.
* Whether API contract, module map, or context pack changed.

---

## Priority During Hackathon

Prioritize:

1. Working demo.
2. Stable integration.
3. Clear user flow.
4. Simple code.
5. Useful documentation.
6. Future scalability only after the demo is safe.

Do not over-engineer.

