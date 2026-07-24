Nhật ký AI

1. AI giúp gì?

Trong buổi Lab hôm nay, em sử dụng Claude làm trợ lý đồng hành xuyên suốt quá trình scoping bài toán AI cho Vin Smart Future. Cụ thể:

Brainstorm bài toán (Phase 1 — SCAN): Em yêu cầu AI liệt kê các bài toán thực tế theo 4 lenses (Lặp lại, Tốn thời gian, AI-upgrade, Pain từ người khác) cho tất cả các công ty thành viên Vingroup. AI đưa ra danh sách 16 bài toán phân loại rõ ràng theo từng lens và từng subsidiary, giúp em tiết kiệm thời gian tìm kiếm ý tưởng và nhanh chóng chọn được 5 bài toán phù hợp nhất (Vinpearl kiểm kê minibar, Vinmec hồ sơ xuất viện, Vinhomes trợ lý cư dân, Vinpearl review OTA, VinFast trạm sạc).

Viết Quick Problem Cards (Phase 2 — QUICK-ASSESS): Sau khi em chọn 3 bài toán, AI giúp điền đầy đủ nội dung từng Quick Card theo đúng format yêu cầu: workflow 5 bước, xác định bottleneck kèm thời gian ước tính, đề xuất bước AI can thiệp, metric có con số cụ thể, và phân loại kiến trúc (LLM Feature / LLM Vision / Agent).

Phản biện thẻ bài toán (Stress-Test): Em sử dụng AI đóng vai CFO và Trưởng phòng Vận hành để phản biện một thẻ bài toán về quản lý tiến độ xây dựng cho Vincons. AI chỉ ra 3 điểm yếu quan trọng: scope quá rộng (gộp 3 bài toán vào 1), metric thiếu con số cụ thể (chỉ viết "giảm rõ" mà không có số liệu), và giải thích vì sao rule-based scheduler + SQL dashboard có thể giải quyết bài toán tốt hơn Agent vì dữ liệu xây dựng đã có cấu trúc sẵn (Gantt chart, milestone, checklist nghiệm thu theo TCVN).

Hỗ trợ viết báo cáo: AI giúp format nội dung theo đúng cấu trúc markdown mà bài lab yêu cầu, tham chiếu file mẫu 02-deliverable-example.md để đảm bảo output đạt chuẩn.

---

2. AI sai gì?

Đề xuất bài toán thiếu thực tế khi chưa có context: Ban đầu khi em chưa cung cấp rõ mảng kinh doanh muốn tập trung, AI đưa ra một số bài toán có phần lý tưởng hóa. Ví dụ bài toán "Nhập liệu thủ công kết quả xét nghiệm từ máy cũ chưa kết nối HIS" cho Vinmec. Trên thực tế, hầu hết bệnh viện Vinmec đã số hóa hệ thống HIS khá hoàn chỉnh, nên bài toán này có thể không còn đúng với tình trạng hiện tại. Đây là dạng hallucination nhẹ — AI giả định một pain point dựa trên kiến thức chung về ngành y tế Việt Nam mà không xác minh được tình trạng thực tế tại Vinmec.

Metric ước tính không có nguồn dẫn chứng: Trong Quick Problem Card, AI viết các con số như "sai lệch 12% đơn hàng minibar mỗi tháng" hay "~200 cuộc gọi/ngày" cho CSKH VinFast. Những con số này nghe hợp lý nhưng hoàn toàn là ước tính do AI tự suy luận, không dựa trên dữ liệu thực tế. Nếu sử dụng trực tiếp trong báo cáo chính thức sẽ gây hiểu lầm.

---

3. Sửa đổi ra sao?

Thu hẹp scope từ đầu: Thay vì yêu cầu AI "liệt kê tất cả bài toán có thể", em đã điều chỉnh bằng cách chỉ định rõ: "Đưa em danh sách các bài toán theo từng lens để em pick". Cách này giúp AI tổ chức output có cấu trúc và em giữ quyền quyết định thay vì để AI chọn hộ.

Yêu cầu phản biện thay vì chỉ sinh nội dung: Khi có một thẻ bài toán chưa chắc chắn (Vincons — quản lý tiến độ xây dựng), em dùng prompt stress-test theo hướng dẫn của worksheet: "Đóng vai CFO khắt khe, chỉ ra 3 điểm yếu và giải thích vì sao rule-based tốt hơn". Kết quả phản biện giúp em nhận ra scope quá rộng và metric thiếu số — điều mà khi tự viết dễ bị bỏ qua.

Ghi nhận rõ các con số là ước tính: Sau khi nhận ra AI tự suy luận metric, em ý thức rằng cần đánh dấu rõ các con số này là "ước tính minh họa" trong báo cáo, hoặc thay bằng dữ liệu thực tế nếu có. Trong tương lai, em sẽ thêm vào prompt: "Chỉ đưa ra con số nếu có nguồn dẫn chứng, nếu không hãy ghi rõ đây là ước tính" để tránh hallucination về số liệu.
