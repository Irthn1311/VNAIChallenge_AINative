# VNAI Hackathon Starter

Repository chuẩn bị cho Vietnam AI Innovation Challenge 2026.

Mục tiêu hiện tại: xây hệ thống tài liệu, workflow, module contract và context pack để team có thể code nhanh, rõ ràng, ít lệch hướng khi vào hackathon thật.

> Trạng thái hiện tại: preparation phase. Chưa scaffold Next.js, FastAPI, Supabase hoặc app code thật.

---

## 1. Repo này dùng để làm gì?

Repo này giúp team 4 người chuẩn bị trước:

* Quy trình làm việc khi dùng AI coding tools.
* Cấu trúc thư mục dự kiến cho MVP AI-native.
* API contract trước khi frontend/backend code.
* Module contract để chia việc rõ ràng.
* Context pack để Codex, ChatGPT, Claude, Gemini/Antigravity hiểu đúng phạm vi.
* Demo script, pitch template, checklist an toàn trước khi trình bày.

Repo này không phải là sản phẩm cuối cùng. Đây là nền tảng để team có thể bắt đầu nhanh khi đề bài thật xuất hiện.

---

## 2. Stack dự kiến

Technical stack:

* Frontend: Next.js
* UI: Tailwind CSS + shadcn/ui
* Backend: FastAPI
* Database: Supabase PostgreSQL
* Vector search: Supabase pgvector trước, Qdrant chỉ dùng nếu thật sự cần
* Frontend deployment: Vercel
* Backend deployment: Railway hoặc Render

Team tools:

* GitHub: source code, branches, pull requests
* Zalo: trao đổi nhanh
* Docs / Notion / OneNote: planning và notes
* Canva: pitch deck
* ChatGPT Plus: planning, prompt design, review
* Codex: implementation có kiểm soát
* Gemini / Antigravity: coding support, quick prototype
* Claude: reasoning, refactor, review
* GitNexus, CodeGraph, Repomix: hiểu codebase và đóng gói context cho AI

Chi tiết quyết định nằm ở [docs/tool-stack-decision.md](docs/tool-stack-decision.md).

---

## 3. Cấu trúc repo

```text
vnai-hackathon-starter/
├── apps/                    # vị trí app thật trong tương lai
│   ├── web/                 # Next.js frontend, chưa scaffold
│   └── api/                 # FastAPI backend, chưa scaffold
├── packages/                # shared packages trong tương lai
├── docs/                    # tài liệu team đọc
├── ai-context/              # tài liệu AI coding tools đọc
│   └── context-packs/       # context theo từng module
├── data/                    # sample, seed, eval data
├── scripts/                 # script tiện ích trong tương lai
└── .github/                 # PR template và workflow
```

Đọc chi tiết ở [docs/repository-guide.md](docs/repository-guide.md).

---

## 4. Cách đọc repo cho thành viên mới

Thứ tự đề xuất:

1. Đọc README này.
2. Đọc [docs/team-onboarding-guide.md](docs/team-onboarding-guide.md).
3. Đọc [docs/tool-stack-decision.md](docs/tool-stack-decision.md).
4. Đọc [docs/preparation-roadmap.md](docs/preparation-roadmap.md).
5. Đọc [ai-context/MODULE_MAP.md](ai-context/MODULE_MAP.md).
6. Chọn một module và đọc context pack tương ứng trong `ai-context/context-packs/`.
7. Viết module contract bằng [docs/module-contract-template.md](docs/module-contract-template.md).

---

## 5. Quy tắc quan trọng

### Contract trước, code sau

Trước khi code một module, team phải biết:

* Module làm gì?
* Ai owner?
* Input là gì?
* Output là gì?
* API/integration point nào?
* File nào liên quan?
* Không được đụng vào phần nào?
* Test bằng cách nào?

### AI coding phải có context

Không prompt kiểu:

```text
Build the chat feature.
```

Prompt phải có:

* Task rõ ràng
* File liên quan
* API contract
* Context pack
* Constraints
* Testing checklist

Workflow chi tiết ở [docs/ai-coding-workflow.md](docs/ai-coding-workflow.md).

### Demo stability quan trọng hơn kiến trúc đẹp

Khi gần demo:

* Không đổi flow lớn.
* Không refactor không cần thiết.
* Không thêm feature chưa test.
* Luôn có fallback: sample data, cached response, screenshot/video.

Checklist ở [docs/demo-safety-checklist.md](docs/demo-safety-checklist.md).

---

## 6. API dự kiến

Chưa có backend code. Các endpoint sau chỉ là planned contract:

* `GET /health`
* `POST /api/chat`
* `POST /api/upload`
* `POST /api/report`
* `POST /api/analyze-image`

Chi tiết request/response ở [docs/api-contract.md](docs/api-contract.md).

---

## 7. Development setup

Chưa có lệnh setup thật vì app chưa được scaffold.

Khi bước vào implementation phase, team mới bổ sung:

* Next.js setup trong `apps/web`
* FastAPI setup trong `apps/api`
* Supabase env setup
* Script seed/eval nếu cần

Không install package hoặc tạo app thật trong preparation phase.

---

## 8. Current preparation outputs

Team cần hoàn thành trước khi code:

* Documentation system hoàn chỉnh.
* Module owners trong `ai-context/MODULE_MAP.md`.
* Module contracts cho các module chính.
* Context packs đã đọc và cập nhật.
* Mock task plan đã chạy thử.
* Demo safety checklist đã thống nhất.

Chỉ sau đó mới scaffold Next.js/FastAPI.

