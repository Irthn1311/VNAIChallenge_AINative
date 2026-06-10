# Context Pack: Upload Document

## 1. Purpose

Upload Document receives user files, validates them, stores them, and prepares content for RAG/report workflows.

Preparation goal: define expected behavior before real implementation.

## 2. Owner

Owner: Nguyễn Tuấn Tài

Support: Lư Hồng Phúc, Nguyễn Hữu Tri, Lê Thanh Phát

## 3. Related Files

Existing files:

```text
docs/api-contract.md
docs/module-contract-template.md
ai-context/MODULE_MAP.md
ai-context/context-packs/chat-rag.md
```

Expected future files:

```text
apps/api/routes/upload.py
apps/api/services/upload_service.py
apps/api/services/document_service.py
apps/api/services/vector_service.py
apps/api/schemas/upload.py
apps/web/components/upload/FileUploadBox.tsx
apps/web/components/upload/UploadedFileList.tsx
apps/web/app/upload/page.tsx
data/samples/documents/
```

## 4. Data Flow

```text
User selects file
  -> Next.js upload UI
  -> POST /api/upload
  -> FastAPI upload route
  -> Validate file type and size
  -> Store file or metadata
  -> Extract text if supported
  -> Optional chunk + embed + index
  -> Return document_id / collection_id / status
```

## 5. Input / Output

Input:

```text
multipart/form-data
file: uploaded file
collection_id: optional string
```

Output:

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

## 6. API or Integration Contract

Endpoint:

```text
POST /api/upload
```

Source of truth:

```text
docs/api-contract.md
```

Status: Planned

## 7. Dependencies

* File validation.
* Storage path or Supabase Storage.
* Text extraction.
* Optional chunking.
* Optional embedding.
* Chat RAG module.

## 8. Do Not Rules

* Do not accept unlimited file size.
* Do not silently process unsupported file types.
* Do not hard-code local absolute paths.
* Do not store secrets in uploaded data.
* Do not block forever if indexing fails.
* Do not change upload response shape without updating API contract.

## 9. Common Tasks

* Define supported file types.
* Define max file size.
* Prepare sample files.
* Implement upload route later.
* Implement text extraction later.
* Connect to RAG indexing later.
* Add upload UI later.

## 10. Testing Checklist

```text
[ ] Valid TXT upload works
[ ] Valid PDF upload works if parser is ready
[ ] Unsupported file type is rejected
[ ] Empty file is rejected
[ ] Response includes document_id
[ ] Response includes collection_id
[ ] Frontend shows success state
[ ] Frontend shows error state
```

## 11. Demo Relevance

Medium to high. Upload is impressive when stable, but risky if parser or storage fails.

Prepare:

* 1-2 stable sample documents.
* Pre-indexed fallback document.
* Screenshot/video of successful upload.

## 12. AI Coding Instruction

When asking AI to work on this module, include:

```text
Supported file types:
Max file size:
Storage method:
Expected API response:
Related RAG behavior:
Testing steps:
```

Good prompt:

```text
Implement POST /api/upload according to docs/api-contract.md.
Support .txt first.
Return document_id, collection_id, filename, file_type, status, and message.
Do not implement PDF parsing yet.
Do not modify chat code.
```
