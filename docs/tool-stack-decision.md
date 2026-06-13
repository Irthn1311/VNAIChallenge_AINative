# Quyết định về Công cụ và Ngăn xếp Kỹ thuật (Tool Stack Decision)

Tài liệu này ghi lại các công cụ và ngăn xếp kỹ thuật (tool & stack) mà đội đã chọn để tránh tranh luận lại khi bước vào hackathon.

---

## 1. Danh sách công cụ chính thức

| Công cụ | Dùng để | Không nên dùng để |
| --- | --- | --- |
| GitHub | Quản lý mã nguồn, branches, PR, kiểm tra code | Trò chuyện thay thế tài liệu |
| Zalo | Trao đổi nhanh, thông báo khẩn | Lưu trữ các quyết định dài hạn |
| Docs / Notion / OneNote | Lập kế hoạch, ghi chú công việc | Nơi duy nhất lưu trữ quy ước code |
| Canva | Thiết kế bản thuyết trình (Pitch deck) | Viết tài liệu kỹ thuật |
| ChatGPT Plus | Lên kế hoạch, thiết kế prompt, viết tài liệu, review | Sửa code mù quáng mà không có ngữ cảnh repo |
| Codex | Chỉnh sửa code theo ngữ cảnh repo, triển khai, test | Khởi tạo cấu trúc dự án quy mô lớn mất kiểm soát |
| Gemini / Antigravity | Sinh mã code nhanh, gợi ý các lựa chọn thay thế | Trực tiếp gộp code (merge) mà chưa được review |
| Claude | Lập luận, xem xét refactor, viết tài liệu dài | Thay thế nguồn chân lý của repo |
| GitNexus | Lập bản đồ codebase, hướng dẫn thành viên mới | Lưu trữ thông tin bảo mật (secrets) |
| CodeGraph | Hiểu các module/sự phụ thuộc trong mã nguồn | Thay thế việc kiểm tra thủ công của con người |
| Repomix | Đóng gói ngữ cảnh repo cho các LLMs | Gửi thông tin bảo mật/dữ liệu cá nhân |

Chi tiết luồng công việc của các công cụ:

* [tools/codebase-context-workflow.md](tools/codebase-context-workflow.md)
* [tools/codegraph-guide.md](tools/codegraph-guide.md)
* [tools/gitnexus-guide.md](tools/gitnexus-guide.md)
* [tools/repomix-guide.md](tools/repomix-guide.md)

---

## 2. Ngăn xếp kỹ thuật chính thức (Technical stack)

* Frontend: Next.js
* Backend: FastAPI
* Database: Supabase/PostgreSQL
* Vector search: ưu tiên dùng pgvector
* Triển khai Frontend: Vercel
* Triển khai Backend: Railway/Render

---

## 3. Lý do lựa chọn Phương án B

Phương án B:

```text
Next.js frontend + FastAPI backend + Supabase/PostgreSQL
```

Được chọn bởi vì:

* Trách nhiệm giữa frontend và backend được phân định rõ ràng.
* Backend dùng Python rất phù hợp cho các tác vụ AI/RAG/CV.
* Supabase giúp giảm thiểu thời gian cài đặt database/lưu trữ.
* Vercel hỗ trợ triển khai frontend rất nhanh chóng.
* Railway/Render đủ đơn giản để triển khai backend.
* pgvector giúp tránh việc phải thêm một vector database riêng biệt từ quá sớm.

Đánh đổi:

* Phải quản lý hai bản triển khai thay vì một.
* Cần xử lý vấn đề CORS và quản lý biến môi trường (env).
* Cần có kỷ luật chặt chẽ hơn về các thỏa thuận API (API contract).

---

## 4. Rủi ro

## CORS

Rủi ro:

Frontend trên Vercel có thể bị lỗi khi gọi backend nếu CORS không được cấu hình đúng cách.

Biện pháp giảm thiểu:

* Định nghĩa rõ các domain được phép (allowed origins).
* Kiểm thử frontend đã triển khai với backend đã triển khai từ sớm.

## Quản lý biến môi trường (Env management)

Rủi ro:

Giá trị biến môi trường có thể khác nhau giữa môi trường local, Vercel, Railway/Render, và Supabase.

Biện pháp giảm thiểu:

* Luôn cập nhật file `.env.example`.
* Tuyệt đối không commit các khóa bảo mật (secrets) thật lên repo.
* Chỉ định một người phụ trách việc kiểm tra danh sách biến môi trường khi triển khai.

## Không khớp thỏa thuận API (API contract mismatch)

Rủi ro:

Frontend kỳ vọng một cấu trúc dữ liệu nhưng backend lại trả về một cấu trúc khác.

Biện pháp giảm thiểu:

* Phải cập nhật `docs/api-contract.md` trước tiên.
* Xem xét kỹ các Pull Request (PR) về những tác động tới API.
* Sử dụng các kiểu dữ liệu chung (shared types) sau này nếu cần thiết.

## Quản lý hai bản triển khai

Rủi ro:

Frontend hoạt động bình thường nhưng backend bị lỗi (down), hoặc backend hoạt động nhưng frontend lại trỏ sai URL.

Biện pháp giảm thiểu:

* Thêm endpoint `/health` để kiểm tra trạng thái.
* Làm nóng (warm up) các bản triển khai trước khi demo.
* Chuẩn bị sẵn phương án dự phòng ở local hoặc ảnh chụp màn hình.

---

## 5. Trạng thái hiện tại

Đã được chốt cho giai đoạn chuẩn bị.

Quá trình lập trình (Implementation) chỉ bắt đầu sau khi hệ thống tài liệu, các module contracts, và các task thử nghiệm (mock tasks) đã hoàn tất.
