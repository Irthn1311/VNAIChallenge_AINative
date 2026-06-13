# Quy trình Viết code bằng AI (AI Coding Workflow)

Sử dụng AI để code giúp team nhanh hơn, nhưng nếu không kiểm soát cẩn thận sẽ dễ dẫn đến sai về kiến trúc, sai về hợp đồng API (API contract) và khó demo.

---

## 1. Tại sao việc dùng AI để code cần được kiểm soát

Các công cụ AI có thể:

* Tạo ra các file không cần thiết.
* Bịa ra các route hoặc cấu trúc dữ liệu (schema).
* Sửa code lan sang các module khác.
* Fix cứng (hard-code) logic chỉ để phục vụ demo.
* Làm cho code chạy được một phần nhưng lại làm hỏng phần tích hợp (integration).

Vì vậy, team phải sử dụng các gói ngữ cảnh (context packs) và các hợp đồng (contracts) trước khi ra lệnh (prompt) cho AI.

Về quy trình sử dụng ngữ cảnh codebase, vui lòng đọc:

* [tools/codebase-context-workflow.md](tools/codebase-context-workflow.md)
* [tools/codegraph-guide.md](tools/codegraph-guide.md)
* [tools/gitnexus-guide.md](tools/gitnexus-guide.md)
* [tools/repomix-guide.md](tools/repomix-guide.md)

---

## 2. Ngữ cảnh bắt buộc trước khi ra lệnh cho AI

Trước khi dùng AI cho một task không phải là quá nhỏ, bạn cần chuẩn bị:

* Yêu cầu task rõ ràng.
* Module liên quan.
* Các file liên quan (Related files).
* Hợp đồng API (API contract).
* Gói ngữ cảnh (Context pack).
* Các ràng buộc (Constraints).
* Danh sách kiểm tra (Testing checklist).

---

## 3. Mẫu prompt chuẩn để code bằng AI

```text
Bạn đang làm việc trong repo VNAI hackathon starter của chúng tôi.
Hãy đọc các file ai-context/AGENTS.md, PROJECT_CONTEXT.md, MODULE_MAP.md, và gói ngữ cảnh (context pack) liên quan trước.

Task:
[Mô tả task]

Module:
[Tên module]

Các file liên quan:
[Danh sách file]

Hợp đồng API (API contract):
[Endpoint hoặc none]

Ràng buộc (Constraints):
- Không thay đổi các file không liên quan.
- Tuân thủ theo docs/api-contract.md.
- Giữ cho phần triển khai code ở mức tối giản (minimal).
- Không tự bịa ra kiến trúc mới.

Kiểm thử (Testing):
[Các bước kiểm tra]
```

---

## 4. Mẫu prompt tìm và sửa lỗi (Debug prompt)

```text
Hãy debug vấn đề này bằng cách sửa lỗi an toàn và nhỏ nhất có thể.

Kết quả mong đợi (Expected):
[expected]

Kết quả thực tế (Actual):
[actual]

Logs:
[logs]

Các file liên quan (Relevant files):
[files]

Ràng buộc (Constraints):
- Không refactor các đoạn code không liên quan.
- Không thay đổi định dạng response của API trừ khi thật sự cần thiết.
- Hãy giải thích cách để xác minh bản vá lỗi này.
```

---

## 5. Mẫu prompt review code

```text
Hãy review đoạn diff này để tìm bug, sự không khớp về API, các vấn đề về ranh giới module, rủi ro khi demo, và các test case bị thiếu.

Module liên quan:
[module]

Hợp đồng API (API contract):
[contract]

Diff:
[diff]
```

---

## 6. Mẫu prompt cấu trúc lại code (Refactor prompt)

```text
Hãy refactor đoạn code này mà không làm thay đổi hành vi của nó.

Mục tiêu (Goal):
[goal]

Các file (Files):
[files]

Ràng buộc (Constraints):
- Giữ cho API công khai (public API) ổn định.
- Giữ cho hành vi UI ổn định.
- Không di chuyển logic qua lại giữa các module trừ khi thật sự cần.
- Hãy giải thích các rủi ro.
```

---

## 7. Mẫu prompt kiểm tra hợp đồng API

```text
Hãy so sánh phần triển khai code với docs/api-contract.md.

Endpoint:
[endpoint]

Các file (Files):
[files]

Trả về kết quả (Return):
- Điểm không khớp về Request.
- Điểm không khớp về Response.
- Điểm không khớp về xử lý lỗi (Error handling).
- Những cập nhật cần thiết cho Docs/context pack.
```

---

## 8. Mẫu prompt tạo Context pack

Sử dụng form mẫu trong `ai-context/PROMPT_LIBRARY.md` hoặc yêu cầu AI tự điền vào 12 phần bắt buộc.

---

## 9. Các quy tắc sử dụng Tool cụ thể

## ChatGPT Plus

Dùng để:

* Lên kế hoạch (Planning).
* Thiết kế prompt (Prompt design).
* Review code.
* Giải thích kiến trúc hệ thống.

Không dùng để:

* Sinh ra lượng lớn code một cách mù quáng mà không có ngữ cảnh repo.

## Codex

Dùng để:

* Chỉnh sửa code có nhận thức về repo.
* Triển khai code (Implementation).
* Sửa lỗi test (Test fixes).
* Cập nhật tài liệu (Documentation updates).

Không dùng để:

* Khởi tạo cấu trúc (scaffolding) diện rộng trừ khi team đã chính thức bước vào giai đoạn implementation.

## Gemini / Antigravity

Dùng để:

* Gợi ý nhanh các phương án code thay thế.
* Đưa ra ý tưởng về UI/code.
* Kiểm tra chéo (Cross-checking) các ý tưởng.

Không dùng để:

* Gộp code trực tiếp (direct merges) mà chưa được review.

## Claude

Dùng để:

* Suy luận logic dài.
* Review việc refactor code.
* Phân tích rủi ro.
* Viết tài liệu rõ ràng hơn.

Không dùng để:

* Thay thế các tài liệu nguồn gốc (source-of-truth docs) trong repo này.

## GitNexus, CodeGraph, Repomix

Dùng để:

* Hiểu cấu trúc codebase.
* Tìm các thành phần phụ thuộc (dependencies).
* Tạo ngữ cảnh gọn nhẹ cho AI.
* Review ranh giới của các module.

Không dùng để:

* Lưu trữ secret.
* Thay thế quy trình review thủ công.

Luật chi tiết:

* GitNexus: [tools/gitnexus-guide.md](tools/gitnexus-guide.md)
* CodeGraph: [tools/codegraph-guide.md](tools/codegraph-guide.md)
* Repomix: [tools/repomix-guide.md](tools/repomix-guide.md)

---

## 10. Những điều AI tuyệt đối không được làm

* Không tự bịa ra kiến trúc.
* Không thay đổi các file không liên quan.
* Không fix cứng (hard-code) thông tin bảo mật (secrets).
* Không âm thầm thay đổi các hợp đồng API.
* Không xóa bỏ các biện pháp an toàn cho demo / fallback.
* Không được tuyên bố tính năng đã hoàn thành trong khi nó mới chỉ nằm trên kế hoạch.
