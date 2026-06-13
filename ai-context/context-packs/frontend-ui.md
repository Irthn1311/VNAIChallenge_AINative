# Gói ngữ cảnh: Giao diện Frontend (Frontend UI)

## 1. Mục đích (Purpose)

Giao diện Frontend là ứng dụng Next.js dự kiến mà người dùng sẽ tương tác trong quá trình demo.

Nó cần phải làm cho các tính năng AI trở nên dễ hiểu: tải lên (upload), nhắn tin (chat), báo cáo (report), phân tích hình ảnh (image analysis), trạng thái tải (loading states), và thông báo lỗi rõ ràng.

## 2. Người phụ trách (Owner)

Người phụ trách chính: Nguyễn Tuấn Tài

Hỗ trợ: Lê Thanh Phát, Nguyễn Hữu Tri, Lư Hồng Phúc

## 3. Các file liên quan (Related Files)

Các file hiện có:

```text
docs/api-contract.md
docs/demo-script.md
ai-context/MODULE_MAP.md
```

Các file dự kiến sẽ có:

```text
apps/web/app/
apps/web/components/
apps/web/lib/api-client.ts
apps/web/components/chat/
apps/web/components/upload/
apps/web/components/report/
apps/web/components/image-analysis/
packages/ui/
packages/shared-types/
```

## 4. Luồng dữ liệu (Data Flow)

```text
Hành động của người dùng
  -> UI component (Thành phần giao diện)
  -> API client
  -> FastAPI endpoint
  -> Phản hồi hoặc lỗi
  -> Cập nhật trạng thái UI
```

## 5. Đầu vào / Đầu ra (Input / Output)

Đầu vào:

* Văn bản do người dùng nhập.
* File tải lên.
* Các hành động qua nút bấm (button) hoặc trình đơn chọn (select).
* Lựa chọn dữ liệu mẫu để demo.

Đầu ra:

* Câu trả lời của AI.
* Nguồn trích dẫn (citations).
* Trạng thái tải lên.
* Nội dung báo cáo.
* Kết quả phân tích hình ảnh/OCR.
* Thông báo lỗi rõ ràng.

## 6. Hợp đồng API / Tích hợp (API or Integration Contract)

Frontend phải tuân thủ theo:

```text
docs/api-contract.md
GET /health
POST /api/chat
POST /api/upload
POST /api/report
POST /api/analyze-image
```

Trạng thái: Đang lên kế hoạch (Planned)

## 7. Các thành phần phụ thuộc (Dependencies)

* Next.js.
* Tailwind CSS.
* shadcn/ui.
* Lucide icons.
* Backend API.
* Shared API types (Kiểu dữ liệu API dùng chung, nếu sau này được tạo).

## 8. Những điều tuyệt đối không làm (Do Not Rules)

* Không lưu trữ các mã bảo mật (secrets) của backend ở frontend.
* Không làm trái với hợp đồng API.
* Không giấu các lỗi từ API đối với người dùng (phải hiển thị lỗi).
* Không fix cứng (hard-code) các kết quả demo cuối cùng trừ khi được đánh dấu là phương án dự phòng (fallback).
* Không tạo ra các luồng trang web (page flows) mà không thể mang đi demo được.

## 9. Các nhiệm vụ chung (Common Tasks)

* Lên phác thảo luồng UI (Draft UI flow).
* Xây dựng màn hình chat (làm sau).
* Xây dựng màn hình upload (làm sau).
* Xây dựng màn hình report/demo (làm sau).
* Thêm các trạng thái loading/error/empty.
* Kết nối API client (làm sau).

## 10. Danh sách kiểm thử (Testing Checklist)

```text
[ ] Luồng demo chính có thể dễ dàng được nhìn thấy mà không cần phải giải thích thêm
[ ] Trạng thái Loading hiển thị rõ ràng khi gọi API
[ ] Trạng thái Error rõ ràng, dễ đọc
[ ] Trạng thái Empty giúp định hướng cho người dùng đi tiếp
[ ] Kích thước hiển thị tốt trên thiết bị di động hoặc màn hình máy chiếu
[ ] Base URL của API có thể cấu hình được
```

## 11. Mức độ quan trọng khi Demo (Demo Relevance)

Rất cao. Frontend là thứ đầu tiên mà ban giám khảo nhìn thấy.

Giữ cho giao diện UI đơn giản, ổn định, và dễ nhìn trên màn hình thuyết trình.

## 12. Hướng dẫn Lập trình với AI (AI Coding Instruction)

Khi yêu cầu AI làm việc trên frontend:

```text
Nêu đích danh màn hình/component cần làm.
Đưa kèm hợp đồng API (API contract).
Kèm theo hành vi mong muốn cho các trạng thái loading/error/empty.
Nêu rõ là dùng dữ liệu giả (mock data) hay gọi API thật.
Không cho phép AI đưa logic của backend vào frontend.
```
