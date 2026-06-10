# Context Pack: Frontend UI

## 1. Purpose

Frontend UI is the planned Next.js app that users interact with during demo.

It should make AI features easy to understand: upload, chat, report, image analysis, loading states, and clear errors.

## 2. Owner

Owner: TBD

Support: Product/Demo, Backend/API, AI/RAG

## 3. Related Files

Existing files:

```text
docs/api-contract.md
docs/demo-script.md
ai-context/MODULE_MAP.md
```

Expected future files:

```text
apps/web/app/
apps/web/components/
apps/web/lib/api-client.ts
apps/web/components/chat/
apps/web/components/upload/
apps/web/components/report/
apps/web/components/image-analysis/
packages/ui/
packages/shared-types/
```

## 4. Data Flow

```text
User action
  -> UI component
  -> API client
  -> FastAPI endpoint
  -> Response or error
  -> UI state update
```

## 5. Input / Output

Input:

* User text.
* Uploaded file.
* Button/select actions.
* Demo sample choices.

Output:

* AI answer.
* Source citations.
* Upload status.
* Report content.
* Image/OCR result.
* Clear error messages.

## 6. API or Integration Contract

Frontend must follow:

```text
docs/api-contract.md
GET /health
POST /api/chat
POST /api/upload
POST /api/report
POST /api/analyze-image
```

Status: Planned

## 7. Dependencies

* Next.js.
* Tailwind CSS.
* shadcn/ui.
* Lucide icons.
* Backend API.
* Shared API types if created later.

## 8. Do Not Rules

* Do not store backend secrets in frontend.
* Do not bypass API contract.
* Do not hide API errors from users.
* Do not hard-code final demo outputs unless marked as fallback.
* Do not create page flows that cannot be demoed.

## 9. Common Tasks

* Draft UI flow.
* Build chat screen later.
* Build upload screen later.
* Build report/demo screen later.
* Add loading/error/empty states.
* Connect API client later.

## 10. Testing Checklist

```text
[ ] Main demo flow is visible without explanation
[ ] Loading state appears during API call
[ ] Error state is clear
[ ] Empty state helps user continue
[ ] Mobile or presentation screen size is acceptable
[ ] API base URL is configurable
```

## 11. Demo Relevance

Very high. The frontend is what judges see first.

Keep the UI simple, stable, and readable on the presentation screen.

## 12. AI Coding Instruction

When asking AI to work on frontend:

```text
Include the exact screen/component.
Include API contract.
Include loading/error/empty behavior.
Say whether mock data or real API call is expected.
Do not allow backend logic in frontend.
```

