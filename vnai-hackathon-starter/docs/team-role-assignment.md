# Team Role Assignment

Tài liệu này giúp team phân vai trước khi bắt đầu code thật. Hiện tại tất cả owner vẫn để `TBD` cho đến khi team leader họp và chốt tên thành viên.

---

## 1. Purpose of role assignment

Phân vai giúp team:

- Biết ai chịu trách nhiệm chính cho từng mảng.
- Tránh hai người cùng sửa một module theo hai hướng khác nhau.
- Có người quyết định cuối khi gần deadline.
- Có backup nếu một thành viên bị kẹt.
- Handoff rõ giữa Product, Frontend, Backend và AI.

Vai trò không có nghĩa là chỉ được làm đúng một việc. Trong hackathon, mỗi người vẫn có thể hỗ trợ nhau, nhưng mỗi phần phải có một người chịu trách nhiệm cuối.

---

## 2. Team structure for 4 members

| Role | Main focus | Current owner |
| --- | --- | --- |
| Role 1 | Technical Lead / Integration Lead | TBD |
| Role 2 | AI/RAG/CV Lead | TBD |
| Role 3 | Frontend/Backend Software Developer | TBD |
| Role 4 | Product Flow / Demo / Pitch Support | TBD |

---

## 3. Role 1: Technical Lead / Integration Lead

Nhiệm vụ chính:

- Giữ architecture và module boundaries.
- Kiểm tra API contract trước khi frontend/backend tích hợp.
- Quyết định cách deploy frontend/backend khi vào implementation phase.
- Review PR có ảnh hưởng nhiều module.
- Điều phối merge gần deadline.

Không nên:

- Ôm toàn bộ code.
- Tự đổi product flow mà không báo Product/Demo.
- Bỏ qua context pack khi dùng AI coding.

---

## 4. Role 2: AI/RAG/CV Lead

Nhiệm vụ chính:

- Thiết kế RAG/CV/OCR flow nếu đề bài cần.
- Quản lý prompt, eval questions, sample data liên quan AI.
- Đảm bảo AI output có nguồn, confidence hoặc explanation khi phù hợp.
- Chuẩn bị fallback cho LLM/vector/OCR lỗi.
- Review hallucination và unsupported cases.

Không nên:

- Claim accuracy khi chưa có eval.
- Hard-code demo answer vào core logic.
- Đổi API response mà không cập nhật contract.

---

## 5. Role 3: Frontend/Backend Software Developer

Nhiệm vụ chính:

- Build UI/API task theo contract khi vào implementation phase.
- Đảm bảo loading, empty, error states.
- Kết nối frontend với backend đúng schema.
- Viết hoặc hỗ trợ smoke test/manual test.
- Giữ code đơn giản, đúng scope.

Không nên:

- Tự bịa endpoint hoặc response schema.
- Đưa backend secret vào frontend.
- Refactor lớn gần deadline.

---

## 6. Role 4: Product Flow / Demo / Pitch Support

Nhiệm vụ chính:

- Viết problem statement, user journey, demo script.
- Chuẩn bị sample questions, sample data, screenshot/video fallback.
- Kiểm soát feature freeze, demo freeze, pitch freeze.
- Làm pitch deck với Canva.
- Đảm bảo demo kể được câu chuyện rõ ràng.

Không nên:

- Hứa feature chưa chạy được.
- Đổi demo flow trong giờ cuối.
- Giữ thông tin demo quan trọng chỉ trong Zalo.

---

## 7. Responsibility table

| Area | Primary role | Support role | Owner now |
| --- | --- | --- | --- |
| Architecture | Technical Lead / Integration Lead | Software Developer | TBD |
| API contract | Technical Lead / Integration Lead | Software Developer, AI/RAG/CV Lead | TBD |
| Frontend UI | Frontend/Backend Software Developer | Product Flow / Demo | TBD |
| Backend API | Frontend/Backend Software Developer | Technical Lead / Integration Lead | TBD |
| Chat RAG | AI/RAG/CV Lead | Backend, Product Flow / Demo | TBD |
| Upload Document | Frontend/Backend Software Developer | AI/RAG/CV Lead | TBD |
| CV/OCR | AI/RAG/CV Lead | Software Developer | TBD |
| Demo script | Product Flow / Demo / Pitch Support | All members | TBD |
| Pitch deck | Product Flow / Demo / Pitch Support | Technical Lead | TBD |
| Deployment readiness | Technical Lead / Integration Lead | Software Developer | TBD |

---

## 8. Decision authority table

| Decision type | Final decision owner | Must consult |
| --- | --- | --- |
| Module boundary | Technical Lead / Integration Lead | Related module owner |
| API request/response schema | Technical Lead / Integration Lead | Frontend/Backend, AI Lead |
| RAG/CV method | AI/RAG/CV Lead | Technical Lead, Product/Demo |
| UI flow | Product Flow / Demo + Software Developer | Technical Lead |
| Demo path | Product Flow / Demo / Pitch Support | All members |
| Feature freeze | Product Flow / Demo + Technical Lead | All members |
| Deployment choice | Technical Lead / Integration Lead | Software Developer |
| Remove risky feature | Technical Lead + Product Flow / Demo | Related owner |

---

## 9. Backup responsibility table

| Primary area | Backup role | Backup responsibility |
| --- | --- | --- |
| Technical Lead / Integration | Software Developer | Check integration, API mismatch, deployment notes |
| AI/RAG/CV | Technical Lead | Validate AI flow, fallback, eval questions |
| Frontend/Backend | Technical Lead | Review scope, unblock schema/API issue |
| Product/Demo/Pitch | AI/RAG/CV Lead | Help prepare sample questions and safe AI outputs |

Backup không có nghĩa là thay owner hoàn toàn. Backup chỉ giúp task không bị đứng khi owner bận hoặc bị block.

---

## 10. Handoff rules between modules

Khi handoff giữa hai module:

1. Ghi rõ input/output.
2. Link API contract hoặc module contract.
3. Ghi file liên quan.
4. Ghi trạng thái: planned, mock, implemented, tested.
5. Ghi rủi ro demo nếu có.
6. Không handoff bằng tin nhắn rời rạc mà không cập nhật docs.

Ví dụ handoff tốt:

```text
Frontend cần POST /api/chat theo docs/api-contract.md.
Backend trả answer, sources, actions.
Chat RAG owner chuẩn bị 3 sample questions trong data/eval.
Status: planned.
Risk: LLM latency, cần cached fallback.
```

---

## 11. How to update owners later

Sau khi team leader họp phân vai:

1. Điền tên thật vào bảng role trong file này.
2. Cập nhật owner trong `ai-context/MODULE_MAP.md`.
3. Cập nhật module contract nếu đã có.
4. Ghi lại thay đổi quan trọng trong `ai-context/DECISIONS.md` nếu ảnh hưởng workflow.
5. Báo trong Zalo/meeting để mọi người biết source of truth đã đổi.

---

## 12. Current owner placeholders

```text
Technical Lead / Integration Lead: TBD
AI/RAG/CV Lead: TBD
Frontend/Backend Software Developer: TBD
Product Flow / Demo / Pitch Support: TBD
```