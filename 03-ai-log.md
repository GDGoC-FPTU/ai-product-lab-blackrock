# 03 — AI Log & Reflection (Bài cá nhân)

> **Họ và tên:** Hoàng Nguyễn Phong
> **MSSV:** 2A202601077
> **Nhóm:** blackrock
> **AI thought-partner đã dùng:** Claude (Claude Code), Gemini

Nhật ký chiêm nghiệm trung thực về việc dùng AI làm trợ lý đồng hành (thought-partner) trong Lab 02.

---

## 1. 🤝 AI đã giúp gì?

- **Brainstorm & cấu trúc bài toán:** Mình dùng AI để đối chiếu 4 Lenses (Lặp lại / Tốn thời gian / AI-upgrade / Stakeholder Pain) với các mảng của Vingroup, từ đó chốt nhanh 5 bài toán trong bảng SCAN và chọn top-3 làm Quick Card ở `01-problem-scan.md`.
- **Chuẩn hóa Quick Problem Card:** AI giúp điền đủ 8 trường của mỗi card (Actor, workflow, bottleneck, bước AI tham gia, metric có số…) đúng format worksheet, và nhắc mình viết metric dạng định lượng (`từ ~4 phút xuống < 30 giây`) thay vì nói chung chung.
- **Phản biện kiến trúc (stress-test):** Mình yêu cầu AI đóng vai CFO/Trưởng phòng Vận hành khắt khe để chỉ ra điểm yếu. Chính nhờ vòng phản biện này mà mình quyết định để **Card #3 (đối soát hóa đơn sạc) dùng Rule thay vì LLM** — đúng tinh thần *"Problem First, AI Second"*.
- **Kỹ năng phụ:** hỏi AI cách kích hoạt `.venv` trên PowerShell và cách nạp `GEMINI_API_KEY` an toàn (không hardcode key vào code).

## 2. ❌ AI đã sai gì?

- **Lỗi định dạng (formatting hallucination):** Khi sinh `01-problem-scan.md`, AI chèn thừa các khối code fence rỗng (` ``` ` đứng một mình) ngay sau mỗi bảng Quick Card. Kết quả là markdownlint báo hàng loạt cảnh báo `MD040/MD031/MD058`, làm file render lỗi và thiếu chuyên nghiệp.
- **Thiên vị "dùng AI cho mọi thứ":** Ở bản nháp đầu, AI có xu hướng gợi ý gắn LLM cho cả bài toán đối soát hóa đơn (vốn là dữ liệu số có luật rõ). Nếu nghe theo thì vừa tốn chi phí, vừa tăng rủi ro sai số — trong khi rule-based làm tốt hơn.
- **Giá trị "ảo" nghe hợp lý nhưng chưa kiểm chứng:** Các con số như *"≥ 90% gán đúng danh mục"* hay *"phát hiện review khẩn < 2 giờ"* là ước lượng AI đề xuất, chưa có baseline thực tế — dễ bị nhầm là dữ liệu thật nếu không cẩn thận.

## 3. 🔧 Mình đã sửa đổi ra sao?

- **Với lỗi format:** Mình yêu cầu AI dọn các code fence rỗng và thêm dòng trắng bao quanh bảng để hết cảnh báo lint; đồng thời tự kiểm tra lại file trên trình xem markdown của VS Code trước khi giữ.
- **Với thiên vị dùng AI:** Mình bổ sung ràng buộc vào prompt — *"Chỉ đề xuất LLM khi đầu vào là ngôn ngữ tự nhiên; nếu dữ liệu có cấu trúc và luật rõ, phải chọn Rule và giải thích vì sao"*. Nhờ đó Card #3 được đổi sang **Rule / State-Machine** kèm lý giải.
- **Với con số chưa kiểm chứng:** Mình đánh dấu rõ đây là *ước lượng cần đo baseline*, và thêm ghi chú tự phản biện ở cuối `01-problem-scan.md` nhắc rằng phải có số liệu người-làm hiện tại thì mới chứng minh được AI cải thiện thật.

---

## 🧭 Bài học rút ra

AI là **thought-partner tốc độ cao** giúp phá vỡ trang giấy trắng và giữ đúng format, nhưng **không phải nguồn sự thật**. Ba nguyên tắc mình giữ sau buổi lab:
1. **Verify trước khi tin** — mọi con số/metric AI đưa ra đều phải gắn cờ "cần baseline".
2. **Ranh giới do mình đặt** — ép AI chọn đúng kiến trúc (Rule vs LLM) bằng ràng buộc trong prompt, không để AI mặc định "AI hoá" mọi thứ.
3. **Human-in-the-loop là bắt buộc** — người vẫn duyệt bước ra quyết định cuối; AI chỉ hỗ trợ.
