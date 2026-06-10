# AI Core

## Purpose

Future shared AI utilities if logic becomes reusable across apps or services.

## What belongs here

* Embedding helpers.
* Prompt formatting helpers.
* Retrieval utilities.
* Evaluation helpers.
* Provider wrappers, if reused.

## What does not belong here

* FastAPI route handlers.
* Frontend components.
* App-specific one-off services.
* Secrets.

## Future examples

```text
embeddings/
retrieval/
providers/
evaluation/
```

## Notes for AI coding

Keep AI logic inside `apps/api/services/` first. Move here only when reuse is clear.

