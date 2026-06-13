# Hướng dẫn GitNexus (GitNexus Guide)

GitNexus dùng để khám phá repo trực quan, hướng dẫn thành viên mới, và hiểu cấu trúc thông qua đồ thị (graph). Trong dự án này, nó nên hỗ trợ điều hướng và review, chứ không thay thế cho các tài liệu Markdown.

## Trạng thái trên máy hiện tại (Status On This Machine)

```text
Phương pháp cài đặt: npx --yes gitnexus
Phiên bản package: 1.6.7
Kiểm tra trợ giúp: npx --yes gitnexus --help
Kiểm tra phân tích: npx --yes gitnexus analyze
```

Lệnh `npx --yes gitnexus analyze` đã hoàn thành thành công:

```text
Repository indexed successfully
539 nodes | 564 edges | 0 clusters | 0 flows
Indexed path: D:\SGU\Challenge\Team_VNAIChallenge_DN2026
```

Lưu ý quan trọng: GitNexus đã phát hiện và đánh chỉ mục thư mục gốc (Git root), chứ không chỉ thư mục `vnai-hackathon-starter`.

## Quan sát các file được sinh ra (Generated Files Observed)

GitNexus đã tạo ra các file không được theo dõi (untracked) này ở thư mục gốc:

```text
D:\SGU\Challenge\Team_VNAIChallenge_DN2026\.gitnexus\
D:\SGU\Challenge\Team_VNAIChallenge_DN2026\.claude\
D:\SGU\Challenge\Team_VNAIChallenge_DN2026\AGENTS.md
D:\SGU\Challenge\Team_VNAIChallenge_DN2026\CLAUDE.md
```

File `.gitignore` ở thư mục gốc đã có dòng loại trừ thư mục `.gitnexus/`. Hãy xem xét xem team muốn giữ lại hay xóa bỏ các file `.claude/`, `AGENTS.md`, và `CLAUDE.md` vừa được tạo ra.

## Các lệnh khuyên dùng (Recommended Commands)

```powershell
npx --yes gitnexus --help
npx --yes gitnexus status
npx --yes gitnexus analyze
npx --yes gitnexus list
npx --yes gitnexus serve
```

Sử dụng lệnh từ thư mục Git gốc nếu bạn muốn phân tích toàn bộ repo:

```powershell
cd D:\SGU\Challenge\Team_VNAIChallenge_DN2026
npx --yes gitnexus analyze
```

Chỉ chạy GitNexus từ trong thư mục dự án này nếu bạn đồng ý với việc GitNexus vẫn tự động tìm lên thư mục Git gốc (parent Git root).

## Khi nào nên dùng (When To Use)

- Hướng dẫn (Onboarding) thành viên mới.
- Giải thích cấu trúc repo trong quá trình team lên kế hoạch.
- Trực quan hóa xem một Pull Request (PR) đang thay đổi những gì.
- Giúp reviewer tìm thấy các tài liệu và module liên quan.

## Tuyệt đối không dùng để (Do Not Use For)

- Quyết định hình dạng API thay cho file `docs/api-contract.md`.
- Thay thế cho việc review code hoặc tài liệu chân lý nguồn (source-of-truth docs).
- Lưu trữ secrets hoặc dữ liệu cá nhân.
- Sinh mã nguồn ứng dụng trong giai đoạn chuẩn bị.

## So sánh các công cụ (Tool Comparison)

| Công cụ | Tốt nhất cho |
| --- | --- |
| GitNexus | Khám phá repo trực quan, hướng dẫn, sơ đồ repo |
| CodeGraph | Các mối quan hệ code có cấu trúc và hỗ trợ MCP |
| Repomix | Đóng gói ngữ cảnh repo được chọn cho LLMs |
| Markdown docs | Nguồn chân lý (Source of truth) cho giai đoạn, hợp đồng, luật code, và vai trò |
