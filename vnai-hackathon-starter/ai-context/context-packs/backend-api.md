# Context Pack: Backend API

## 1. Purpose

Backend API is the planned FastAPI service that validates requests, orchestrates AI services, and returns stable responses to the frontend.

## 2. Owner

Owner: Nguyễn Tuấn Tài

Support: Nguyễn Hữu Tri, Lư Hồng Phúc, Lê Thanh Phát

## 3. Related Files

Existing files:

```text
docs/api-contract.md
docs/architecture.md
ai-context/MODULE_MAP.md
```

Expected future files:

```text
apps/api/main.py
apps/api/routes/
apps/api/services/
apps/api/schemas/
apps/api/core/config.py
apps/api/tests/
```

## 4. Data Flow

```text
Frontend request
  -> FastAPI route
  -> Pydantic validation
  -> Service layer
  -> Supabase / AI provider / storage
  -> Structured response
  -> Frontend
```

## 5. Input / Output

Input:

* JSON payloads for chat/report.
* Multipart uploads for documents/images.
* Health check requests.

Output:

* JSON responses matching `docs/api-contract.md`.
* Stable error responses.

## 6. API or Integration Contract

Planned endpoints:

```text
GET /health
POST /api/chat
POST /api/upload
POST /api/report
POST /api/analyze-image
```

Status: Planned

## 7. Dependencies

* FastAPI.
* Pydantic.
* Supabase client.
* LLM/embedding provider.
* File parser/OCR provider if needed.
* Environment variables.

## 8. Do Not Rules

* Do not return undocumented schemas.
* Do not hard-code secrets.
* Do not put UI logic in backend.
* Do not create duplicate routes.
* Do not make `/health` depend on slow AI calls.
* Do not swallow errors without useful messages.

## 9. Common Tasks

* Define schemas.
* Implement health route.
* Implement chat/upload/report/image routes.
* Add service layer.
* Add CORS.
* Add manual smoke tests.

## 10. Testing Checklist

```text
[ ] GET /health returns ok
[ ] Valid requests match API contract
[ ] Invalid requests return clear errors
[ ] CORS works with frontend origin
[ ] Missing env variables fail clearly
[ ] Demo endpoints respond within acceptable time
```

## 11. Demo Relevance

Very high. Backend instability can break the entire demo.

Prepare `/health`, logs, env checklist, and fallback plan.

## 12. AI Coding Instruction

When asking AI to work on backend:

```text
Name the exact endpoint.
Paste the API contract.
Name service files to use or create.
Require validation and documented error response.
Do not modify frontend unless explicitly requested.
```
