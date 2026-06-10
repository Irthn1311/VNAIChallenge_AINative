# Team Onboarding Guide

Hướng dẫn này dành cho thành viên mới trước khi bắt đầu contribute.

---

## 1. Repo này dùng để làm gì?

Repo này là starter cho team Vietnam AI Innovation Challenge 2026. Hiện tại repo dùng để chuẩn bị:

* Workflow làm việc.
* Module contracts.
* API contracts.
* Context packs cho AI coding.
* Demo và pitch checklist.

Đây chưa phải app thật.

---

## 2. Current phase

Current phase:

```text
Preparation, not coding.
```

Không scaffold Next.js, FastAPI, Supabase hoặc install package cho đến khi team thống nhất chuyển phase.

---

## 3. Tool stack

* GitHub: code, PR, review.
* Zalo: trao đổi nhanh.
* Docs/Notion/OneNote: planning.
* Canva: pitch deck.
* ChatGPT Plus, Codex, Gemini/Antigravity, Claude: AI support.
* GitNexus, CodeGraph, Repomix: hiểu repo và đóng gói context.

Stack dự kiến:

* Next.js frontend.
* FastAPI backend.
* Supabase/PostgreSQL.
* pgvector.
* Vercel.
* Railway/Render.

---

## 4. Folder overview

```text
docs/        - team-facing documentation
ai-context/  - AI-facing rules and context packs
apps/        - future frontend/backend apps
packages/    - future shared packages
data/        - sample, seed, eval data
scripts/     - future setup/eval/index scripts
```

---

## 5. How to read the repo

Recommended order:

1. `README.md`
2. `docs/team-workflow.md`
3. `docs/tool-stack-decision.md`
4. `docs/preparation-roadmap.md`
5. `docs/team-role-assignment.md`
6. `docs/definition-of-done.md`
7. `ai-context/MODULE_MAP.md`
8. `ai-context/PROMPT_LIBRARY.md`
9. `docs/tools/codebase-context-workflow.md`
10. Related context pack
11. `docs/module-contract-template.md`

---

## 6. How to receive a task

Khi nhận task, hãy xác định:

* Module nào?
* Owner là ai?
* File nào liên quan?
* API contract nào?
* Có ảnh hưởng demo không?
* Done khi nào?

Nếu task mơ hồ, hỏi lại trước khi code.

---

## 7. How to write a module contract

Dùng [module-contract-template.md](module-contract-template.md).

Mỗi contract cần có:

* Module name.
* Owner/support.
* Purpose.
* Input/output.
* API/integration.
* Related files.
* Dependencies.
* Do not rules.
* Testing checklist.
* Demo relevance.

---

## 8. How to use AI coding safely

Trước khi prompt AI:

* Đưa task rõ ràng.
* Đưa context pack.
* Đưa API contract.
* Ghi constraints.
* Yêu cầu không sửa file ngoài scope.

Sau khi AI sửa:

* Review diff.
* Test thủ công.
* Cập nhật docs nếu contract thay đổi.

---

## 9. How to use context packs

Context pack là file ngắn giúp AI hiểu module.

Khi làm module nào, đọc file tương ứng:

```text
ai-context/context-packs/chat-rag.md
ai-context/context-packs/upload-document.md
ai-context/context-packs/frontend-ui.md
ai-context/context-packs/backend-api.md
ai-context/context-packs/demo-flow.md
ai-context/context-packs/cv-ocr.md
```

Nếu context pack sai hoặc thiếu, cập nhật trước khi code.

---

## 10. How to use codebase context tools

For codebase context workflow, read:

* [tools/codebase-context-workflow.md](tools/codebase-context-workflow.md)
* [tools/codegraph-guide.md](tools/codegraph-guide.md)
* [tools/gitnexus-guide.md](tools/gitnexus-guide.md)
* [tools/repomix-guide.md](tools/repomix-guide.md)

Tóm tắt:

* GitNexus: visual repo understanding and onboarding.
* CodeGraph: structured code relationship and AI coding support after implementation begins.
* Repomix: packaging selected context for LLMs.
* Markdown docs/context packs: source of truth.

---

## 11. What not to do

* Không tạo app code khi đang preparation.
* Không install package tùy hứng.
* Không để secret trong repo.
* Không để quyết định quan trọng chỉ nằm trong Zalo.
* Không prompt AI mơ hồ.
* Không đổi API response mà không cập nhật contract.

---

## 12. First onboarding checklist

```text
[ ] Đọc README.md
[ ] Đọc team workflow
[ ] Đọc tool stack decision
[ ] Đọc team role assignment
[ ] Đọc definition of done
[ ] Đọc module map
[ ] Đọc prompt library
[ ] Đọc codebase context workflow
[ ] Chọn một context pack để đọc kỹ
[ ] Viết thử một module contract
[ ] Review PR template
[ ] Hiểu demo safety checklist
```
