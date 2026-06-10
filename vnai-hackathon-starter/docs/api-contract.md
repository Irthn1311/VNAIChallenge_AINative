# API Contract

Tài liệu này ghi planned API contract cho phase sau. Hiện tại chưa có backend code, nên tất cả endpoint đều có:

```text
Status: Planned
```

Không tạo route thật cho đến khi team chuyển sang implementation phase.

---

## 1. Shared conventions

Base URL trong tương lai:

```text
NEXT_PUBLIC_API_BASE_URL=https://your-api.example.com
```

JSON error response chung:

```json
{
  "detail": "Human-readable error message",
  "code": "OPTIONAL_ERROR_CODE"
}
```

API response phải ổn định để frontend, backend và AI tools không lệch schema.

---

## 2. GET /health

Status: Planned

Purpose:

Kiểm tra backend còn sống trước khi demo hoặc deploy.

Request:

```http
GET /health
```

Response:

```json
{
  "status": "ok",
  "service": "vnai-api",
  "version": "0.1.0"
}
```

Error response:

```json
{
  "detail": "Service unavailable",
  "code": "SERVICE_UNAVAILABLE"
}
```

Notes:

* Endpoint này phải nhẹ, không gọi LLM.
* Dùng cho deployment health check và demo warm-up.

---

## 3. POST /api/chat

Status: Planned

Purpose:

Nhận câu hỏi người dùng và trả câu trả lời có nguồn tham khảo nếu RAG có dữ liệu.

Request:

```json
{
  "session_id": "string",
  "message": "string",
  "collection_id": "string | null"
}
```

Response:

```json
{
  "answer": "string",
  "sources": [
    {
      "title": "string",
      "content": "string",
      "score": 0.87,
      "metadata": {}
    }
  ],
  "actions": [
    {
      "type": "string",
      "label": "string",
      "payload": {}
    }
  ]
}
```

Error response:

```json
{
  "detail": "Message is required",
  "code": "INVALID_MESSAGE"
}
```

Notes:

* Nếu không tìm thấy nguồn phù hợp, answer phải nói rõ không đủ dữ liệu.
* Không hard-code câu trả lời demo trong core logic.
* Context pack: `ai-context/context-packs/chat-rag.md`.

---

## 4. POST /api/upload

Status: Planned

Purpose:

Upload tài liệu để dùng cho RAG hoặc demo data.

Request:

```text
multipart/form-data
file: uploaded file
collection_id: optional string
```

Response:

```json
{
  "document_id": "string",
  "collection_id": "string",
  "filename": "string",
  "file_type": "string",
  "status": "uploaded",
  "message": "Upload received"
}
```

Error response:

```json
{
  "detail": "Unsupported file type",
  "code": "UNSUPPORTED_FILE_TYPE"
}
```

Notes:

* File type và size phải được validate.
* Trong MVP, ưu tiên `.txt`, `.pdf`, `.csv`; OCR ảnh là optional.
* Context pack: `ai-context/context-packs/upload-document.md`.

---

## 5. POST /api/report

Status: Planned

Purpose:

Tạo summary/report từ dữ liệu đã upload, truy vấn, hoặc kết quả phân tích.

Request:

```json
{
  "report_type": "summary | insight | checklist",
  "source_ids": ["string"],
  "question": "string | null",
  "format": "markdown | json"
}
```

Response:

```json
{
  "report_id": "string",
  "title": "string",
  "content": "string",
  "format": "markdown",
  "sources": []
}
```

Error response:

```json
{
  "detail": "No source data provided",
  "code": "MISSING_SOURCE"
}
```

Notes:

* Dùng cho demo flow khi cần kết quả trình bày rõ.
* Report không được đưa ra kết luận không có dữ liệu hỗ trợ.

---

## 6. POST /api/analyze-image

Status: Planned

Purpose:

Phân tích ảnh bằng OCR/CV nếu đề bài cần.

Request:

```text
multipart/form-data
file: image file
task_type: ocr | classification | extraction
```

Response:

```json
{
  "result": {},
  "text": "string | null",
  "confidence": 0.92,
  "explanation": "string"
}
```

Error response:

```json
{
  "detail": "Invalid image file",
  "code": "INVALID_IMAGE"
}
```

Notes:

* CV/OCR là optional module, không được làm hỏng demo chính nếu chưa sẵn sàng.
* Context pack: `ai-context/context-packs/cv-ocr.md`.

