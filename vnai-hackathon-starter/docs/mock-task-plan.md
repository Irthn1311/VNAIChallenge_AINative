# Mock Task Plan

Plan này dùng để test cách team phối hợp trước hackathon thật.

---

## 1. Goal of mock tasks

Mock tasks giúp team biết:

* Ai mạnh phần nào.
* Workflow có rõ không.
* AI coding prompt có đủ context không.
* Review và merge có bị chậm không.
* Demo fallback có được chuẩn bị không.

---

## 2. Role-based tasks

## Frontend/UI member

Suggested owner: Nguyễn Tuấn Tài

Mock task:

* Vẽ wireframe cho chat/upload/report flow.
* Viết component plan, chưa code thật.
* Xác định loading, empty, error state.

Output:

* UI flow note.
* Related future files.
* Questions for backend contract.

## Backend/API member

Suggested owner: Nguyễn Tuấn Tài, with API direction from Nguyễn Hữu Tri

Mock task:

* Viết planned API schema cho một endpoint.
* Kiểm tra request/response có đủ cho frontend không.
* Ghi error cases.

Output:

* API contract update.
* Module contract.

## AI/RAG/CV member

Suggested owner: Lư Hồng Phúc

Mock task:

* Thiết kế RAG/CV data flow.
* Viết prompt/eval questions.
* Xác định unsupported cases.

Output:

* Context pack update.
* Eval checklist.

## Product/Flow/Demo member

Suggested owner: Lê Thanh Phát

Mock task:

* Viết user journey.
* Chuẩn bị sample questions.
* Viết fallback plan.

Output:

* Demo script draft.
* Demo safety checklist update.

---

## 3. Mini task round

Thời lượng: 60-90 phút.

Goal:

* Mỗi người hoàn thành một docs-only task nhỏ.
* Mỗi task có PR hoặc review checklist.

Review questions:

* Task có rõ không?
* File thay đổi có đúng scope không?
* Có ai bị thiếu context không?

---

## 4. Small AI-native mock project round

Thời lượng: 0.5-1 ngày.

Goal:

* Chọn một mock idea đơn giản, ví dụ "Document Q&A for school regulation".
* Viết module contracts.
* Viết API contracts.
* Chuẩn bị demo data.
* Chỉ scaffold nếu team đã chuyển phase trong buổi mock.

Review questions:

* Module boundary có rõ không?
* Frontend/backend có khớp contract không?
* AI output có nguồn/fallback không?

---

## 5. Mock hackathon pressure round

Thời lượng: 3-4 giờ.

Goal:

* Mô phỏng áp lực deadline.
* Chạy demo freeze.
* Kiểm tra fallback.
* Pitch thử 3 phút.

Rules:

* Sau giờ thứ 3 không thêm feature mới.
* Chỉ sửa lỗi demo-critical.
* Product/Demo member kiểm soát flow.

---

## 6. Evaluate member strengths and weaknesses

Sau mỗi round, ghi nhận:

* Người nào mạnh planning?
* Người nào mạnh implementation?
* Người nào review kỹ?
* Người nào giao tiếp API tốt?
* Người nào xử lý demo tốt?
* Ai cần checklist rõ hơn?

Kết quả dùng để điều chỉnh owner trong `ai-context/MODULE_MAP.md` nếu team discussion thay đổi phân vai chính thức.
