# MODULE_MAP.md

File này dùng để ánh xạ các module dự kiến với các trách nhiệm, người phụ trách (owner), các điểm tích hợp và các gói ngữ cảnh (context packs) tương ứng.

Cập nhật file này khi:

* Một module được thêm, xóa, hoặc đổi tên.
* Có sự thay đổi về người phụ trách.
* Có sự thay đổi về thỏa thuận API (API contract).
* Thay đổi luồng quan trọng của demo (Demo-critical flow).

Giai đoạn hiện tại: chỉ mới là chuẩn bị (preparation). Các đường dẫn bên dưới có thể là các file dự kiến trong tương lai.

Nguồn phân công vai trò:

```text
docs/team-role-assignment.md
```

Lưu ý về người phụ trách (Owner note):

Các vai trò chính thức hiện đã được điền để phục vụ cho việc onboarding. Nếu sau này đội thay đổi phân công, hãy nhớ cập nhật cùng lúc ở `docs/team-role-assignment.md`, file này, và các module contracts/context packs liên quan.

Các người phụ trách hiện tại:

```text
Technical Lead / Integration Lead: Nguyễn Hữu Tri
AI/RAG/CV Lead: Lư Hồng Phúc
Frontend/Backend Software Developer: Nguyễn Tuấn Tài
Product Flow / Demo / Pitch Support: Lê Thanh Phát
```

---

## 1. Giao diện Frontend (Frontend UI)

Đường dẫn:

```text
apps/web
```

Người phụ trách:

```text
Nguyễn Tuấn Tài
```

Hỗ trợ:

```text
Lê Thanh Phát / Nguyễn Hữu Tri
```

Gói ngữ cảnh (Context pack):

```text
ai-context/context-packs/frontend-ui.md
```

Trách nhiệm:

* Bố cục ứng dụng (App layout).
* Giao diện Chat.
* Giao diện Upload.
* Màn hình Báo cáo/Dashboard.
* Gọi API đến FastAPI backend.
* Xử lý các trạng thái tải (loading), trống (empty), và lỗi (error).

Điểm tích hợp:

```text
GET /health
POST /api/chat
POST /api/upload
POST /api/report
POST /api/analyze-image
```

Không được làm (Do not):

* Không lưu trữ thông tin bảo mật của backend (secrets).
* Không fix cứng (hard-code) câu trả lời cuối cùng của AI trừ khi đó là dữ liệu fallback/demo được đánh dấu rõ ràng.
* Không thay đổi các giả định về API mà không cập nhật vào `docs/api-contract.md`.

---

## 2. API Backend (Backend API)

Đường dẫn:

```text
apps/api
```

Người phụ trách:

```text
Nguyễn Tuấn Tài
```

Hỗ trợ:

```text
Nguyễn Hữu Tri / Lư Hồng Phúc
```

Gói ngữ cảnh (Context pack):

```text
ai-context/context-packs/backend-api.md
```

Trách nhiệm:

* Các endpoint (routes) FastAPI.
* Kiểm tra tính hợp lệ của request (Request validation).
* Đảm bảo tính ổn định của cấu trúc response (Response schema stability).
* Điều phối các dịch vụ (Service orchestration).
* Kết nối Supabase.
* Tích hợp AI/RAG/CV.

Không được làm (Do not):

* Không trả về các định dạng response chưa được viết trong tài liệu.
* Không tạo các endpoint trùng lặp.
* Không đưa logic giao diện (frontend UI) vào đây.
* Không che giấu các lỗi triển khai trong lúc demo.

---

## 3. Chat RAG

Đường dẫn:

```text
apps/api/services/rag
apps/web/components/chat
```

Người phụ trách:

```text
Lư Hồng Phúc
```

Hỗ trợ:

```text
Nguyễn Hữu Tri / Nguyễn Tuấn Tài / Lê Thanh Phát
```

Gói ngữ cảnh (Context pack):

```text
ai-context/context-packs/chat-rag.md
```

API:

```text
POST /api/chat
```

Trách nhiệm:

* Truy xuất các đoạn thông tin liên quan (Retrieve relevant chunks).
* Xây dựng prompt kèm ngữ cảnh.
* Sinh câu trả lời.
* Trả về nguồn trích dẫn (sources).
* Xử lý an toàn các câu hỏi không được hỗ trợ.

---

## 4. Tải lên tài liệu (Upload Document)

Đường dẫn:

```text
apps/api/routes/upload.py
apps/api/services/document_service.py
apps/web/components/upload
```

Người phụ trách:

```text
Nguyễn Tuấn Tài
```

Hỗ trợ:

```text
Lư Hồng Phúc / Nguyễn Hữu Tri
```

Gói ngữ cảnh (Context pack):

```text
ai-context/context-packs/upload-document.md
```

API:

```text
POST /api/upload
```

Trách nhiệm:

* Kiểm tra tính hợp lệ của file.
* Lưu trữ file hoặc siêu dữ liệu (metadata).
* Trích xuất văn bản (nếu được hỗ trợ).
* Chuẩn bị tài liệu cho hệ thống RAG.

---

## 5. Thị giác máy tính / Nhận dạng ký tự quang học (CV / OCR)

Đường dẫn:

```text
apps/api/services/cv
apps/web/components/image-analysis
```

Người phụ trách:

```text
Lư Hồng Phúc
```

Hỗ trợ:

```text
Nguyễn Tuấn Tài / Lê Thanh Phát
```

Gói ngữ cảnh (Context pack):

```text
ai-context/context-packs/cv-ocr.md
```

API:

```text
POST /api/analyze-image
```

Trách nhiệm:

* Kiểm tra tính hợp lệ của ảnh đầu vào.
* Chạy mô hình/API OCR hoặc CV.
* Trả về kết quả có cấu trúc, độ tin cậy (confidence), và lời giải thích.

Không được làm (Do not):

* Không lấy block CV (vốn là tùy chọn) làm phần demo chính.
* Không phụ thuộc vào các mô hình chạy local quá nặng trừ khi đã được test.

---

## 6. Luồng Báo cáo / Demo (Report / Demo Flow)

Đường dẫn:

```text
docs/
data/samples/
data/eval/
apps/web/report
apps/api/services/report_service.py
```

Người phụ trách:

```text
Lê Thanh Phát
```

Hỗ trợ:

```text
Nguyễn Hữu Tri / Nguyễn Tuấn Tài / Lư Hồng Phúc
```

Gói ngữ cảnh (Context pack):

```text
ai-context/context-packs/demo-flow.md
```

API:

```text
POST /api/report
```

Trách nhiệm:

* Phát biểu bài toán (Problem statement).
* Hành trình người dùng (User journey).
* Kịch bản demo (Demo script).
* Dữ liệu mẫu (Sample data).
* Các câu hỏi đánh giá (Evaluation questions).
* Dàn ý bài thuyết trình (Pitch outline).
* Kế hoạch dự phòng (Fallback plan).

Không được làm (Do not):

* Không giữ luồng demo chỉ ở trong các tin nhắn trò chuyện (phải viết vào docs).
* Không sử dụng dữ liệu demo ngẫu nhiên chưa được test.
* Không thay đổi luồng demo ngay sát giờ thuyết trình.
