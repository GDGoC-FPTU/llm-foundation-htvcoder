# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) -> Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00-1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00-1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2-3 câu)
> Khi temperature thấp, đặc biệt là 0.0, câu trả lời thường ổn định, trực tiếp và ít biến đổi giữa các lần gọi. Khi tăng lên 1.0 hoặc 1.5, phản hồi có xu hướng sáng tạo hơn, cách diễn đạt phong phú hơn, nhưng cũng dễ lan man hoặc chọn các chi tiết kém nhất quán hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt temperature khoảng 0.2-0.4 cho chatbot hỗ trợ khách hàng. Mức này giúp câu trả lời vẫn tự nhiên nhưng ưu tiên tính nhất quán, chính xác và ít bịa đặt, phù hợp với các tình huống cần hướng dẫn người dùng theo chính sách hoặc tài liệu có sẵn.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Workload mỗi ngày là 10.000 x 3 x 350 = 10.500.000 token. Nếu giả sử tỷ lệ input/output giống nhau, GPT-4o có giá cao hơn GPT-4o-mini khoảng 33,3 lần vì cả giá input (5.00/0.150) và output (20.00/0.600) đều chênh lệch khoảng 33,3 lần.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng khi tác vụ cần lập luận phức tạp, độ chính xác cao, xử lý yêu cầu mơ hồ hoặc ảnh hưởng trực tiếp đến trải nghiệm quan trọng của người dùng, ví dụ phân tích hồ sơ, tư vấn quy trình nghiệp vụ hoặc tổng hợp thông tin nhiều bước. GPT-4o-mini phù hợp hơn cho tác vụ khối lượng lớn, rủi ro thấp và có khuôn mẫu rõ ràng như phân loại tin nhắn, trả lời FAQ, tóm tắt ngắn hoặc sinh nội dung nháp.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi dài hoặc người dùng đang chờ tương tác trực tiếp, ví dụ chatbot, trợ lý viết nội dung, giải thích từng bước hoặc sinh báo cáo dài, vì người dùng thấy kết quả xuất hiện ngay và cảm giác chờ đợi giảm đáng kể. Non-streaming phù hợp hơn khi cần nhận toàn bộ kết quả rồi mới xử lý tiếp, chẳng hạn phân loại, trích xuất JSON, kiểm thử tự động, ghi log, hoặc các API backend cần một output hoàn chỉnh và dễ kiểm soát lỗi.


## Danh Sách Kiểm Tra Nộp Bài
- [x] Tất cả tests pass: `pytest tests/ -v`
- [x] `call_openai` đã triển khai và kiểm thử
- [x] `call_openai_mini` đã triển khai và kiểm thử
- [x] `compare_models` đã triển khai và kiểm thử
- [x] `streaming_chatbot` đã triển khai và kiểm thử
- [x] `retry_with_backoff` đã triển khai và kiểm thử
- [x] `batch_compare` đã triển khai và kiểm thử
- [x] `format_comparison_table` đã triển khai và kiểm thử
- [x] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định
