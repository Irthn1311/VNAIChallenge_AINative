# Shared Types

## Purpose

Future shared request/response types for frontend-backend communication.

## What belongs here

* Types that mirror `docs/api-contract.md`.
* Shared enums or lightweight interfaces.

## What does not belong here

* Backend-only database models.
* Frontend-only component props.
* Types not used by more than one module.

## Future examples

```text
ChatRequest
ChatResponse
UploadResponse
ReportResponse
ImageAnalysisResponse
```

## Notes for AI coding

If API contract changes, update shared types and frontend/backend usage together.

