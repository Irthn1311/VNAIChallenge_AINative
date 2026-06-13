# Gói ngữ cảnh: Tải lên Tài liệu (Upload Document)

## 1. Mục đích (Purpose)

Tải lên Tài liệu là module nhận các file từ người dùng, kiểm tra tính hợp lệ, lưu trữ, và chuẩn bị nội dung để phục vụ cho các luồng RAG hoặc báo cáo.

Mục tiêu giai đoạn chuẩn bị: định nghĩa hành vi dự kiến trước khi tiến hành code thật.

## 2. Người phụ trách (Owner)

Người phụ trách chính: Nguyễn Tuấn Tài

Hỗ trợ: Lư Hồng Phúc, Nguyễn Hữu Tri, Lê Thanh Phát

## 3. Các file liên quan (Related Files)

Các file hiện có:

```text
docs/api-contract.md
docs/module-contract-template.md
ai-context/MODULE_MAP.md
ai-context/context-packs/chat-rag.md
```

Các file dự kiến sẽ có:

```text
apps/api/routes/upload.py
apps/api/services/upload_service.py
apps/api/services/document_service.py
apps/api/services/vector_service.py
apps/api/schemas/upload.py
apps/web/components/upload/FileUploadBox.tsx
apps/web/components/upload/UploadedFileList.tsx
apps/web/app/upload/page.tsx
data/samples/documents/
```

## 4. Luồng dữ liệu (Data Flow)

```text
Người dùng chọn file
  -> UI tải lên của Next.js
  -> Gọi POST /api/upload
  -> Route upload của FastAPI
  -> Kiểm tra định dạng và dung lượng file
  -> Lưu file hoặc siêu dữ liệu (metadata)
  -> Trích xuất văn bản nếu được hỗ trợ
  -> (Tùy chọn) Cắt nhỏ (chunk) + Nhúng (embed) + Đánh chỉ mục (index)
  -> Trả về document_id / collection_id / status
```

## 5. Đầu vào / Đầu ra (Input / Output)

Đầu vào:

```text
multipart/form-data
file: file được tải lên
collection_id: chuỗi ký tự (không bắt buộc)
```

Đầu ra:

```json
{
  "document_id": "string",
  "collection_id": "string",
  "filename": "string",
  "file_type": "string",
  "status": "uploaded",
  "message": "string"
}
```

## 6. Hợp đồng API / Tích hợp (API or Integration Contract)

Endpoint:

```text
POST /api/upload
```

Nguồn chân lý (Source of truth):

```text
docs/api-contract.md
```

Trạng thái: Đang lên kế hoạch (Planned)

## 7. Các thành phần phụ thuộc (Dependencies)

* Hàm kiểm tra tính hợp lệ của file.
* Đường dẫn lưu trữ hoặc Supabase Storage.
* Tính năng trích xuất văn bản.
* (Tùy chọn) Thuật toán cắt nhỏ văn bản (chunking).
* (Tùy chọn) Thuật toán tạo vector nhúng (embedding).
* Module Chat RAG.

## 8. Những điều tuyệt đối không làm (Do Not Rules)

* Không cho phép tải lên file có kích thước không giới hạn.
* Không âm thầm xử lý các định dạng file không được hỗ trợ.
* Không fix cứng (hard-code) các đường dẫn tuyệt đối (absolute paths) trên máy local.
* Không lưu trữ các thông tin bảo mật (secrets) trong dữ liệu được tải lên.
* Không khóa luồng xử lý vĩnh viễn (block forever) nếu việc đánh chỉ mục (indexing) bị lỗi.
* Không thay đổi cấu trúc dữ liệu trả về của API upload mà không cập nhật tài liệu hợp đồng API.

## 9. Các nhiệm vụ chung (Common Tasks)

* Định nghĩa các định dạng file được hỗ trợ.
* Định nghĩa dung lượng file tối đa.
* Chuẩn bị các file mẫu (sample files).
* Triển khai route upload (làm sau).
* Triển khai tính năng trích xuất văn bản (làm sau).
* Kết nối với tính năng đánh chỉ mục RAG (làm sau).
* Thêm UI tải lên (làm sau).

## 10. Danh sách kiểm thử (Testing Checklist)

```text
[ ] Tải lên file TXT hợp lệ thành công
[ ] Tải lên file PDF hợp lệ thành công nếu trình đọc file (parser) đã sẵn sàng
[ ] Định dạng file không được hỗ trợ sẽ bị từ chối
[ ] File rỗng sẽ bị từ chối
[ ] Dữ liệu trả về (response) có chứa document_id
[ ] Dữ liệu trả về có chứa collection_id
[ ] Frontend hiển thị trạng thái thành công
[ ] Frontend hiển thị trạng thái báo lỗi
```

## 11. Mức độ quan trọng khi Demo (Demo Relevance)

Trung bình đến cao. Việc tải lên thành công sẽ rất ấn tượng, nhưng cũng đầy rủi ro nếu bộ đọc file (parser) hoặc hệ thống lưu trữ (storage) gặp trục trặc.

Cần chuẩn bị:

* 1 đến 2 tài liệu mẫu hoạt động ổn định.
* Tài liệu dự phòng đã được đánh chỉ mục sẵn (Pre-indexed fallback document).
* Hình ảnh hoặc video quay lại cảnh upload thành công.

## 12. Hướng dẫn Lập trình với AI (AI Coding Instruction)

Khi yêu cầu AI làm việc với module này, cần phải cung cấp các thông tin sau:

```text
Định dạng file hỗ trợ (Supported file types):
Dung lượng tối đa (Max file size):
Phương pháp lưu trữ (Storage method):
Dữ liệu API trả về mong đợi (Expected API response):
Hành vi liên quan tới RAG (Related RAG behavior):
Các bước kiểm thử (Testing steps):
```

Ví dụ một prompt tốt:

```text
Hãy triển khai endpoint POST /api/upload tuân theo docs/api-contract.md.
Hỗ trợ định dạng .txt trước.
Trả về document_id, collection_id, filename, file_type, status, và message.
Đừng triển khai tính năng đọc file PDF lúc này.
Không chỉnh sửa các đoạn code liên quan đến chat.
```
