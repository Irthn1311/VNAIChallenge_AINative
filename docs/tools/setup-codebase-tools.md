# Cài đặt Các Công cụ Ngữ cảnh Codebase (Codebase Context Tools Setup)

Cấu hình này chỉ dành cho mục đích chuẩn bị/cài đặt công cụ/tài liệu. Quá trình này không khởi tạo khung ứng dụng (scaffold) và cũng không cài đặt bất kỳ thư viện phụ thuộc nào cho frontend hay backend.

## Môi trường Đã phát hiện (Environment Detected)

```text
Thư mục hiện tại: D:\SGU\Challenge\Team_VNAIChallenge_DN2026\vnai-hackathon-starter
Node: v22.20.0
npm: 11.16.0
Git: git version 2.49.0.windows.1
Python: Python 3.13.9
Repomix: 1.14.1 qua npx/global package; lệnh PATH trực tiếp chưa hiển thị cho đến khi thêm bin toàn cục của npm vào PATH
CodeGraph: 0.9.9 qua global package; lệnh PATH trực tiếp cần C:\Users\ADMIN\AppData\Roaming\npm có trong biến PATH
GitNexus: 1.6.7 qua npx
```

Vị trí của các file thực thi đã tìm thấy:

```text
node: C:\Program Files\nodejs\node.exe
npm: C:\Program Files\nodejs\npm, C:\Program Files\nodejs\npm.cmd
git: C:\Program Files\Git\bin\git.exe, C:\Program Files\Git\cmd\git.exe
npm global prefix: C:\Users\ADMIN\AppData\Roaming\npm
```

## Kết quả Cài đặt (Installation Result)

| Công cụ   | Kết quả                                                                                  | Kiểm chứng                                                                                                        | Ghi chú                                                                                                                                                                                                                                       |
| --------- | ---------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Repomix   | Đã cài đặt global bằng `npm install -g repomix`; `npx repomix@latest` cũng hoạt động tốt | Lệnh `npx repomix@latest --version` trả về `1.14.1`; Lệnh `repomix --version` (khi đã chỉnh PATH) trả về `1.14.1` | Tiến trình PowerShell hiện tại ban đầu chưa có đường dẫn npm global bin, do đó hãy dùng `npx repomix@latest` hoặc thêm `C:\Users\ADMIN\AppData\Roaming\npm` vào PATH.                                                                         |
| CodeGraph | Đã cài đặt global bằng `npm install -g @colbymchenry/codegraph`                          | Lệnh `codegraph --version` (khi đã chỉnh PATH) trả về `0.9.9`; `codegraph --help` hoạt động                       | Lệnh `codegraph install --target codex --location local` đã hỏi cấu hình PATH và không hoàn thành được tự động. `codegraph install --print-config codex` chỉ in ra đoạn cấu hình MCP Codex.                                                   |
| GitNexus  | Sử dụng qua `npx --yes gitnexus`                                                         | `npx --yes gitnexus --help` hoạt động; siêu dữ liệu npm package hiển thị version `gitnexus` là `1.6.7`            | `npx --yes gitnexus analyze` đã hoàn thành và đánh chỉ mục thư mục Git gốc `D:\SGU\Challenge\Team_VNAIChallenge_DN2026`, chứ không chỉ trong thư mục con này. Nó đã tạo các file `.gitnexus/`, `.claude/`, `AGENTS.md`, và `CLAUDE.md` ở gốc. |

## Các lệnh đã chạy thành công (Commands Run Successfully)

```powershell
pwd
node -v
npm -v
git --version
python --version
where.exe node
where.exe npm
where.exe git
npm install -g repomix
npx repomix@latest --version
npm view @colbymchenry/codegraph version
npm install -g @colbymchenry/codegraph
codegraph --version
codegraph --help
codegraph install --print-config codex
npm view gitnexus version description bin
npx --yes gitnexus --help
npx --yes gitnexus analyze
```

