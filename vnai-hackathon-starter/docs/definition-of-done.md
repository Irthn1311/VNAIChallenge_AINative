# Definition of Done

Tài liệu này định nghĩa khi nào một task hoặc module được xem là "xong". Mục tiêu là tránh tình trạng "xong trên máy em" nhưng chưa sẵn sàng để người khác dùng, review hoặc demo.

---

## 1. Definition of Done for documentation tasks

Một documentation task được xem là done khi:

* Nội dung đúng phase hiện tại.
* Không nói rằng feature đã implemented nếu chỉ mới planned.
* Có link đến file liên quan nếu cần.
* Dễ đọc với thành viên mới.
* Không chứa secret, token, private data.
* Không mâu thuẫn với `README.md`, `MODULE_MAP.md`, hoặc `docs/api-contract.md`.

---

## 2. Definition of Done for module contract

Module contract done khi có đủ:

* Module name.
* Owner và support, có thể để `TBD` trong preparation phase.
* Purpose.
* Input.
* Output.
* API / integration point.
* Related files, gồm cả expected future files nếu chưa code.
* Dependencies.
* Do not rules.
* Testing checklist.
* Demo relevance.

Contract phải đủ rõ để một người khác hoặc AI coding tool hiểu phạm vi module.

---

## 3. Definition of Done for API contract

API contract done khi có:

* Endpoint.
* Purpose.
* Request shape.
* Response shape.
* Error response.
* Notes.
* Status: `Planned`, `Mock`, hoặc `Implemented`.
* Context pack liên quan nếu có.

Nếu frontend/backend đã code, contract phải khớp implementation. Nếu chưa code, phải ghi rõ là planned.

---

## 4. Definition of Done for frontend task

Frontend task done khi:

* UI đáp ứng đúng user flow.
* Loading, empty, error states có xử lý.
* API call dùng đúng contract.
* Không chứa backend secret.
* Không hard-code demo output trừ khi được đánh dấu fallback.
* Manual test flow chính đã chạy.
* Demo impact đã được ghi trong PR.

---

## 5. Definition of Done for backend task

Backend task done khi:

* Route/service đúng API contract.
* Request được validate.
* Response và error response ổn định.
* Không hard-code secret.
* Không tạo duplicate endpoint.
* Có handling cho lỗi demo-critical.
* `/health` không bị phụ thuộc vào AI call chậm.
* Manual smoke test pass.

---

## 6. Definition of Done for AI/RAG/CV task

AI/RAG/CV task done khi:

* Input/output rõ ràng.
* Có xử lý unsupported case.
* RAG answer có sources khi có dữ liệu.
* Prompt hoặc model behavior được ghi lại.
* Eval/sample questions được cập nhật nếu cần.
* Có fallback nếu LLM/vector/OCR lỗi.
* Không claim accuracy nếu chưa có evidence.
* Không expose API keys hoặc private data.

---

## 7. Definition of Done for demo/pitch task

Demo/pitch task done khi:

* Demo script có flow rõ.
* Sample data đã chuẩn bị.
* Sample questions đã test.
* Screenshot/video fallback có sẵn nếu cần.
* Pitch deck có story: problem, solution, demo, impact.
* Speaker notes hoặc talking points đã có.
* Demo freeze/pitch freeze được team biết.

---

## 8. Definition of Done for pull request

PR done khi:

* PR template được điền đủ.
* Scope rõ và không đổi file ngoài phạm vi.
* API contract impact được ghi.
* Context pack đã đọc hoặc cập nhật nếu cần.
* Cách test được mô tả.
* Demo impact và risk level được ghi.
* Reviewer hiểu được thay đổi mà không cần hỏi lại quá nhiều.

---

## 9. Hackathon-specific Definition of Done

Trong hackathon, done không chỉ là code chạy. Done nghĩa là:

* Người khác trong team dùng được.
* Demo flow không bị phá.
* Có fallback cho phần rủi ro.
* Không làm tăng complexity không cần thiết.
* Nếu gần deadline, thay đổi phải nhỏ và có lợi trực tiếp cho demo.

Ưu tiên:

1. Demo chạy ổn.
2. Output đáng tin.
3. UI dễ hiểu.
4. Code đủ sạch để sửa nhanh.
5. Docs đủ rõ để handoff.

---

## 10. What does NOT count as done

Không được xem là done nếu:

* Chỉ mới "AI generated" nhưng chưa review.
* Chỉ chạy trên một máy nhưng không ghi cách test.
* API response khác contract.
* Owner không biết task đã đổi gì.
* Demo flow bị ảnh hưởng nhưng không báo.
* Có secret/private data trong file.
* Placeholder vẫn còn nhưng được trình bày như đã hoàn tất.
* Không có fallback cho phần demo-critical rủi ro cao.

