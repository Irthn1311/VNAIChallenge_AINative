# MODULE_MAP.md

This file maps planned modules to responsibilities, owners, integration points, and context packs.

Update this file when:

* A module is added, removed, or renamed.
* Ownership changes.
* API contract changes.
* Demo-critical flow changes.

Current phase: preparation only. Paths below may be expected future files.

Role assignment source:

```text
docs/team-role-assignment.md
```

Owner note:

Official role owners are now filled for onboarding. If the team changes owner assignments later, update `docs/team-role-assignment.md`, this file, and related module contracts/context packs together.

Current role owners:

```text
Technical Lead / Integration Lead: Nguyễn Hữu Tri
AI/RAG/CV Lead: Lư Hồng Phúc
Frontend/Backend Software Developer: Nguyễn Tuấn Tài
Product Flow / Demo / Pitch Support: Lê Thanh Phát
```

---

## 1. Frontend UI

Path:

```text
apps/web
```

Owner:

```text
Nguyễn Tuấn Tài
```

Support:

```text
Lê Thanh Phát / Nguyễn Hữu Tri
```

Context pack:

```text
ai-context/context-packs/frontend-ui.md
```

Responsibilities:

* App layout.
* Chat UI.
* Upload UI.
* Report/dashboard screen.
* API calls to FastAPI backend.
* Loading, empty, error states.

Integration points:

```text
GET /health
POST /api/chat
POST /api/upload
POST /api/report
POST /api/analyze-image
```

Do not:

* Store backend secrets.
* Hard-code final AI responses except clearly marked fallback/demo fixtures.
* Change API assumptions without updating `docs/api-contract.md`.

---

## 2. Backend API

Path:

```text
apps/api
```

Owner:

```text
Nguyễn Tuấn Tài
```

Support:

```text
Nguyễn Hữu Tri / Lư Hồng Phúc
```

Context pack:

```text
ai-context/context-packs/backend-api.md
```

Responsibilities:

* FastAPI routes.
* Request validation.
* Response schema stability.
* Service orchestration.
* Supabase connection.
* AI/RAG/CV integration.

Do not:

* Return undocumented response formats.
* Create duplicate endpoints.
* Put frontend UI logic here.
* Hide deployment errors during demo.

---

## 3. Chat RAG

Path:

```text
apps/api/services/rag
apps/web/components/chat
```

Owner:

```text
Lư Hồng Phúc
```

Support:

```text
Nguyễn Hữu Tri / Nguyễn Tuấn Tài / Lê Thanh Phát
```

Context pack:

```text
ai-context/context-packs/chat-rag.md
```

API:

```text
POST /api/chat
```

Responsibilities:

* Retrieve relevant chunks.
* Build prompt with context.
* Generate answer.
* Return sources.
* Handle unsupported questions safely.

---

## 4. Upload Document

Path:

```text
apps/api/routes/upload.py
apps/api/services/document_service.py
apps/web/components/upload
```

Owner:

```text
Nguyễn Tuấn Tài
```

Support:

```text
Lư Hồng Phúc / Nguyễn Hữu Tri
```

Context pack:

```text
ai-context/context-packs/upload-document.md
```

API:

```text
POST /api/upload
```

Responsibilities:

* Validate file.
* Store file or metadata.
* Extract text if supported.
* Prepare document for RAG.

---

## 5. CV / OCR

Path:

```text
apps/api/services/cv
apps/web/components/image-analysis
```

Owner:

```text
Lư Hồng Phúc
```

Support:

```text
Nguyễn Tuấn Tài / Lê Thanh Phát
```

Context pack:

```text
ai-context/context-packs/cv-ocr.md
```

API:

```text
POST /api/analyze-image
```

Responsibilities:

* Validate image input.
* Run OCR or CV model/API.
* Return structured result, confidence, and explanation.

Do not:

* Make optional CV block the main demo.
* Depend on heavy local-only models unless tested.

---

## 6. Report / Demo Flow

Path:

```text
docs/
data/samples/
data/eval/
apps/web/report
apps/api/services/report_service.py
```

Owner:

```text
Lê Thanh Phát
```

Support:

```text
Nguyễn Hữu Tri / Nguyễn Tuấn Tài / Lư Hồng Phúc
```

Context pack:

```text
ai-context/context-packs/demo-flow.md
```

API:

```text
POST /api/report
```

Responsibilities:

* Problem statement.
* User journey.
* Demo script.
* Sample data.
* Evaluation questions.
* Pitch outline.
* Fallback plan.

Do not:

* Keep demo flow only in chat messages.
* Use random untested demo data.
* Change demo path right before presentation.
