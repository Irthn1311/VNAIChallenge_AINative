# Codebase Context Workflow

Tài liệu này nối CodeGraph, GitNexus, Repomix và Markdown docs/context packs thành một workflow thống nhất.

---

## 1. Why codebase context workflow is needed

AI coding dễ lệch hướng nếu context rời rạc. Team cần workflow chung để:

* AI biết repo đang ở phase nào.
* Thành viên biết file nào là source of truth.
* Tránh duplicate module/route/component.
* Tránh API contract mismatch.
* Giữ docs, context packs, code và demo flow kết nối với nhau.

---

## 2. Tool roles

| Tool | Role |
| --- | --- |
| GitNexus | Visual repo understanding and onboarding |
| CodeGraph | Structured code relationship and AI coding support |
| Repomix | Packaging selected context for LLMs |
| Markdown docs/context packs | Source of truth for project rules |

Markdown docs luôn là source of truth cho phase, role, API contract, module map và do-not rules.

---

## 3. Preparation phase workflow

Current phase:

```text
Preparation/documentation only.
```

Workflow hiện tại:

1. Đọc README.
2. Đọc onboarding guide.
3. Đọc role assignment.
4. Đọc Definition of Done.
5. Đọc module map.
6. Đọc API contract.
7. Đọc hoặc viết context pack.
8. Dùng Repomix nếu cần pack docs/context để AI audit.
9. Không scaffold app code.

GitNexus/CodeGraph có thể dùng để hiểu repo structure, nhưng chưa phải công cụ chính vì chưa có app code thật.

---

## 4. Implementation phase workflow

Khi team leader xác nhận chuyển sang implementation phase:

1. Đọc module contract.
2. Đọc context pack.
3. Đọc API contract.
4. Dùng GitNexus để hiểu repo area.
5. Dùng CodeGraph để inspect code relationships.
6. Dùng Repomix để pack selected context nếu cần hỏi LLM.
7. Prompt AI với constraints rõ.
8. Test.
9. Update docs/context nếu contract hoặc module boundary thay đổi.
10. Open PR.

---

## 5. Before editing code checklist

```text
[ ] Repo đã chuyển sang implementation phase
[ ] Module owner đã rõ trong MODULE_MAP.md
[ ] Module contract đã có
[ ] Context pack đã đọc
[ ] API contract đã đọc nếu có endpoint
[ ] Related files đã xác định
[ ] Do-not rules đã rõ
[ ] Test/manual verification đã định nghĩa
```

---

## 6. Before merging code checklist

```text
[ ] PR đúng scope
[ ] API contract vẫn khớp
[ ] Context pack cập nhật nếu cần
[ ] MODULE_MAP cập nhật nếu owner/boundary đổi
[ ] Demo flow không bị phá
[ ] Risk level đã ghi
[ ] Manual test đã chạy
```

---

## 7. How to decide which tool to use

| Need | Use |
| --- | --- |
| New member needs repo overview | GitNexus + README/onboarding |
| Need source-of-truth rules | Markdown docs |
| Need module ownership | `ai-context/MODULE_MAP.md` |
| Need endpoint shape | `docs/api-contract.md` |
| Need AI module constraints | Context pack |
| Need code dependency/call relation | CodeGraph |
| Need to send selected repo context to LLM | Repomix |

---

## 8. Anti-patterns

* Asking AI to "build feature" without context pack.
* Sending full repo to AI when one module context is enough.
* Treating GitNexus or CodeGraph output as source of truth over docs.
* Changing API response without updating `docs/api-contract.md`.
* Updating code but leaving context packs stale.
* Scaffolding app code during preparation phase.

---

## 9. Example end-to-end workflow

1. Read module contract.
2. Read context pack.
3. Use GitNexus to understand repo area.
4. Use CodeGraph to inspect code relationships.
5. Use Repomix to package relevant context.
6. Ask AI to implement with strict prompt.
7. Test.
8. Update docs if needed.
9. Open PR.

During preparation phase, stop after docs/context review and do not proceed to implementation.

