# Module Contract Template

Mỗi module nên có contract trước khi code. Contract giúp owner, support, frontend, backend và AI coding tools hiểu cùng một phạm vi.

---

## 1. Blank Template

```markdown
# Module Contract: [Module Name]

## Module name

## Owner

## Support

## Purpose

## Input

## Output

## API / Integration point

## Related files

## Dependencies

## Do not rules

## Testing checklist

## Demo relevance
```

---

## 2. Example: Chat RAG

## Module name

Chat RAG

## Owner

Lư Hồng Phúc

## Support

Backend/API, AI, Frontend/UI

## Purpose

Cho phép người dùng hỏi đáp trên tài liệu đã upload hoặc dữ liệu mẫu. Câu trả lời phải có nguồn nếu có dữ liệu liên quan.

## Input

```json
{
  "session_id": "string",
  "message": "string",
  "collection_id": "string | null"
}
```

## Output

```json
{
  "answer": "string",
  "sources": [],
  "actions": []
}
```

## API / Integration point

```text
POST /api/chat
```

## Related files

```text
docs/api-contract.md
ai-context/context-packs/chat-rag.md
apps/api/routes/chat.py - expected future file
apps/web/components/chat/ChatWindow.tsx - expected future file
```

## Dependencies

* Upload Document module.
* Supabase pgvector.
* LLM provider.
* Prompt templates.

## Do not rules

* Do not answer unsupported questions as facts.
* Do not change response schema without updating API contract.
* Do not expose API keys to frontend.

## Testing checklist

```text
[ ] Valid question returns answer
[ ] Sources are returned when available
[ ] Unsupported question is handled safely
[ ] Empty message is handled
[ ] Frontend displays error state
```

## Demo relevance

Core demo module for most AI-native products.

---

## 3. Example: Upload Document

## Module name

Upload Document

## Owner

Nguyễn Tuấn Tài

## Support

Backend/API, AI/RAG, Frontend/UI

## Purpose

Cho phép người dùng upload file để hệ thống lưu, đọc nội dung và dùng cho RAG hoặc report.

## Input

```text
multipart/form-data
file: uploaded file
collection_id: optional string
```

## Output

```json
{
  "document_id": "string",
  "collection_id": "string",
  "filename": "string",
  "file_type": "string",
  "status": "uploaded",
  "message": "string"
}
```

## API / Integration point

```text
POST /api/upload
```

## Related files

```text
docs/api-contract.md
ai-context/context-packs/upload-document.md
apps/api/routes/upload.py - expected future file
apps/web/components/upload/FileUploadBox.tsx - expected future file
```

## Dependencies

* File validation.
* Storage.
* Text extraction.
* Optional chunking/embedding.

## Do not rules

* Do not accept unlimited file size.
* Do not silently accept unsupported file types.
* Do not hard-code local absolute paths.

## Testing checklist

```text
[ ] Valid TXT upload works
[ ] Unsupported file is rejected
[ ] Empty file is rejected
[ ] Response includes document_id and collection_id
[ ] Upload error is shown clearly
```

## Demo relevance

Important if demo starts from user-provided data. Prepare preloaded fallback.

---

## 4. Example: CV/OCR Module

## Module name

CV/OCR

## Owner

Lư Hồng Phúc

## Support

AI, Backend/API, Product/Demo

## Purpose

Nhận ảnh hoặc tài liệu ảnh, trích xuất text hoặc phân tích nội dung bằng OCR/CV.

## Input

```text
multipart/form-data
file: image file
task_type: ocr | classification | extraction
```

## Output

```json
{
  "result": {},
  "text": "string | null",
  "confidence": 0.92,
  "explanation": "string"
}
```

## API / Integration point

```text
POST /api/analyze-image
```

## Related files

```text
docs/api-contract.md
ai-context/context-packs/cv-ocr.md
apps/api/services/cv - expected future folder
apps/web/components/image-analysis - expected future folder
```

## Dependencies

* OCR/CV model or API.
* Image validation.
* Optional storage.

## Do not rules

* Do not block the main demo if CV is optional.
* Do not claim high accuracy without evaluation.
* Do not return unstructured output if frontend needs fields.

## Testing checklist

```text
[ ] Valid image returns structured result
[ ] Invalid image is rejected
[ ] Confidence/explanation is present
[ ] Slow model has fallback
```

## Demo relevance

Useful when challenge problem involves forms, documents, images, receipts, or visual inspection.
