# Context Pack: CV/OCR

## 1. Purpose

CV/OCR handles image-based tasks such as extracting text, classifying an image, or returning structured information from a visual input.

This is optional unless the challenge problem needs it.

## 2. Owner

Owner: Lư Hồng Phúc

Support: Nguyễn Tuấn Tài, Nguyễn Hữu Tri, Lê Thanh Phát

## 3. Related Files

Existing files:

```text
docs/api-contract.md
docs/module-contract-template.md
ai-context/MODULE_MAP.md
```

Expected future files:

```text
apps/api/routes/image.py
apps/api/services/cv_service.py
apps/api/schemas/image_analysis.py
apps/web/components/image-analysis/ImageUploadBox.tsx
apps/web/components/image-analysis/ImageResultPanel.tsx
data/samples/images/
data/eval/cv_ocr_eval.md
```

## 4. Data Flow

```text
User uploads image
  -> Frontend image upload UI
  -> POST /api/analyze-image
  -> Backend validates image
  -> OCR/CV service processes input
  -> Backend returns structured result
  -> Frontend displays result, confidence, explanation
```

## 5. Input / Output

Input:

```text
multipart/form-data
file: image file
task_type: ocr | classification | extraction
```

Output:

```json
{
  "result": {},
  "text": "string | null",
  "confidence": 0.92,
  "explanation": "string"
}
```

## 6. API or Integration Contract

Endpoint:

```text
POST /api/analyze-image
```

Source of truth:

```text
docs/api-contract.md
```

Status: Planned

## 7. Dependencies

* Image validation.
* OCR/CV model or external API.
* Optional storage.
* Frontend image upload component.
* Evaluation sample images.

## 8. Do Not Rules

* Do not make CV/OCR required for main demo unless stable.
* Do not process huge images without limits.
* Do not claim accuracy without testing.
* Do not return unstructured text if frontend expects fields.
* Do not expose provider keys.

## 9. Common Tasks

* Decide whether CV/OCR is needed for the real problem.
* Prepare sample images.
* Define output schema.
* Implement OCR first if full CV is too risky.
* Add fallback screenshot/output.

## 10. Testing Checklist

```text
[ ] Valid image returns result
[ ] Invalid file is rejected
[ ] Large file is handled safely
[ ] Confidence/explanation is present
[ ] Demo image has stable output
[ ] Fallback output exists
```

## 11. Demo Relevance

Medium. Strong if the problem is document/image-heavy. Risky if model latency or accuracy is unstable.

Use only if it strengthens the story and can be tested early.

## 12. AI Coding Instruction

When asking AI to work on CV/OCR:

```text
Specify task type: OCR, classification, or extraction.
Specify accepted file types and size limit.
Paste API contract.
Require structured output.
Require fallback/error behavior.
Do not connect heavy models without approval.
```
