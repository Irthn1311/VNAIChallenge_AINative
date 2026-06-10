# DECISIONS.md

This file records important technical and product decisions.

Use this format:

```markdown
## Decision XXX: Title

Date:
Status: Proposed / Accepted / Rejected / Replaced

Decision:
...

Reason:
...

Impact:
...

Follow-up:
...
```

---

## Decision 001: Use Next.js + FastAPI + Supabase

Date: 2026-06-10
Status: Accepted

Decision:

Use Next.js for frontend, FastAPI for backend, and Supabase PostgreSQL for database.

Reason:

* Next.js is suitable for fast UI development and Vercel deployment.
* FastAPI is suitable for Python-based AI/RAG/CV services.
* Supabase provides PostgreSQL, storage, and pgvector support.
* This architecture separates frontend, backend, and AI logic clearly.

Impact:

* Need to manage CORS.
* Need to maintain API contracts.
* Need to deploy frontend and backend separately.
* Need clear `.env.example`.

Follow-up:

* Keep API contracts updated before coding.
* Scaffold only after preparation phase is accepted.

---

## Decision 002: Use pgvector First

Date: 2026-06-10
Status: Accepted

Decision:

Use Supabase pgvector as the first vector search option. Consider Qdrant only if pgvector is not enough for the actual problem.

Reason:

* Fewer services to deploy.
* Simpler demo architecture.
* Good fit for small hackathon datasets.

Impact:

* Vector search design should stay simple.
* RAG scale is acceptable for MVP, not optimized for large production data.

Follow-up:

* Document table and embedding schema during implementation phase.

---

## Decision 003: Preparation Before Scaffolding

Date: 2026-06-10
Status: Accepted

Decision:

Finish documentation, contracts, context packs, and team workflow before creating real app code.

Reason:

* Reduces AI-generated architecture drift.
* Helps students onboard faster.
* Makes module ownership clearer before pressure starts.

Impact:

* Current repo may contain placeholder app folders without code.
* Setup commands remain planned until implementation phase.

Follow-up:

* Assign module owners.
* Run mock tasks.
* Then scaffold Next.js and FastAPI.

---

## Decision 004: Use AI Coding With Context Packs

Date: 2026-06-10
Status: Accepted

Decision:

Every non-trivial AI coding task should include the relevant context pack and API contract.

Reason:

* AI tools perform better with concrete file boundaries.
* Prevents duplicate routes, mismatched schemas, and unrelated edits.

Impact:

* Context packs must stay updated.
* PR template asks whether the context pack was read or updated.

Follow-up:

* Team members practice by writing one module contract each.

