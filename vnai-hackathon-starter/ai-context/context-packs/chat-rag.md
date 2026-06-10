# Context Pack: Chat RAG

## 1. Purpose

Chat RAG lets users ask questions over uploaded or preloaded documents and receive grounded answers with sources.

Preparation goal: define the module clearly before implementation. No backend or frontend code exists yet.

## 2. Owner

Owner: TBD

Support: Backend/API, AI/RAG, Frontend/UI, Product/Demo

## 3. Related Files

Existing files:

```text
docs/api-contract.md
docs/module-contract-template.md
ai-context/MODULE_MAP.md
ai-context/PROJECT_CONTEXT.md
```

Expected future files:

```text
apps/api/routes/chat.py
apps/api/services/rag_service.py
apps/api/services/llm_service.py
apps/api/services/vector_service.py
apps/api/schemas/chat.py
apps/web/components/chat/ChatWindow.tsx
apps/web/components/chat/MessageBubble.tsx
apps/web/components/chat/SourceCitationCard.tsx
apps/web/app/chat/page.tsx
data/eval/rag_eval_questions.md
```

## 4. Data Flow

```text
User message
  -> Next.js Chat UI
  -> POST /api/chat
  -> FastAPI chat route
  -> RAG retrieval
  -> Prompt + LLM generation
  -> Answer + sources
  -> Frontend displays answer and citations
```

## 5. Input / Output

Input:

```json
{
  "session_id": "string",
  "message": "string",
  "collection_id": "string | null"
}
```

Output:

```json
{
  "answer": "string",
  "sources": [],
  "actions": []
}
```

## 6. API or Integration Contract

Endpoint:

```text
POST /api/chat
```

Source of truth:

```text
docs/api-contract.md
```

Status: Planned

## 7. Dependencies

* Upload Document module.
* Supabase PostgreSQL.
* pgvector.
* Embedding provider.
* LLM provider.
* Prompt templates.
* Evaluation questions.

## 8. Do Not Rules

* Do not answer unsupported questions as facts.
* Do not hide missing sources.
* Do not expose API keys to frontend.
* Do not create another chat endpoint without updating API contract.
* Do not change response schema without updating docs and frontend assumptions.
* Do not hard-code demo answers inside core RAG logic.

## 9. Common Tasks

* Write module contract.
* Define evaluation questions.
* Implement chat route later.
* Implement retrieval later.
* Add source citation UI later.
* Add fallback answer for retrieval/LLM failure.

## 10. Testing Checklist

```text
[ ] Valid question returns answer
[ ] Response includes sources array
[ ] Unsupported question is handled safely
[ ] Empty message is handled
[ ] Retrieval failure returns user-friendly response
[ ] Frontend displays citations
[ ] Demo questions are stable
```

## 11. Demo Relevance

High. Chat RAG is likely the main demo feature for knowledge assistant, policy assistant, business assistant, or education assistant ideas.

Prepare:

* 3 reliable questions.
* 1 unsupported question.
* Preloaded sample document.
* Cached/screenshot fallback.

## 12. AI Coding Instruction

When asking AI to work on this module, include:

```text
Task:
Related files:
docs/api-contract.md endpoint:
Expected answer behavior:
Source/citation requirement:
Do not rules:
Testing checklist:
```

Good prompt:

```text
Implement POST /api/chat according to docs/api-contract.md.
Use the Chat RAG context pack.
Return answer, sources, and actions.
Do not modify upload or frontend files.
Add clear error handling for empty message.
```