Đối với các CLI global trực tiếp trong shell hiện tại, dòng cấu hình biến môi trường này đã được sử dụng:

```powershell
$env:PATH="$env:APPDATA\npm;$env:PATH"
```

## Các lệnh bị lỗi hoặc bị bỏ qua (Commands Failed Or Skipped)

```powershell
repomix --version
codegraph --version
npx gitnexus --help
```

Các lệnh `repomix` và `codegraph` trực tiếp ban đầu bị lỗi do biến môi trường PATH chưa được cập nhật thư mục npm global bin trong shell. Lệnh `npx gitnexus --help` ban đầu lỗi vì cache offline, sau đó bị quá thời gian, dùng lệnh có thêm `--yes` (`npx --yes gitnexus --help`) thì đã thành công.

```powershell
codegraph install --target codex --location local
```

Lệnh này bắt đầu quá trình tương tác hỏi về biến môi trường PATH và không sinh ra file cấu hình `local` trong project. Để tránh tự ý chỉnh sửa file cấu hình global một cách lẳng lặng, tôi chỉ lưu lại đoạn mã in cấu hình Codex được in ra:

```toml
[mcp_servers.codegraph]
command = "codegraph"
args = ["serve", "--mcp"]
```

## Quy tắc sử dụng (Usage Rules)

- Repomix có thể sử dụng an toàn ngay bây giờ do repo đã chứa thư mục `docs/` và `ai-context/`.
- CodeGraph đã được cài đặt, nhưng nó sẽ hữu ích hơn khi app bắt đầu có mã nguồn thật.
- GitNexus có thể dùng để trực quan hóa cấu trúc và hỗ trợ thành viên mới (onboarding).
- Các file tài liệu Markdown và các gói ngữ cảnh (context packs) luôn luôn là Nguồn chân lý (Source of truth).
- Không commit các file sinh tự động như `.codegraph`, `.gitnexus`, hoặc `repomix-*.md`.
- Đừng coi kết quả trả ra từ GitNexus/CodeGraph là sự thay thế cho thư mục `docs/`, `ai-context/`, bước duyệt code (code review), hay các quyết định rõ ràng của nhóm.

## Các lệnh khuyên dùng (Recommended Commands)

Sử dụng các lệnh global sau khi đã cập nhật biến môi trường PATH (thêm npm global bin), hoặc dùng `npx` như dự phòng cho Repomix.

```powershell
repomix --style markdown --include "docs/**,ai-context/**" --output repomix-docs-context.md
repomix --style markdown --include "docs/**" --output repomix-docs-only.md
repomix --style markdown --include "ai-context/**" --output repomix-ai-context-only.md
npx --yes gitnexus analyze
codegraph --help
```

Lệnh Repomix dự phòng:

```powershell
npx repomix@latest --style markdown --include "docs/**,ai-context/**" --output repomix-docs-context.md
npx repomix@latest --style markdown --include "docs/**" --output repomix-docs-only.md
npx repomix@latest --style markdown --include "ai-context/**" --output repomix-ai-context-only.md
```

## Các thao tác cần làm thủ công (Manual Actions Required)

1. Quyết định xem có nên giữ lại các file do GitNexus tự sinh ra tại thư mục Git gốc hay không: `.gitnexus/`, `.claude/`, `AGENTS.md`, `CLAUDE.md`.
2. Nếu muốn gọi các công cụ trực tiếp tại mọi phiên làm việc mới của PowerShell, bạn hãy thêm đường dẫn `C:\Users\ADMIN\AppData\Roaming\npm` vào biến hệ thống PATH.
3. Nếu bạn muốn Codex dùng CodeGraph MCP, hãy sao chép đoạn cấu hình (đã nêu trên) vào file `C:\Users\ADMIN\.codex\config.toml` hoặc chạy lại trình cài đặt bằng tay với vị trí và mục tiêu mong muốn.
