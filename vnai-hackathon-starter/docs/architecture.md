# Architecture

Tài liệu này mô tả kiến trúc dự kiến cho MVP AI-native. Hiện tại đây là kiến trúc chuẩn bị, chưa phải code đã triển khai.

---

## 1. Mục tiêu kiến trúc

Kiến trúc cần giúp team:

* Chia việc frontend, backend, AI/RAG/CV rõ ràng.
* Giữ API contract ổn định.
* Dễ demo trong thời gian ngắn.
* Dễ dùng AI coding tools mà không để AI tự bịa cấu trúc.
* Có fallback khi một phần AI service bị lỗi.

---

## 2. Sơ đồ tổng quan

```text
User
  |
  v
Next.js Frontend
  |
  v
FastAPI Backend
  |
  +--> RAG Service
  +--> Upload / Document Service
  +--> Report Service
  +--> CV / OCR Service
  |
  v
Supabase PostgreSQL + pgvector + Storage
```

---

## 3. Thành phần chính

## Frontend - `apps/web`

Vai trò:

* Hiển thị UI.
* Gọi API backend.
* Hiển thị loading, empty, error state.
* Hiển thị kết quả AI, citations, report, upload status.

Không làm:

* Không chứa backend secret.
* Không xử lý logic AI nặng.
* Không tự bịa response format khác API contract.

## Backend - `apps/api`

Vai trò:

* FastAPI routes.
* Validate request.
* Orchestrate service.
* Kết nối Supabase, AI provider, vector search.
* Trả response đúng contract.

Không làm:

* Không trả schema tùy hứng.
* Không trộn UI logic vào backend.
* Không hard-code demo answer trong core service.

## Supabase/PostgreSQL

Vai trò:

* Lưu dữ liệu app.
* Lưu metadata tài liệu.
* Dùng pgvector cho search nếu có RAG.
* Supabase Storage có thể lưu file upload.

## AI services

Có thể gồm:

* LLM generation.
* Embedding.
* RAG retrieval.
* OCR/CV nếu đề bài cần.

AI service phải có fallback và thông báo rõ khi không đủ dữ liệu.

---

## 4. Luồng dữ liệu mẫu

## Chat RAG

```text
User question
  -> Frontend Chat UI
  -> POST /api/chat
  -> Backend validates request
  -> RAG retrieves chunks
  -> LLM generates grounded answer
  -> Backend returns answer + sources
  -> Frontend displays answer and citations
```

## Upload Document

```text
User uploads file
  -> Frontend upload component
  -> POST /api/upload
  -> Backend validates file
  -> Store file / extract text
  -> Optional chunk + embed + index
  -> Return document_id and status
```

## Analyze Image

```text
User uploads image
  -> POST /api/analyze-image
  -> Backend validates image
  -> CV/OCR service extracts result
  -> Backend returns structured result
```

---

## 5. Integration rule

Frontend/backend integration must follow [api-contract.md](api-contract.md).

Nếu đổi request hoặc response:

1. Cập nhật `docs/api-contract.md`.
2. Cập nhật context pack liên quan.
3. Cập nhật `ai-context/MODULE_MAP.md` nếu module boundary đổi.
4. Ghi decision nếu thay đổi lớn.

---

## 6. Preparation status

Status: Planned.

Chưa có app code thật. Tài liệu này dùng để thống nhất hướng trước khi scaffold.

