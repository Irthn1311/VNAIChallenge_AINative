# Demo Safety Checklist

Checklist này giúp tránh demo fail trong giờ cuối.

---

## 1. Demo data

```text
[ ] Có sample documents
[ ] Có sample images nếu dùng CV/OCR
[ ] Có sample CSV/data nếu dùng report/dashboard
[ ] Không dùng dữ liệu riêng tư hoặc nhạy cảm
[ ] Data đã test trước trên máy demo
```

---

## 2. Sample questions

```text
[ ] Có 3 câu hỏi chắc chắn trả lời tốt
[ ] Có 1 câu hỏi ngoài dữ liệu để test refusal
[ ] Có expected answer ngắn cho từng câu
[ ] Người demo đã luyện thứ tự câu hỏi
```

---

## 3. Cached responses

```text
[ ] Có cached response cho flow chính
[ ] Cached response được đánh dấu rõ là fallback
[ ] Không hard-code fallback vào core logic nếu không cần
```

---

## 4. Screenshot/video fallback

```text
[ ] Có screenshot kết quả chính
[ ] Có video ngắn nếu mạng/API lỗi
[ ] File fallback mở được offline
```

---

## 5. Local fallback

```text
[ ] Có cách chạy local nếu deploy lỗi
[ ] Env local đã chuẩn bị
[ ] Dữ liệu local giống demo data
```

---

## 6. API health check

```text
[ ] GET /health pass
[ ] Backend logs không có lỗi nghiêm trọng
[ ] Frontend gọi đúng API base URL
[ ] CORS đã test
```

---

## 7. Deployment warm-up

```text
[ ] Mở frontend trước demo
[ ] Gọi API trước demo để tránh cold start
[ ] Kiểm tra Supabase/API provider quota
```

---

## 8. Freeze rules

Feature freeze:

```text
[ ] Không thêm feature mới
[ ] Chỉ sửa bug đã biết
```

Demo freeze:

```text
[ ] Flow demo đã chốt
[ ] Không đổi sample data
[ ] Không đổi câu hỏi demo
```

Pitch freeze:

```text
[ ] Slide đã export
[ ] Speaker notes đã chốt
[ ] Timer đã luyện
```

---

## 9. Final 1-hour rules

Trong 1 giờ cuối:

* Không refactor.
* Không đổi dependency.
* Không đổi API schema.
* Không thêm module.
* Chỉ kiểm tra lại flow và fallback.
* Một người giữ máy demo ổn định.

