# Quy trình Sử dụng Ngữ cảnh Codebase (Codebase Context Workflow)

Quy trình này kết nối Repomix, CodeGraph, GitNexus và các tài liệu/gói ngữ cảnh (context packs) dạng Markdown.

Giai đoạn hiện tại:

```text
Chỉ là giai đoạn chuẩn bị/cài đặt công cụ/viết tài liệu.
Chưa khởi tạo dự án Next.js.
Chưa khởi tạo dự án FastAPI.
Chưa có code triển khai sản phẩm.
Chưa có các thư viện phụ thuộc (dependencies) của ứng dụng frontend/backend.
```

## Vai trò của các công cụ (Tool Roles)

| Công cụ | Vai trò |
| --- | --- |
| Repomix | Đóng gói ngữ cảnh repo được chọn cho ChatGPT, Claude, Gemini hoặc LLM khác |
| CodeGraph | Phân tích quan hệ mã nguồn có cấu trúc, tìm kiếm ký hiệu (symbol search), phân tích mức độ ảnh hưởng (impact analysis), hỗ trợ MCP |
| GitNexus | Khám phá repo trực quan, hướng dẫn thành viên mới (onboarding), và sơ đồ repo (repo graph) |
| Markdown docs/context packs | Nguồn chân lý (Source of truth) cho giai đoạn dự án, các quy tắc, vai trò, hợp đồng, và ranh giới module |

## Quy trình làm việc trong Giai đoạn Chuẩn bị (Preparation Phase Workflow)

1. Đọc `README.md`.
2. Đọc `docs/team-onboarding-guide.md`.
3. Đọc `docs/definition-of-done.md`.
4. Đọc `ai-context/AGENTS.md`.
5. Đọc `ai-context/MODULE_MAP.md`.
6. Đọc `docs/api-contract.md` nếu có liên quan đến chủ đề API.
7. Sử dụng Repomix để đóng gói `docs/**` và `ai-context/**` cho AI phân tích.
8. Sử dụng GitNexus để xem tổng quan repo nếu cần thiết.
9. Giữ cài đặt CodeGraph nhưng tránh việc đánh chỉ mục (indexing) quá nhiều cho đến khi có code thật.

Dừng lại ở đây trong giai đoạn chuẩn bị.

## Quy trình làm việc trong Giai đoạn Lập trình (Implementation Phase Workflow)

Chỉ thực hiện sau khi đội chính thức bước vào giai đoạn lập trình (implementation):

1. Đọc hợp đồng module (module contract) và gói ngữ cảnh (context pack).
2. Dùng GitNexus để hiểu rõ khu vực code trong repo.
3. Dùng CodeGraph để kiểm tra các mối quan hệ của code và mức độ ảnh hưởng.
4. Dùng Repomix để đóng gói các ngữ cảnh được chọn nếu cần nhờ LLM hỗ trợ.
5. Cung cấp ranh giới file chính xác và các quy tắc "không được làm" (do-not rules) vào prompt cho AI.
6. Kiểm thử (Test).
7. Cập nhật docs/context nếu hợp đồng API hoặc ranh giới module có thay đổi.
8. Mở Pull Request (PR).

## Các lệnh khuyên dùng (Recommended Commands)

```powershell
repomix --style markdown --include "docs/**,ai-context/**" --output repomix-docs-context.md
repomix --style markdown --include "docs/**" --output repomix-docs-only.md
repomix --style markdown --include "ai-context/**" --output repomix-ai-context-only.md
npx --yes gitnexus analyze
codegraph --help
```

Các lệnh Repomix dự phòng:

```powershell
npx repomix@latest --style markdown --include "docs/**,ai-context/**" --output repomix-docs-context.md
```

## Danh sách kiểm tra trước khi sửa code (Before Editing Code Checklist)

```text
[ ] Team đã xác nhận bước vào giai đoạn lập trình (implementation phase)
[ ] Người phụ trách module đã được ghi rõ trong ai-context/MODULE_MAP.md
[ ] Đã có hợp đồng module hoặc phạm vi (scope) được xác định rõ
[ ] Đã đọc gói ngữ cảnh (context pack)
[ ] Đã đọc hợp đồng API nếu hành vi của endpoint có liên quan
[ ] Các file liên quan đã được xác định
[ ] Các quy tắc "Tuyệt đối không" (Do-not rules) đã rõ ràng
[ ] Cách kiểm thử (Test) hoặc xác minh thủ công đã được định nghĩa
```

## Các thói quen xấu cần tránh (Anti-Patterns)

- Yêu cầu AI xây dựng tính năng mà không có gói ngữ cảnh/tài liệu liên quan.
- Gửi toàn bộ repo cho AI trong khi chỉ cần ngữ cảnh của một module là đủ.
- Coi kết quả đầu ra của GitNexus hoặc CodeGraph là nguồn chân lý thay vì các tài liệu Markdown.
- Thay đổi hành vi API mà không cập nhật file `docs/api-contract.md`.
- Commit các file đầu ra được tạo tự động như `.codegraph`, `.gitnexus`, hoặc `repomix-*.md`.
- Dựng khung (scaffold) ứng dụng trong giai đoạn chuẩn bị.
