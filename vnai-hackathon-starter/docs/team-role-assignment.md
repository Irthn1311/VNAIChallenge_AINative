# Team Role Assignment

Tài liệu này giúp team phân vai trước khi bắt đầu code thật. Các tên dưới đây là role ownership chính thức cho phase chuẩn bị và onboarding.

---

## 1. Purpose of role assignment

Phân vai giúp team:

- Biết ai chịu trách nhiệm chính cho từng mảng.
- Tránh hai người cùng sửa một module theo hai hướng khác nhau.
- Có người quyết định cuối khi gần deadline.
- Có backup nếu một thành viên bị kẹt.
- Handoff rõ giữa Product, Frontend, Backend và AI.

Vai trò là ownership role, không phải ranh giới cứng. Thành viên có thể hỗ trợ nhau, nhưng mỗi area phải có một owner rõ để tránh lệch hướng.

---

## 2. Team structure for 4 members

| Role | Main focus | Current owner |
| --- | --- | --- |
| Role 1 | Technical Lead / Integration Lead | Nguyễn Hữu Tri |
| Role 2 | AI/RAG/CV Lead | Lư Hồng Phúc |
| Role 3 | Frontend/Backend Software Developer | Nguyễn Tuấn Tài |
| Role 4 | Product Flow / Demo / Pitch Support | Lê Thanh Phát |

---

## 3. Role 1: Technical Lead / Integration Lead

Owner: Nguyễn Hữu Tri

Nhiệm vụ chính:

* System architecture.
* Final integration.
* API contract direction.
* Repo structure.
* AI coding workflow control.
* Merge/demo stability.
* Coordination between frontend, backend, AI, and product flow.

Không nên:

- Ôm toàn bộ code.
- Tự đổi product flow mà không báo Product/Demo.
- Bỏ qua context pack khi dùng AI coding.

---

## 4. Role 2: AI/RAG/CV Lead

Owner: Lư Hồng Phúc

Nhiệm vụ chính:

* AI/RAG pipeline design.
* Computer Vision/OCR module if needed.
* Prompt design support.
* Model/API choice support.
* AI evaluation support.
* AI module context packs.

Không nên:

- Claim accuracy khi chưa có eval.
- Hard-code demo answer vào core logic.
- Đổi API response mà không cập nhật contract.

---

## 5. Role 3: Frontend/Backend Software Developer

Owner: Nguyễn Tuấn Tài

Nhiệm vụ chính:

* Frontend implementation support.
* Backend/API implementation support.
* UI integration with API.
* Software engineering structure.
* Bug fixing and feature implementation.

Không nên:

- Tự bịa endpoint hoặc response schema.
- Đưa backend secret vào frontend.
- Refactor lớn gần deadline.

---

## 6. Role 4: Product Flow / Demo / Pitch Support

Owner: Lê Thanh Phát

Nhiệm vụ chính:

* User journey.
* Product flow.
* Demo script.
* Sample data planning.
* Pitch story support.
* Testing the product from user perspective.

Không nên:

- Hứa feature chưa chạy được.
- Đổi demo flow trong giờ cuối.
- Giữ thông tin demo quan trọng chỉ trong Zalo.

---

## 7. Responsibility table

| Area | Primary role | Support role | Owner now |
| --- | --- | --- | --- |
| Architecture | Technical Lead / Integration Lead | Software Developer | Nguyễn Hữu Tri |
| API contract | Technical Lead / Integration Lead | Software Developer, AI/RAG/CV Lead | Nguyễn Hữu Tri |
| Frontend UI | Frontend/Backend Software Developer | Product Flow / Demo | Nguyễn Tuấn Tài |
| Backend API | Frontend/Backend Software Developer | Technical Lead / Integration Lead | Nguyễn Tuấn Tài |
| Chat RAG | AI/RAG/CV Lead | Backend, Product Flow / Demo | Lư Hồng Phúc |
| Upload Document | Frontend/Backend Software Developer | AI/RAG/CV Lead | Nguyễn Tuấn Tài |
| CV/OCR | AI/RAG/CV Lead | Software Developer | Lư Hồng Phúc |
| Demo script | Product Flow / Demo / Pitch Support | All members | Lê Thanh Phát |
| Pitch deck | Product Flow / Demo / Pitch Support | Technical Lead | Lê Thanh Phát |
| Deployment readiness | Technical Lead / Integration Lead | Software Developer | Nguyễn Hữu Tri |

---

## 8. Decision authority table

| Decision type | Final decision owner | Must consult |
| --- | --- | --- |
| Module boundary | Nguyễn Hữu Tri | Related module owner |
| API request/response schema | Nguyễn Hữu Tri | Nguyễn Tuấn Tài, Lư Hồng Phúc |
| RAG/CV method | Lư Hồng Phúc | Nguyễn Hữu Tri, Lê Thanh Phát |
| UI flow | Lê Thanh Phát + Nguyễn Tuấn Tài | Nguyễn Hữu Tri |
| Demo path | Lê Thanh Phát | All members |
| Feature freeze | Lê Thanh Phát + Nguyễn Hữu Tri | All members |
| Deployment choice | Nguyễn Hữu Tri | Nguyễn Tuấn Tài |
| Remove risky feature | Nguyễn Hữu Tri + Lê Thanh Phát | Related owner |

---

## 9. Backup responsibility table

| Primary area | Backup role | Backup responsibility |
| --- | --- | --- |
| Technical Lead / Integration | Nguyễn Tuấn Tài | Check integration, API mismatch, deployment notes |
| AI/RAG/CV | Nguyễn Hữu Tri | Validate AI flow, fallback, eval questions |
| Frontend/Backend | Nguyễn Hữu Tri | Review scope, unblock schema/API issue |
| Product/Demo/Pitch | Lư Hồng Phúc | Help prepare sample questions and safe AI outputs |

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

Nếu team đổi owner sau discussion:

1. Cập nhật tên trong bảng role của file này.
2. Cập nhật owner trong `ai-context/MODULE_MAP.md`.
3. Cập nhật module contract nếu đã có.
4. Ghi lại thay đổi quan trọng trong `ai-context/DECISIONS.md` nếu ảnh hưởng workflow.
5. Báo trong Zalo/meeting để mọi người biết source of truth đã đổi.

---

## 12. Current owners

```text
Technical Lead / Integration Lead: Nguyễn Hữu Tri
AI/RAG/CV Lead: Lư Hồng Phúc
Frontend/Backend Software Developer: Nguyễn Tuấn Tài
Product Flow / Demo / Pitch Support: Lê Thanh Phát
```
