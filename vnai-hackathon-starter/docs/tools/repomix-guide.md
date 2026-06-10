# Repomix Guide

Repomix dùng để đóng gói một phần hoặc toàn bộ repo thành context dễ đưa vào ChatGPT, Claude, Gemini hoặc công cụ LLM khác.

Current phase: preparation only. Repomix có thể hữu ích để pack docs/context cho review, nhưng không dùng nó để scaffold app code.

---

## 1. What Repomix is used for

Repomix dùng để:

* Pack repo context cho AI đọc.
* Chọn đúng folder/file thay vì paste thủ công quá nhiều.
* Tạo context cho review, planning, hoặc implementation prompt.
* Giúp AI hiểu docs, module map, API contract, context packs.

---

## 2. When to use Repomix

Dùng Repomix khi:

* Cần gửi nhiều file docs/context cho AI.
* Cần review consistency giữa docs.
* Cần pack một module cùng context pack trước khi code.
* Cần tạo snapshot cho ChatGPT/Claude/Gemini phân tích.

---

## 3. When not to use Repomix

Không dùng Repomix khi:

* Task chỉ cần một file.
* Repo chứa secrets/private data chưa kiểm tra.
* Context pack đã đủ và không cần full repo.
* Gần deadline và việc pack context làm chậm hơn review trực tiếp.

---

## 4. How to pack the whole repo

Example commands, may need adjustment later:

```bash
npx repomix
npx repomix --style markdown
```

Chỉ pack whole repo khi chắc chắn không có secrets/private data và AI cần nhìn toàn cảnh.

---

## 5. How to pack only docs

Example:

```bash
npx repomix --include "docs/**"
```

Dùng khi muốn AI audit team-facing documentation.

---

## 6. How to pack only ai-context

Example:

```bash
npx repomix --include "ai-context/**"
```

Dùng khi muốn AI audit rules, module map, prompt library, context packs.

---

## 7. How to pack docs and ai-context together

Example:

```bash
npx repomix --include "docs/**,ai-context/**"
```

Dùng cho documentation coherence audit hoặc onboarding review.

---

## 8. How to pack one module

Backend API example:

```bash
npx repomix --include "apps/api/**,ai-context/context-packs/backend-api.md"
```

Frontend UI example:

```bash
npx repomix --include "apps/web/**,ai-context/context-packs/frontend-ui.md"
```

During preparation phase, `apps/` may not contain real code yet. In that case, pack docs and context packs only.

---

## 9. How to avoid sending too much context to AI

Before running Repomix:

* Decide the question first.
* Include only related folders/files.
* Include the relevant context pack.
* Include `docs/api-contract.md` for API tasks.
* Exclude secrets, generated files, large binaries, and private data.

If output is too large, narrow it to:

```text
docs/api-contract.md
ai-context/MODULE_MAP.md
ai-context/context-packs/[module].md
related app/package files
```

---

## 10. How to use Repomix output with ChatGPT/Claude/Gemini

Suggested prompt:

```text
This is selected repo context from Repomix.
Use Markdown docs as source of truth.
Do not scaffold app code unless explicitly requested.
Check consistency with MODULE_MAP.md, api-contract.md, and context packs.
Task:
[task]
```

---

## 11. Do not rules

* Do not include `.env` with real values.
* Do not include private user data.
* Do not send more context than needed.
* Do not let AI override source-of-truth docs without explicit update.
* Do not use Repomix output as a substitute for local verification.

---

## 12. Example commands

These are examples and may need adjustment later:

```bash
npx repomix
npx repomix --style markdown
npx repomix --include "docs/**,ai-context/**"
npx repomix --include "apps/api/**,ai-context/context-packs/backend-api.md"
npx repomix --include "apps/web/**,ai-context/context-packs/frontend-ui.md"
```

