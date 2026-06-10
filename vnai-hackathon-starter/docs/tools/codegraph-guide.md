# CodeGraph Guide

CodeGraph là công cụ hỗ trợ hiểu cấu trúc code, quan hệ symbol/call/dependency và vùng ảnh hưởng của thay đổi.

Current phase: preparation only. Team chuẩn bị workflow dùng CodeGraph bây giờ, nhưng chỉ dùng nghiêm túc sau khi bắt đầu scaffold/code thật.

---

## 1. What CodeGraph is used for in this team

CodeGraph dùng để:

* Hiểu quan hệ giữa file, function, class, route, service.
* Trace dependency hoặc call relationship.
* Tìm vùng code bị ảnh hưởng trước khi sửa.
* Hỗ trợ AI coding bằng context có cấu trúc.
* Kiểm tra module boundary có bị vượt không.

---

## 2. When to use CodeGraph

Dùng CodeGraph khi:

* Implementation phase đã bắt đầu.
* Cần hiểu một route gọi service nào.
* Cần biết function/component đang được dùng ở đâu.
* Cần kiểm tra thay đổi có ảnh hưởng module khác không.
* Chuẩn bị prompt cho AI sửa code có nhiều file liên quan.

---

## 3. When not to use CodeGraph

Không cần dùng CodeGraph khi:

* Repo chỉ đang ở preparation docs phase.
* Task chỉ sửa Markdown đơn giản.
* Chưa có code thật để phân tích.
* Câu hỏi đã được trả lời rõ trong `docs/` hoặc `ai-context/`.

---

## 4. How CodeGraph helps AI coding

CodeGraph giúp AI coding bằng cách:

* Xác định đúng file liên quan.
* Tránh tạo duplicate function/service.
* Cho biết dependency nào có thể bị ảnh hưởng.
* Giúp prompt AI cụ thể hơn thay vì yêu cầu sửa mơ hồ.

AI vẫn phải đọc source-of-truth docs trước:

```text
ai-context/AGENTS.md
ai-context/MODULE_MAP.md
docs/api-contract.md
ai-context/context-packs/
```

---

## 5. Suggested workflow before asking AI to edit code

1. Đọc module contract.
2. Đọc context pack.
3. Đọc API contract nếu có endpoint.
4. Dùng CodeGraph để tìm related files và dependency.
5. Ghi rõ file nào được sửa, file nào không được sửa.
6. Prompt AI với constraints rõ ràng.

---

## 6. What questions to ask CodeGraph

Ví dụ câu hỏi:

* Route này gọi service nào?
* Component này được dùng ở page nào?
* Function này có caller nào?
* Nếu đổi schema này, file nào bị ảnh hưởng?
* Có module nào đang duplicate logic không?
* Service này thuộc module nào trong `MODULE_MAP.md`?

---

## 7. Relation to context packs

Context pack nói module nên hoạt động như thế nào.

CodeGraph giúp kiểm tra code thật có đang đi theo module đó không.

Nếu CodeGraph phát hiện file quan trọng chưa có trong context pack, cập nhật context pack trước hoặc trong PR.

---

## 8. Relation to MODULE_MAP.md

`ai-context/MODULE_MAP.md` là source of truth về owner, responsibility, integration point.

CodeGraph chỉ giúp nhìn code relationship. Nếu CodeGraph và `MODULE_MAP.md` có vẻ mâu thuẫn, team phải cập nhật docs hoặc code để đồng bộ.

---

## 9. Do not rules

* Do not use CodeGraph as source of truth for product decision.
* Do not ignore `docs/api-contract.md`.
* Do not ask AI to edit files just because CodeGraph found them.
* Do not use CodeGraph to justify broad refactors near deadline.
* Do not treat generated graph output as a replacement for review.

---

## 10. Example usage scenarios

## Scenario 1: Chat route change

Use CodeGraph to see:

* `POST /api/chat` route.
* RAG service calls.
* Prompt/LLM service dependency.
* Response schema usage.

Then prompt AI with only the relevant files.

## Scenario 2: Frontend chat component

Use CodeGraph to see:

* Chat page.
* Message components.
* API client.
* Shared types.

Then update UI without touching backend unless needed.

## Scenario 3: Pre-merge review

Use CodeGraph to check whether a PR touched modules outside its stated scope.

