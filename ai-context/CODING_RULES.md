# CODING_RULES.md

Những quy tắc này dùng để định hướng cho quá trình lập trình (implementation) sau này. Trong giai đoạn chuẩn bị (preparation phase), hãy áp dụng chúng cho tài liệu (documentation), các hợp đồng (contracts) và các gói ngữ cảnh (context packs).

---

## 1. Quy tắc cho Giai đoạn Chuẩn bị (Preparation Phase Rules)

1. Không khởi tạo (scaffold) Next.js hoặc FastAPI cho đến khi được phê duyệt rõ ràng.
2. Không cài đặt các thư viện/packages.
3. Chỉ tập trung thay đổi vào các tài liệu Markdown.
4. Giữ lại những nội dung hiện có nếu chúng hữu ích.
5. Đánh dấu các file code trong tương lai là `expected future file`.
6. Giữ cho tài liệu thực tế và phù hợp với một đội sinh viên thi hackathon.
7. Không viết khống trạng thái hoàn thành của tính năng (fake implementation status).

---

## 2. Quy tắc Code Chung (General Coding Rules)

1. Giữ cho code đơn giản và dễ đọc.
2. Ưu tiên một phiên bản MVP chạy được hơn là một kiến trúc phức tạp.
3. Không tạo ra các hàm tiện ích (utilities) hoặc các dịch vụ (services) trùng lặp.
4. Không fix cứng (hard-code) các thông tin bảo mật (secrets).
5. Sử dụng các biến môi trường (environment variables) cho các thông tin xác thực và URL.
6. Giữ cho định dạng dữ liệu trả về (API response formats) ổn định.
7. Cập nhật tài liệu khi thay đổi các hợp đồng API (API contracts).
8. Thêm xử lý lỗi (error handling) cho các luồng quan trọng khi demo (demo-critical flows).
9. Tự kiểm thử (manual test) trước khi mở một pull request.
10. Không commit code đang bị lỗi lên nhánh `main`.

---

## 3. Quy tắc cho Frontend (Frontend Rules)

1. Tuân thủ các quy ước của Next.js.
2. Giữ cho các UI component tập trung vào một nhiệm vụ (focused).
3. Sử dụng đầy đủ các trạng thái tải (loading), trống (empty), và lỗi (error).
4. Không đưa logic nghiệp vụ (business logic) của backend vào frontend.
5. Không để lộ các khóa API bảo mật (secret API keys).
6. Khớp với các kiểu dữ liệu trả về của API được định nghĩa trong `docs/api-contract.md`.

---

## 4. Quy tắc cho Backend (Backend Rules)

1. Khai báo các route FastAPI một cách rõ ràng.
2. Cố gắng giữ cho các hàm xử lý route (route handlers) càng gọn nhẹ càng tốt.
3. Đặt logic nghiệp vụ vào phần dịch vụ (services).
4. Kiểm tra tính hợp lệ của dữ liệu đầu vào (request payloads).
5. Trả về cấu trúc response đúng như tài liệu đã mô tả.
6. Thêm endpoint `/health` để kiểm tra trạng thái triển khai (deployment checks).
7. Không bỏ qua (bypass) các tầng dịch vụ (service layers).
8. Không đặt các logic đặc thù của frontend vào backend.

---

## 5. Quy tắc cho AI / RAG (AI / RAG Rules)

1. Các câu trả lời của hệ thống RAG phải kèm theo nguồn trích dẫn (sources) nếu có thể.
2. Không để AI bịa đặt (hallucinate) các thông tin không được hỗ trợ.
3. Nếu không tìm thấy câu trả lời trong dữ liệu, hãy nói rõ điều đó.
4. Quản lý phiên bản (versioned) của các prompt trong `packages/prompts` hoặc trong các file prompt của backend.
5. Tách biệt logic của quá trình truy xuất (retrieval), tạo prompt (prompting), và sinh văn bản (generation).
6. Thêm các câu hỏi dùng để đánh giá (evaluation questions) vào thư mục `data/eval`.

---

## 6. Quy tắc khi Demo (Demo Rules)

1. Luồng demo phải được kiểm thử cẩn thận trước khi thuyết trình.
2. Sử dụng dữ liệu mẫu (sample data) ổn định.
3. Chuẩn bị sẵn dữ liệu phản hồi được lưu tạm (cached response) hoặc ảnh chụp màn hình (screenshot) làm phương án dự phòng (fallback).
4. Không refactor code khi đã cận kề thời gian demo.
5. Không thêm các tính năng lớn sau khi đã đóng băng tính năng (feature freeze).
