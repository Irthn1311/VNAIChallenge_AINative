# Demo Script

Tài liệu này là khung kịch bản demo. Team sẽ cập nhật theo đề bài thật.

---

## 1. Demo goal

Trong 3-5 phút, người xem phải hiểu:

* Vấn đề là gì.
* Người dùng mục tiêu là ai.
* Sản phẩm giải quyết bằng AI như thế nào.
* Kết quả demo có đáng tin và hữu ích không.

---

## 2. Demo flow template

## Step 1: Problem setup

Nói ngắn:

```text
Người dùng gặp khó khăn gì?
Tại sao cách hiện tại chậm, tốn chi phí hoặc dễ sai?
```

## Step 2: Show input

Ví dụ:

* Upload tài liệu.
* Nhập câu hỏi.
* Upload ảnh.
* Chọn bộ dữ liệu mẫu.

## Step 3: Show AI processing result

Ví dụ:

* Câu trả lời có nguồn.
* Summary/report.
* OCR result.
* Insight dashboard.

## Step 4: Show trust signal

Ví dụ:

* Citations.
* Confidence.
* Source preview.
* Manual verification.
* Clear fallback if not enough data.

## Step 5: Business/social impact

Nói ngắn:

* Tiết kiệm thời gian gì?
* Giảm lỗi gì?
* Ai được lợi?

---

## 3. Demo data

Chuẩn bị trước:

* 2-3 sample documents.
* 3 stable questions.
* 1 unsupported question để chứng minh hệ thống biết từ chối.
* 1 screenshot fallback.
* 1 short video fallback nếu mạng/API lỗi.

Lưu ở:

```text
data/samples/
data/eval/
```

---

## 4. Speaker notes

```text
Opening:

Demo action 1:

Expected output:

Demo action 2:

Expected output:

Fallback line if API fails:

Closing:
```

---

## 5. Demo freeze checklist

Trước khi demo:

```text
[ ] Demo data đã ổn định
[ ] API health check pass
[ ] Flow chính đã chạy ít nhất 3 lần
[ ] Screenshot/video fallback đã sẵn sàng
[ ] Người demo biết câu hỏi mẫu
[ ] Không còn đổi feature
```

