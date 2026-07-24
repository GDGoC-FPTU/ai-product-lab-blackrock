# 03 — AI Log & Reflection (Cá nhân)

**Họ và tên:** Phan Hoàng Long
**Bài toán nhóm đã chọn để Deep-Dive:** Quản lý tiến độ & điều phối nhân lực thi công (Vincons) — bài toán do một bạn khác trong nhóm đề xuất tại Phase 2, được cả nhóm thống nhất chọn để làm tiếp Phase 3-5.

---

## 🤝 AI đã giúp tôi những gì?

Trong buổi Lab hôm nay tôi dùng Claude làm thought-partner cho các việc sau:

* **Brainstorm & hoàn thiện Phase 1-2 cá nhân:** Tôi nhờ AI giúp quét (SCAN) các bài toán tiềm năng thuộc nhiều công ty thành viên Vingroup và viết đủ 3 Quick Problem Cards có metric cụ thể (ví dụ: đổi câu mô tả mơ hồ "giảm rõ tiến độ" thành con số đo được như "giảm từ 4 giờ xuống dưới 1 giờ/công trình/tuần").
* **Thiết lập môi trường kỹ thuật cho Phase 4:** AI giúp tôi cài `python-dotenv`, nối `load_dotenv()` vào `prompt_prototype.py` để script tự đọc `GEMINI_API_KEY` từ file `.env` thay vì phải gõ lại biến môi trường mỗi lần mở terminal mới, và xác nhận `.env` đã nằm trong `.gitignore` nên không bị đẩy lên GitHub.
* **Soát lại bảo mật:** Khi tôi dán API Key trực tiếp vào chat, AI chủ động cảnh báo là định dạng key (`AQ.Ab8...`) không giống chuẩn key Google AI Studio thường thấy (`AIzaSy...`), nhắc tôi kiểm tra lại tại aistudio.google.com trước khi tin tưởng chạy thử — giúp tôi tránh mất thời gian debug lỗi auth sau này.
* **Hỗ trợ Git workflow:** Tạo branch theo đúng MSSV, kiểm tra file trước khi commit, và xác nhận lại rằng `.env`/API Key thật sự không lọt vào commit nào trước khi tôi push.

---

## ⚠️ AI đã sai ở đâu?

Điểm sai rõ nhất: khi tôi dán card "Quản lý tiến độ thi công (Vincons)" — vốn là bài toán của **một bạn khác trong nhóm** — và yêu cầu "dùng bài toán này", AI đã **lập tức chèn thẳng nó vào file cá nhân `01-problem-scan.md` của tôi** (thay Card #1, thêm dòng #7 vào bảng SCAN) mà không hỏi lại xem đây có thực sự là ý tưởng do chính tôi tự nghĩ ra trong Phase 1-2 hay không.

Đây không phải lỗi kỹ thuật (hallucination hay code sai), mà là một **lỗi ranh giới liên quan đến tính trung thực học thuật**: file `01-problem-scan.md` là bài chấm điểm cá nhân (15đ), thể hiện tư duy quét bài toán của riêng tôi trước khi thảo luận nhóm — nếu tôi không để ý và nộp luôn bản đó, tôi sẽ vô tình đứng tên cho ý tưởng của người khác trong phần bài cá nhân.

## 🛠️ Tôi đã sửa như thế nào?

Tôi yêu cầu AI gỡ bài toán Vincons ra khỏi `01-problem-scan.md` và khôi phục lại đúng bản gốc (dùng `git checkout` vì file chưa được commit ở trạng thái đã chèn). Bài toán Vincons vẫn được giữ lại đúng chỗ của nó — làm **bài toán chung của cả nhóm** để Deep-Dive ở Phase 3-5 trong `02-deep-dive-report.md`, chứ không lẫn vào phần cá nhân của tôi.

Rút kinh nghiệm cho các buổi sau: trước khi yêu cầu AI chỉnh sửa một tài liệu chấm điểm cá nhân, tôi cần nói rõ ngay từ đầu nguồn gốc của nội dung ("đây là ý tưởng của ai") thay vì để AI mặc định làm theo yêu cầu bề mặt. Tôi cũng sẽ chủ động prompt AI kiểu "hãy hỏi lại tôi nếu nội dung này có thể ảnh hưởng đến tính cá nhân/trung thực của bài nộp" để AI biết dừng lại xác minh thay vì thực thi ngay.
