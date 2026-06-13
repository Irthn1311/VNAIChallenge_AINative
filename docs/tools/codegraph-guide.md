# Hướng dẫn CodeGraph (CodeGraph Guide)

CodeGraph hỗ trợ phân tích quan hệ mã nguồn có cấu trúc, tìm kiếm ký hiệu, kiểm tra mức độ ảnh hưởng (impact checks), và sử dụng MCP cho việc code bằng AI. Hiện tại công cụ này đã được cài đặt sẵn để chuẩn bị, nhưng nó sẽ hữu ích hơn sau khi khung ứng dụng và các file source code thực tế đã được tạo ra.

## Trạng thái trên máy hiện tại (Status On This Machine)

```text
Đã cài đặt: có, dưới dạng global npm package @colbymchenry/codegraph
Phiên bản: 0.9.9
Cách kiểm tra: codegraph --version, codegraph --help
```

File thực thi global nằm ở `C:\Users\ADMIN\AppData\Roaming\npm`. Hãy thêm thư mục đó vào biến môi trường PATH để có thể dùng trực tiếp trong các session PowerShell mới, hoặc chạy lệnh sau ở đầu session:

```powershell
$env:PATH="$env:APPDATA\npm;$env:PATH"
```

## Lưu ý về cài đặt MCP (MCP Setup Note)

Lệnh `codegraph install --target codex --location local` đã yêu cầu cấu hình PATH và không thể hoàn thành tự động (non-interactively). Chưa có bộ chỉ mục dự án `.codegraph/` nào được tạo.

Cấu hình MCP cho Codex được in ra an toàn là:

```toml
[mcp_servers.codegraph]
command = "codegraph"
args = ["serve", "--mcp"]
```

Chỉ thêm nó thủ công vào cấu hình Codex khi nào đội thực sự muốn kích hoạt CodeGraph MCP.

## Các lệnh khuyên dùng (Recommended Commands)

```powershell
codegraph --help
codegraph --version
codegraph install --print-config codex
```

Sau khi ứng dụng đã có code thật:

```powershell
codegraph init
codegraph status
codegraph query "chat route"
codegraph impact "symbolName"
```

## Khi nào nên dùng (When To Use)

- Sau khi giai đoạn lập trình bắt đầu.
- Để kiểm tra các mối quan hệ gọi hàm, sử dụng ký hiệu, và ranh giới ảnh hưởng (blast radius).
- Để chuẩn bị các prompt AI với danh sách file liên quan cụ thể.
- Để kiểm tra xem một sự thay đổi có vượt quá ranh giới module hay không.

## Tuyệt đối không dùng để (Do Not Use For)

- Đưa ra các quyết định về sản phẩm.
- Thay thế cho `docs/api-contract.md`, `ai-context/MODULE_MAP.md`, hoặc các context packs.
- Bào chữa cho việc refactor code quy mô lớn khi gần đến hạn chót (deadline).
- Sinh code ứng dụng trong giai đoạn chuẩn bị.

## Quy tắc cho Giai đoạn hiện tại (Current Phase Rule)

Trong suốt giai đoạn chuẩn bị, hãy để CodeGraph đóng vai trò như một công cụ đã được cài đặt. Không chạy các lệnh đánh chỉ mục (indexing) nặng trừ khi team yêu cầu một cách rõ ràng sau khi app đã có code.
