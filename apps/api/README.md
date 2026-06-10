# API App

## Purpose

Planned FastAPI backend for routes, validation, service orchestration, AI/RAG/CV integration, and Supabase access.

Current status: preparation only. No FastAPI app has been scaffolded yet.

## What belongs here

* Future FastAPI app entrypoint.
* Routes.
* Schemas.
* Services.
* Backend tests.
* Config loading.

## What does not belong here

* Frontend UI code.
* Hard-coded secrets.
* Random notebooks.
* Response schemas not documented in `docs/api-contract.md`.

## Future examples

```text
main.py
routes/chat.py
routes/upload.py
services/rag_service.py
schemas/chat.py
core/config.py
```

## Notes for AI coding

Read `ai-context/context-packs/backend-api.md` before editing future backend code. Keep `/health` lightweight and keep all endpoint responses aligned with `docs/api-contract.md`.

