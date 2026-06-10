# Team Workflow

Workflow này dành cho team hackathon 4 người, ưu tiên rõ việc, nhanh, ít conflict và demo ổn định.

---

## 1. Vai trò đề xuất

* Nguyễn Hữu Tri - Technical Lead / Integration Lead: system architecture, API contract direction, integration, merge/demo stability.
* Lư Hồng Phúc - AI/RAG/CV Lead: RAG/CV/OCR design, prompt support, AI eval, AI context packs.
* Nguyễn Tuấn Tài - Frontend/Backend Software Developer: UI/API implementation support, integration, bug fixing.
* Lê Thanh Phát - Product Flow / Demo / Pitch Support: user journey, demo script, sample data planning, pitch story.

Đây là ownership role, không phải ranh giới cứng. Thành viên có thể hỗ trợ nhau, nhưng mỗi module phải có một owner chính.

Chi tiết phân vai nằm ở [team-role-assignment.md](team-role-assignment.md).

---

## 2. Quy trình nhận task

Trước khi làm task:

1. Đọc issue/task description.
2. Xác định module liên quan trong `ai-context/MODULE_MAP.md`.
3. Đọc context pack tương ứng.
4. Kiểm tra API contract nếu có frontend/backend interaction.
5. Ghi rõ files dự kiến đụng vào.
6. Nếu chưa rõ, hỏi trước khi code.

---

## 3. Branch và PR

Tên branch:

```text
docs/...
feature/...
fix/...
experiment/...
```

PR phải có:

* Summary.
* Module liên quan.
* Files changed.
* API contract impact.
* Cách test.
* Demo impact.
* Risk level.

Không push trực tiếp vào `main`.

---

## 4. Daily sync nhanh

Mỗi người trả lời 3 câu:

1. Hôm qua làm gì?
2. Hôm nay làm gì?
3. Đang bị block ở đâu?

Nếu task ảnh hưởng API/demo, nói rõ trong sync.

---

## 5. AI coding workflow

Khi dùng Codex, ChatGPT, Claude, Gemini/Antigravity:

* Luôn đưa context pack.
* Luôn đưa API contract nếu liên quan.
* Luôn ghi "do not change unrelated files".
* Không yêu cầu AI scaffold rộng khi task nhỏ.
* Review diff trước khi merge.

Chi tiết ở [ai-coding-workflow.md](ai-coding-workflow.md).

---

## 6. Definition of Done

Một task được xem là xong khi:

* Đúng scope.
* Không đổi file ngoài phạm vi.
* Manual test pass.
* Docs/context pack cập nhật nếu contract thay đổi.
* Demo flow không bị ảnh hưởng xấu.
* PR mô tả rõ ràng.

---

## 7. Khi gần deadline

Trong 2 giờ cuối:

* Chỉ sửa bug demo-critical.
* Không thêm module mới.
* Không refactor lớn.
* Ưu tiên fallback, sample data, screenshot/video.

Trong 1 giờ cuối:

* Demo freeze.
* Pitch freeze.
* Chỉ chạy lại flow đã test.
