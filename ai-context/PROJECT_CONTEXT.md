# PROJECT_CONTEXT.md

## Tên Dự án (Project Name)

VNAI Hackathon Starter

---

## Giai đoạn Hiện tại (Current Phase)

Giai đoạn chuẩn bị (Preparation phase).

Kho lưu trữ (repository) này đang được sử dụng để định nghĩa hệ thống tài liệu, quy trình làm việc, hợp đồng module (module contracts), các gói ngữ cảnh (context packs), và các hợp đồng API (API contracts) dự kiến trước khi bắt đầu code thật.

Đừng mặc định rằng ứng dụng đã có sẵn code.

---

## Mục đích (Purpose)

Kho lưu trữ này chuẩn bị một nền tảng linh hoạt để xây dựng các sản phẩm AI-native MVP trong suốt cuộc thi Vietnam AI Innovation Challenge 2026.

Mục tiêu không phải là xây sẵn một sản phẩm cố định. Mục tiêu là giúp cả đội có thể triển khai công việc một cách nhanh chóng ngay khi đề bài thực tế được công bố.

---

## Các Mô hình Sản phẩm (Product Patterns)

Dự án starter này hỗ trợ các mô hình có khả năng cao sẽ gặp trong hackathon:

1. Trợ lý Tri thức AI (AI Knowledge Copilot)
   * Hệ thống RAG trên các tài liệu.
   * Trả lời kèm theo nguồn trích dẫn.
   * Tạo ra các checklist hoặc đoạn tóm tắt.

2. Trợ lý Vận hành Doanh nghiệp AI (AI Business Operation Copilot)
   * Phân tích dữ liệu doanh nghiệp.
   * Tóm tắt thông tin khách hàng, đơn hàng, hoạt động hoặc các case study.
   * Đề xuất các hành động tiếp theo.

3. Trợ lý Tài liệu / OCR / CV AI (AI Document / OCR / CV Copilot)
   * Tải lên hình ảnh hoặc tài liệu.
   * Trích xuất văn bản hoặc các trường dữ liệu có cấu trúc.
   * Trả về lời giải thích và độ tin cậy (confidence).

4. Trợ lý Báo cáo AI (AI Report Assistant)
   * Tạo báo cáo từ dữ liệu được tải lên.
   * Hiển thị bảng điều khiển (dashboard) hoặc các thẻ thông tin chi tiết (insight cards).
   * Xuất file hoặc trình bày các kết quả tìm được.

---

## Kiến trúc Dự kiến (Planned Architecture)

```text
Next.js Frontend
  -> FastAPI Backend
  -> Các dịch vụ AI / RAG / CV Services
  -> Supabase PostgreSQL + pgvector + Storage
```

Frontend và backend phải được tích hợp thông qua `docs/api-contract.md`.

---

## Các Thư mục Chính (Main Folders)

```text
apps/web       - frontend Next.js dự kiến
apps/api       - backend FastAPI dự kiến
packages       - các gói dùng chung trong tương lai
docs           - tài liệu để con người (thành viên đội) đọc
ai-context     - ngữ cảnh dự án để AI đọc
data           - dữ liệu demo/đánh giá/seed
scripts        - các đoạn script tiện ích
```

---

## Nguyên tắc Phát triển (Development Principle)

Viết code bằng AI là một công cụ tăng tốc, không phải để thay thế phán đoán kỹ thuật của con người.

Mọi task làm việc với AI phải bao gồm:

* Module liên quan.
* Các file liên quan (Related files).
* Hợp đồng API (API contract).
* Gói ngữ cảnh (Context pack).
* Các ràng buộc (Constraints).
* Danh sách kiểm tra (Testing checklist).

Sự ổn định lúc demo quan trọng hơn một kiến trúc hoàn hảo.
