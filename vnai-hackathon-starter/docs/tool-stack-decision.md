# Tool Stack Decision

Tài liệu này ghi lại tool và stack team đã chọn để tránh tranh luận lại khi vào hackathon.

---

## 1. Final tool list

| Tool | Used for | Should not be used for |
| --- | --- | --- |
| GitHub | Source code, branches, PR, review | Chat thay thế docs |
| Zalo | Trao đổi nhanh, alert | Lưu quyết định dài hạn |
| Docs / Notion / OneNote | Planning, task notes | Source of truth cho code contract |
| Canva | Pitch deck | Technical documentation |
| ChatGPT Plus | Planning, prompt design, docs, review | Blind code changes without repo context |
| Codex | Repo-aware editing, implementation, tests | Uncontrolled broad scaffolding |
| Gemini / Antigravity | Fast generation, alternative suggestions | Direct unreviewed merge |
| Claude | Reasoning, refactor review, long-form docs | Replacing repo source-of-truth |
| GitNexus | Codebase graph, onboarding | Secret storage |
| CodeGraph | Module/dependency understanding | Replacing manual review |
| Repomix | Packing repo context for LLMs | Sending secrets/private data |

---

## 2. Final technical stack

* Frontend: Next.js
* Backend: FastAPI
* Database: Supabase/PostgreSQL
* Vector search: pgvector first
* Frontend deploy: Vercel
* Backend deploy: Railway/Render

---

## 3. Why Option B was chosen

Option B:

```text
Next.js frontend + FastAPI backend + Supabase/PostgreSQL
```

Chosen because:

* Frontend and backend responsibilities are clear.
* Python backend fits AI/RAG/CV work.
* Supabase reduces database/storage setup time.
* Vercel is fast for frontend deploy.
* Railway/Render are simple enough for backend deploy.
* pgvector avoids adding a separate vector database too early.

Tradeoff:

* Two deployments instead of one.
* Need CORS and env management.
* Need stronger API contract discipline.

---

## 4. Risks

## CORS

Risk:

Frontend on Vercel may fail to call backend if CORS is not configured.

Mitigation:

* Define allowed origins.
* Test deployed frontend against deployed backend early.

## Env management

Risk:

Different env values across local, Vercel, Railway/Render, Supabase.

Mitigation:

* Keep `.env.example` updated.
* Never commit real secrets.
* Assign one person to deployment env checklist.

## API contract mismatch

Risk:

Frontend expects one schema while backend returns another.

Mitigation:

* Update `docs/api-contract.md` first.
* Review PRs for API impact.
* Use shared types later if needed.

## Two deployments

Risk:

Frontend works but backend is down, or backend works but frontend points to wrong URL.

Mitigation:

* Add `/health`.
* Warm up deployments before demo.
* Prepare local/screenshot fallback.

---

## 5. Current status

Accepted for preparation.

Implementation starts only after documentation, module contracts, and mock tasks are complete.

