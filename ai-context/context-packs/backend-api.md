# Gói ngữ cảnh: API Backend (Backend API)

## 1. Mục đích (Purpose)

Backend API là dịch vụ FastAPI dự kiến, có chức năng kiểm tra tính hợp lệ của request, điều phối các dịch vụ AI, và trả về dữ liệu ổn định cho frontend.

## 2. Người phụ trách (Owner)

Người phụ trách chính: Nguyễn Tuấn Tài

Hỗ trợ: Nguyễn Hữu Tri, Lư Hồng Phúc, Lê Thanh Phát

## 3. Các file liên quan (Related Files)

Các file hiện có:

```text
docs/api-contract.md
docs/architecture.md
ai-context/MODULE_MAP.md
```

Các file dự kiến sẽ có:

```text
apps/api/main.py
apps/api/routes/
apps/api/services/
apps/api/schemas/
apps/api/core/config.py
apps/api/tests/
```

## 4. Luồng dữ liệu (Data Flow)

```text
Request từ Frontend
  -> Route của FastAPI
  -> Xác thực dữ liệu bằng Pydantic
  -> Tầng dịch vụ (Service layer)
  -> Supabase / API của nhà cung cấp AI / Bộ nhớ lưu trữ (storage)
  -> Trả về response có cấu trúc
  -> Frontend
```

## 5. Đầu vào / Đầu ra (Input / Output)

Đầu vào:

* Các payload dạng JSON cho tính năng chat/báo cáo.
* Giao thức Multipart uploads cho tài liệu/hình ảnh.
* Các request kiểm tra trạng thái sức khỏe (Health check requests).

Đầu ra:

* Các phản hồi JSON khớp với định nghĩa trong `docs/api-contract.md`.
* Các phản hồi lỗi ổn định.

## 6. Hợp đồng API / Tích hợp (API or Integration Contract)

Các endpoint dự kiến:

```text
GET /health
POST /api/chat
POST /api/upload
POST /api/report
POST /api/analyze-image
```

Trạng thái: Đang lên kế hoạch (Planned)

## 7. Các thành phần phụ thuộc (Dependencies)

* FastAPI.
* Pydantic.
* Supabase client.
* LLM/embedding provider.
* Trình đọc file/OCR (nếu cần).
* Biến môi trường (Environment variables).

## 8. Những điều tuyệt đối không làm (Do Not Rules)

* Không trả về các cấu trúc dữ liệu chưa được ghi trong tài liệu (undocumented schemas).
* Không fix cứng (hard-code) các mã bảo mật (secrets).
* Không đưa logic giao diện UI vào backend.
* Không tạo các route trùng lặp.
* Không làm cho endpoint `/health` bị phụ thuộc vào các lời gọi AI chậm chạp.
* Không lờ đi (swallow) các lỗi mà thiếu đi tin nhắn cảnh báo hữu ích.

## 9. Các nhiệm vụ chung (Common Tasks)

* Định nghĩa các schema.
* Triển khai route health (kiểm tra sức khỏe hệ thống).
* Triển khai các route chat/upload/report/image.
* Bổ sung tầng dịch vụ (service layer).
* Cấu hình CORS.
* Viết thêm các bài kiểm tra chạy thử (manual smoke tests).

## 10. Danh sách kiểm thử (Testing Checklist)

```text
[ ] GET /health trả về ok
[ ] Các request hợp lệ khớp với hợp đồng API
[ ] Các request không hợp lệ trả về lỗi rõ ràng
[ ] Cấu hình CORS hoạt động tốt với domain của frontend
[ ] Sẽ báo lỗi rõ ràng nếu thiếu các biến môi trường
[ ] Các endpoint dùng để demo phản hồi trong khoảng thời gian chấp nhận được
```

## 11. Mức độ quan trọng khi Demo (Demo Relevance)

Rất cao. Sự thiếu ổn định của backend có thể phá hỏng toàn bộ buổi demo.

Hãy chuẩn bị sẵn endpoint `/health`, hệ thống log, danh sách kiểm tra các biến môi trường (env), và phương án dự phòng (fallback plan).

## 12. Hướng dẫn Lập trình với AI (AI Coding Instruction)

Khi yêu cầu AI làm việc trên backend:

```text
Nêu tên đích danh endpoint.
Dán nội dung hợp đồng API (API contract) vào.
Nêu tên các file service cần sử dụng hoặc tạo mới.
Bắt buộc phải có chức năng kiểm tra hợp lệ (validation) và response lỗi phải giống tài liệu.
Không được thay đổi frontend trừ khi có yêu cầu rõ ràng.
```
