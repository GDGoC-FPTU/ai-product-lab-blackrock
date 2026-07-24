# Lab 02 — Worksheet: AI Product Scoping (Vin Smart Future)


# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | Xanh SM | Tốn thời gian | Tổng hợp hóa thông tin phản ánh về điều kiện xe từ tài xế trước khi quyết định bảo trì hoặc sửa chữa (ví dụ - pin hiệu suất thấp, cảm giác lái không tốt, tuổi thọ pin, độ bền của giảm xóc)| 
| 2 | Vinhomes | Lặp lại | Tự động hóa các hoạt động đặt chỗ, thanh toán dịch vụ/phí thuế, các thao tác hủy/báo lỗi của cư dân (v.d. hủy lịch đặt sân tập, hoàn tiền vé bơi, vv.) |
| 3 | Vincons | Tốn thời gian | Đánh giá tiến độ thi công và chất lượng thi công của các đội công nhân và các nhà thầu, nhằm điều phối thời gian và nhân lực hợp lý và giảm thiểu chi phí |
| 4 | Vinmec | Stakeholder pain | Bệnh nhân phản ánh về việc chờ khám tốn thời gian quá lâu / không thể đặt lịch khám do bác sĩ dành thời gian quá lâu đối với từng bệnh nhân / phân công tại phòng khám bệnh viện chênh lệch |
| 5 | Vincons | Lặp lại | Xuất hóa đơn và phân loại chi phí dựa trên hạng mục chi tiêu, linh kiện và vật liệu để phục vụ hoạt động quyết toán |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                     │
│                                                             │
│ Bài toán (1 câu): Quản lý tiến độ và chất lượng xây dựng tùy theo công trình, subcontractor và đội thợ để điều phối nhân lực hiệu quả  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [X] Khác (Ghi rõ) Vincons  │
│                                                             │
│ Ai đang đau (Actor)? Nhà thầu chính                          │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Quản đốc và chủ thầu báo cáo tại chỗ ──> 2. Chủ thầu giám định tiến độ/chất lượng ──> 3. Điều phối tài nguyên và nhân lực ──> 4. Đánh giá sau hoàn thiện                   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Giám định tiến độ (⏱ N phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Quản lý tiến độ và chu kỳ thi công, quản lý nhân sự trong công trình │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Tiến độ thi công giảm rõ so với các dự án chưa thí điểm: thời gian thi công giảm 20-30%, chi phí thi công giảm 10%, etc.                                         │
│   VD: "Giảm thời gian soạn phản hồi từ 10 min ──> under 2 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [X] Agent │
└─────────────────────────────────────────────────────────────┘
```

> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*

1. Metric vô nghĩa — không đo lường được, không quy trách nhiệm được

"Tiến độ thi công giảm rõ so với các dự án chưa thí điểm" là một câu định tính, không phải metric. Nó thiếu: baseline (giảm so với con số nào?), đơn vị đo (ngày, %, giờ công?), và cơ chế kiểm soát biến nhiễu (thời tiết, giá vật liệu, tay nghề đội thợ khác nhau giữa công trình thí điểm và đối chứng — làm sao tách được phần cải thiện do AI mang lại?). Không có con số baseline, tôi không thể duyệt ngân sách cho dự án này vì không ai chứng minh được ROI, và cũng không ai chịu trách nhiệm nếu nó thất bại. So sánh với ví dụ mẫu trong card ("10 min → dưới 2 min") — đó là metric tốt vì có baseline, đơn vị, và ngưỡng rõ ràng. Card này chưa đạt chuẩn đó.

2. Nhảy thẳng vào "Agent" trong khi vấn đề gốc chưa được định nghĩa rõ

Bước tốn thời gian nhất được xác định là "Giám định tiến độ" nhưng lại ghi "⏱ N phút/lượt" — N là biến chưa điền, nghĩa là ta chưa đo được vấn đề trước khi chọn giải pháp. Chọn kiến trúc "Agent" (mức phức tạp và chi phí vận hành cao nhất trong 4 lựa chọn) mà chưa định lượng được cơn đau là đặt cược ngân sách dựa trên cảm tính. Đây là lỗi kinh điển: chọn công nghệ trước, định nghĩa bài toán sau.

3. Vì sao rule-based / code thông thường có thể giải quyết tốt hơn

Nhìn kỹ workflow: đây bản chất là bài toán quản lý tiến độ dự án (project scheduling, resource allocation) — một lĩnh vực đã có giải pháp toán học chín muồi (CPM, PERT, thuật toán tối ưu phân bổ nguồn lực) chạy trong các hệ ERP xây dựng (Procore, Primavera P6, MS Project) từ hàng chục năm nay. Ba lý do cụ thể:

Tính xác định và kiểm toán được: Tiến độ/chất lượng thi công liên quan đến an toàn công trình và nghiệm thu pháp lý. Một hệ rule-based cho ra kết quả có thể truy vết (nếu X ngày trễ và Y nhân công thiếu thì cảnh báo Z) — kiểm toán viên và cơ quan quản lý xây dựng có thể verify logic. Một Agent dùng LLM để "quản lý tiến độ và nhân sự" tạo ra output không xác định (non-deterministic), khó giải trình khi có sự cố hoặc tranh chấp hợp đồng với subcontractor.
Chi phí vận hành: Agent (gọi LLM lặp lại, có bộ nhớ, ra quyết định đa bước) tốn chi phí inference và độ trễ cao hơn nhiều so với một hệ thống rule + dashboard đơn giản đọc dữ liệu từ báo cáo hiện trường (nhập liệu qua app/checklist) rồi tự động tính lại lịch trình bằng thuật toán tối ưu. Với quy mô nhiều công trình của Vincons, chênh lệch chi phí này rất lớn.
Vấn đề thực chất nằm ở dữ liệu đầu vào, không phải ở suy luận: Cơn đau thật sự là "quản đốc báo cáo tại chỗ" chậm và thiếu chuẩn hóa — đây là bài toán thu thập dữ liệu (data capture: ảnh, checklist số hóa, IoT sensor) chứ không phải bài toán cần AI suy luận phức tạp. Giải quyết khâu nhập liệu bằng app + rule engine sẽ mang lại 80% giá trị với 20% chi phí và rủi ro so với việc dùng Agent.

Đề xuất: hạ kiến trúc xuống "Rule" hoặc "LLM" (chỉ dùng LLM cho phần xử lý ngôn ngữ tự nhiên, ví dụ trích xuất thông tin từ báo cáo viết tay/giọng nói của quản đốc), giữ phần tính toán lịch trình và cảnh báo bằng logic rule-based, và bắt buộc điền số N cụ thể trước khi trình phê duyệt ngân sách.

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                     │
│                                                             │
│ Bài toán (1 câu): Tổng hợp và phân loại phản ánh của tài xế về tình trạng xe (pin, giảm xóc, cảm giác lái) để ra quyết định bảo trì kịp thời │
│ Công ty thành viên: [ ] VinFast  [X] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ) ______  │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên điều phối bảo trì đội xe (fleet maintenance coordinator) │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Tài xế gửi phản ánh qua app/hotline/nhóm chat, không chuẩn hóa ──> 2. Điều phối viên đọc thủ công từng phản ánh ──> 3. Phân loại mức độ ưu tiên (khẩn cấp/theo dõi) ──> 4. Đối chiếu lịch sử bảo trì trên hệ thống ──> 5. Lên lịch đưa xe vào xưởng │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2-3, đọc và phân loại phản ánh dạng văn bản tự do (⏱ 4 phút/phản ánh, ~150 phản ánh/ngày toàn hệ thống), dễ bỏ sót phản ánh khẩn cấp lẫn trong phản ánh vụn vặt │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3: trích xuất loại lỗi + mức độ nghiêm trọng từ văn bản tự do và gợi ý ưu tiên, điều phối viên vẫn duyệt quyết định cuối │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Giảm thời gian phân loại 1 phản ánh từ 4 phút ──> dưới 30 giây; giảm tỷ lệ bỏ sót phản ánh khẩn cấp từ ~8%/tháng xuống dưới 2%/tháng (đo qua số ca xe hỏng đột xuất không có cảnh báo trước) │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                     │
│                                                             │
│ Bài toán (1 câu): Bệnh nhân chờ khám lâu và khó đặt lịch do thời gian khám không được ước lượng đúng khi xếp lịch cho từng bác sĩ │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [X] Vinmec   [ ] Khác (Ghi rõ) ______  │
│                                                             │
│ Ai đang đau (Actor)? Bệnh nhân ngoại trú và nhân viên lễ tân/điều phối phòng khám │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Bệnh nhân gọi hotline/đến trực tiếp đặt lịch ──> 2. Lễ tân tra cứu thủ công lịch trống từng bác sĩ ──> 3. Xếp lịch theo kinh nghiệm cá nhân, không tính thời gian khám thực tế theo loại bệnh ──> 4. Bệnh nhân đến khám và chờ theo thứ tự, không có cảnh báo trễ giờ │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3, xếp lịch không dựa trên thời gian khám trung bình thực tế, gây dồn toa ~25% số slot; thời gian chờ trung bình hiện tại ⏱ 45 phút/lượt khám │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 3: dự đoán thời gian khám dựa trên dữ liệu lịch sử (loại bệnh, bác sĩ) để xếp lịch động và cảnh báo sớm cho bệnh nhân khi dự kiến trễ giờ │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Giảm thời gian chờ trung bình từ 45 phút ──> dưới 20 phút/lượt khám; tăng tỷ lệ lịch khám đúng giờ (lệch dưới 10 phút) từ ~55% lên trên 80% │
│                                                             │
│ Quick Architecture: [ ] No AI  [X] Rule  [ ] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

Ghi chú kiến trúc: Card #2 dùng **LLM** vì cốt lõi là trích xuất/phân loại từ văn bản tự do (NLU) — không cần trạng thái đa bước của Agent. Card #3 dùng **Rule** vì dự đoán thời gian khám và xếp lịch là bài toán thống kê/tối ưu có thể kiểm toán được, tương tự bài học rút ra từ phản biện ở Card #1 — không nên mặc định chọn kiến trúc phức tạp khi chưa cần suy luận ngôn ngữ.