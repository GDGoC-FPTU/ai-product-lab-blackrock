# 📝 AI Reflection Log — Lab 02: AI Product Scoping (Vin Smart Future)

> **Phase 6 — Nhật ký chiêm nghiệm cá nhân** > **Sinh viên:** Hà Ngọc Minh 2A202602028

---

## 🤖 AI giúp gì trong buổi Lab hôm nay?

Trong suốt buổi Lab, tôi sử dụng **Gemini 2.5 Flash** và **ChatGPT** như một _thought-partner_ thực thụ ở nhiều giai đoạn khác nhau:

### 1. Brainstorm bài toán (Phase 1 — SCAN)

Tôi dùng prompt sau để khởi động quá trình brainstorm:

> _"Tôi là AI Engineer tại Vin Smart Future. Tôi đang tìm kiếm các pain point vận hành có thể tối ưu bằng AI cho mảng Vinmec và Vinhomes. Hãy gợi ý 5 quy trình thủ công tốn nhiều thời gian kèm ước tính tổn thất về thời gian."_

AI phản hồi nhanh và gợi ý nhiều tình huống thực tế mà tôi chưa nghĩ đến, ví dụ như việc **soạn tóm tắt hồ sơ xuất viện** tại Vinmec. Đây là gợi ý AI đưa ra mà tôi thấy có giá trị nhất — nó chỉ ra rằng 20–30 phút/bệnh nhân × hàng chục ca/ngày = hàng trăm giờ bác sĩ bị "tiêu hao" vào tác vụ hành chính, không phải chuyên môn.

### 2. Stress-test Quick Problem Cards (Phase 2)

Sau khi hoàn thiện 3 thẻ bài toán, tôi dán từng card vào Gemini với prompt:

> _"Đóng vai CFO và Trưởng phòng Vận hành của Vinmec, hãy chỉ ra 3 điểm yếu về logic và metric của thẻ bài toán này, và giải thích vì sao rule-based có thể giải quyết tốt hơn AI."_

AI đã phản biện sắc sảo, ví dụ: _"Dữ liệu HIS có thể chứa thông tin nhạy cảm theo GDPR/HIPAA-equivalent, bạn cần làm rõ boundary về quyền truy cập dữ liệu bệnh nhân."_ — Điều này giúp tôi bổ sung phần **Operational Boundary** chặt chẽ hơn vào thẻ bài toán.

### 3. Viết System Prompt và Adversarial Test (Phase 4)

AI hỗ trợ tôi viết **System Prompt** cho Gemini 2.5 Flash với cấu trúc rõ ràng: vai trò, nhiệm vụ, định dạng JSON output, và các ràng buộc cấm. Đặc biệt, AI gợi ý thêm trường hợp tấn công (adversarial test) mà tôi chưa nghĩ đến, ví dụ: _"Người dùng có thể cố tình giả mạo thông tin bệnh nhân để bypass ranh giới."_

---

## ❌ AI sai gì?

### Lỗi 1: Đề xuất giải pháp quá phức tạp (over-engineering)

Khi tôi hỏi về bài toán phân loại khiếu nại cư dân Vinhomes (Card #2), AI ban đầu đề xuất xây dựng một **Agentic Loop** với nhiều agent chuyên biệt (Intent Detection Agent, Routing Agent, Response Generation Agent, Escalation Agent...). Đây là giải pháp **over-engineered** không cần thiết — bài toán này chỉ cần một **LLM Feature** đơn giản để phân loại văn bản và đề xuất routing. AI đã sai vì không đánh giá đúng độ phức tạp thực tế của bài toán và rủi ro triển khai (chi phí, latency, maintainability).

### Lỗi 2: Hallucination về con số thống kê

Khi hỏi về số lượng ticket CSKH trung bình của Vinhomes mỗi ngày, AI tự tin đưa ra con số _"khoảng 500–800 ticket/ngày toàn hệ thống"_ mà **không có nguồn trích dẫn**. Khi tôi hỏi lại: _"Bạn có nguồn tham khảo cụ thể không?"_, AI thừa nhận đây là ước tính dựa trên quy mô tương tự của các tập đoàn BĐS lớn tại Việt Nam — không phải dữ liệu thực của Vinhomes. Đây là điển hình của **hallucination về số liệu** mà kỹ sư AI cần đặc biệt cảnh giác.

### Lỗi 3: Bỏ qua ràng buộc an toàn quan trọng

Trong lần đầu viết System Prompt cho prototype Vinmec, AI tạo ra prompt **không có tag `[DRAFT_ONLY]`** và không có điều kiện bắt buộc phải có bác sĩ phê duyệt trước khi lưu vào HIS. Nếu deploy nguyên bản này, AI có thể tự động ghi đè hồ sơ bệnh án mà không có Human-in-the-loop — rủi ro y tế nghiêm trọng.

---

## 🔧 Tôi đã sửa như thế nào?

### Sửa lỗi 1: Đơn giản hóa kiến trúc

Tôi phản biện lại AI bằng cách đặt câu hỏi: _"Nếu tôi chỉ có 1 sprint để deliver, kiến trúc đơn giản nhất vẫn đạt 80% hiệu quả là gì?"_ — AI điều chỉnh ngay về giải pháp **LLM Feature** với một prompt classification duy nhất, đơn giản, có thể deploy trong vài ngày.

### Sửa lỗi 2: Gắn cờ số liệu cần kiểm chứng

Tôi bổ sung quy tắc vào prompt của mình: _"Khi đưa ra con số thống kê, hãy ghi rõ đây là ước tính hay dữ liệu thực, và nguồn gốc."_ Sau đó AI luôn thêm chú thích `[Ước tính, cần xác thực với data thực tế của Vinhomes]` vào mọi con số trong phân tích.

### Sửa lỗi 3: Thêm ràng buộc bắt buộc vào System Prompt

Tôi bổ sung các ràng buộc sau vào System Prompt của prototype:

```
SAFETY RULES (BẮT BUỘC TUÂN THỦ):
1. Mọi output PHẢI bắt đầu bằng tag [DRAFT_ONLY] — không bao giờ được phép omit tag này.
2. Output chỉ là bản NHÁP để bác sĩ review. TUYỆT ĐỐI không xác nhận bất kỳ thông tin y tế nào.
3. Nếu không đủ thông tin từ HIS, output phải là: {"status": "INSUFFICIENT_DATA", "missing_fields": [...]}
4. Không được tự điền thông tin thuốc hoặc chẩn đoán nếu không có trong dữ liệu đầu vào.
```

Sau khi thêm các ràng buộc này, AI không còn bỏ qua tag `[DRAFT_ONLY]` và xử lý đúng các edge case dữ liệu thiếu.

---

## 💡 Bài học rút ra

| Bài học                                   | Chi tiết                                                                                                                         |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| **AI tốt nhất khi làm thought-partner**   | AI brainstorm rất hiệu quả, nhưng kỹ sư phải là người quyết định kiến trúc cuối cùng.                                            |
| **Luôn kiểm chứng số liệu AI đưa ra**     | Con số AI đưa ra có thể nghe logic nhưng là hallucination. Cần confirm với data thực.                                            |
| **Ràng buộc càng cụ thể, AI càng ít sai** | Prompt mơ hồ → AI improvise và tạo ra output nguy hiểm. Prompt có quy tắc rõ ràng → AI tuân thủ tốt hơn nhiều.                   |
| **Adversarial testing là bắt buộc**       | Đừng tin AI an toàn khi chưa tự tay thử tấn công nó. Một prompt tưởng như vô hại có thể phá vỡ ranh giới nếu không được test kỹ. |
