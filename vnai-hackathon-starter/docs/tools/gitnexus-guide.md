# GitNexus Guide

GitNexus dùng để hiểu repo bằng cách trực quan hơn: folder, module relationship, repo overview và onboarding.

Current phase: preparation only. Có thể dùng GitNexus để xem cấu trúc docs/folders, nhưng giá trị chính sẽ rõ hơn sau khi code scaffold bắt đầu.

---

## 1. What GitNexus is used for in this team

GitNexus dùng để:

* Onboard thành viên mới.
* Nhìn tổng quan repo structure.
* Thảo luận module relationship trong team.
* Kiểm tra PR có đụng vùng nào lớn không.
* Chuẩn bị review trước khi merge.

GitNexus không phải primary implementation tool.

---

## 2. When to use GitNexus

Dùng GitNexus khi:

* Thành viên mới cần hiểu repo.
* Team cần thảo luận folder/module.
* Trước khi merge PR có nhiều file.
* Muốn nhìn nhanh vùng code/docs liên quan.
* Muốn giải thích repo cho người không trực tiếp code phần đó.

---

## 3. When not to use GitNexus

Không dùng GitNexus để:

* Quyết định API schema thay cho `docs/api-contract.md`.
* Thay thế code review.
* Sinh code hoặc sửa code trực tiếp.
* Lưu secrets hoặc private context.
* Kết luận implementation đã đúng chỉ vì nhìn graph đẹp.

---

## 4. How GitNexus helps onboarding and visual understanding

GitNexus giúp:

* Nhìn được repo có `docs/`, `ai-context/`, `apps/`, `packages/`, `data/`, `scripts/`.
* Hiểu docs và context packs nằm ở đâu.
* Giúp team leader chỉ nhanh khu vực mỗi member cần đọc.
* Hỗ trợ discussion trong meeting.

---

## 5. How to use GitNexus before merge/review

Trước khi review PR lớn:

1. Xem PR touched files.
2. Dùng GitNexus để nhìn affected areas.
3. So với `MODULE_MAP.md` để biết owner.
4. Nếu PR đụng module khác, request owner module đó review.
5. Kiểm tra docs/context pack có cần update không.

---

## 6. How GitNexus differs from CodeGraph

| Tool | Best for |
| --- | --- |
| GitNexus | Visual repo exploration, onboarding, module discussion |
| CodeGraph | Structured code relationships, symbol/call/dependency tracing |
| Repomix | Packing selected repo context for LLMs |
| Markdown docs | Source of truth for rules, contracts, roles, phase |

---

## 7. Do not rules

* Do not use GitNexus output as the only review.
* Do not override docs based only on visual graph.
* Do not expose secrets/private files.
* Do not use it to encourage broad refactors during deadline pressure.

---

## 8. Example usage scenarios

## Scenario 1: New member onboarding

Use GitNexus to show:

* `README.md`
* `docs/team-onboarding-guide.md`
* `ai-context/MODULE_MAP.md`
* related context pack

## Scenario 2: Team planning

Use GitNexus in meeting to explain which folders are future app code and which folders are docs/context.

## Scenario 3: PR review

Use GitNexus to see whether a PR that claims to update Chat RAG also touches upload, report, or deployment files.

