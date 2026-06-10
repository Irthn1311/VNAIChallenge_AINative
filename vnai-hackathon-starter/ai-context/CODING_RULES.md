# CODING_RULES.md

These rules guide future implementation. During preparation phase, apply them to documentation, contracts, and context packs.

---

## 1. Preparation Phase Rules

1. Do not scaffold Next.js or FastAPI until explicitly approved.
2. Do not install packages.
3. Keep changes focused on Markdown documentation.
4. Preserve useful existing content.
5. Mark future code files as `expected future file`.
6. Keep docs practical for a student hackathon team.
7. Do not write fake implementation status.

---

## 2. General Coding Rules

1. Keep code simple and readable.
2. Prefer a working MVP over complex architecture.
3. Do not create duplicate utilities or duplicate services.
4. Do not hard-code secrets.
5. Use environment variables for credentials and URLs.
6. Keep API response formats stable.
7. Update documentation when changing API contracts.
8. Add error handling for demo-critical flows.
9. Test manually before opening a pull request.
10. Do not commit broken code to `main`.

---

## 3. Frontend Rules

1. Use Next.js conventions.
2. Keep UI components focused.
3. Use loading, empty, and error states.
4. Do not put backend business logic in frontend.
5. Do not expose secret API keys.
6. Match API response types defined in `docs/api-contract.md`.

---

## 4. Backend Rules

1. Use FastAPI routes clearly.
2. Keep route handlers thin when possible.
3. Put business logic in services.
4. Validate request payloads.
5. Return documented response structures.
6. Add `/health` endpoint for deployment checks.
7. Do not bypass service layers.
8. Do not put frontend-specific logic in backend.

---

## 5. AI / RAG Rules

1. RAG responses should include sources when possible.
2. Do not hallucinate unsupported claims.
3. If answer is not found in data, say so clearly.
4. Keep prompts versioned in `packages/prompts` or backend prompt files.
5. Keep retrieval, prompting, and generation logically separated.
6. Add evaluation questions in `data/eval`.

---

## 6. Demo Rules

1. Demo path must be tested before presentation.
2. Use stable sample data.
3. Prepare cached response or screenshot fallback.
4. Do not refactor near final demo time.
5. Do not add large features after feature freeze.

