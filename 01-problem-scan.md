# 01 — Problem Scan (Bài cá nhân)

> **Họ và tên:** Hoàng Nguyễn Phong
> **MSSV:** 2A202601077
> **Nhóm:** blackrock
> **Vai trò:** AI Product Engineer @ Vin Smart Future

Tài liệu này hoàn thiện **Phase 1 — SCAN** và **Phase 2 — QUICK-ASSESS** trong `01-worksheet.md`.

---

## 🔍 Phase 1 — SCAN: Bảng quét cơ hội (5 bài toán)

Sử dụng **4 Lenses**: `Lặp lại` · `Tốn thời gian` · `AI-upgrade (AI có thể tốt hơn)` · `Stakeholder Pain (Pain từ người khác)`.

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|------------|------|---------------------|
| 1 | **Vinhomes** | Lặp lại | Ban quản lý tòa nhà mỗi ngày phải đọc thủ công hàng trăm phản ánh cư dân gửi qua app (mất nước, hỏng đèn, ồn ào, rác thải…) rồi phân loại và điều hướng đến đúng bộ phận. Việc phân loại lặp đi lặp lại, dễ nhầm và làm chậm thời gian xử lý. |
| 2 | **Vinpearl** | AI-upgrade | Quản lý hiệu quả tài nguyên vận hành (điện, nước, HVAC/điều hòa) tại khu nghỉ dưỡng. Hiện đội kỹ thuật theo dõi đồng hồ/BMS thủ công, điều chỉnh điều hòa & chiếu sáng theo kinh nghiệm, gây lãng phí năng lượng ở khu vực/khung giờ ít khách. |
| 3 | **VinFast** | Lặp lại | Đội tài chính đối chiếu (reconcile) hóa đơn sạc điện hằng tuần từ hàng nghìn trụ sạc đối tác với dữ liệu log hệ thống. Thao tác so khớp số kWh/số tiền theo từng trạm rất lặp lại và tốn giờ công. |
| 4 | **Xanh SM** | Stakeholder Pain | Khi khách hủy chuyến, tổng đài + tài xế ghi chú lý do rời rạc (voice note, text). Không ai tổng hợp được đâu là 10 nguyên nhân chính gây rò rỉ cuốc, nên đội vận hành không biết ưu tiên khắc phục gì. |
| 5 | **Vinmec** | Tốn thời gian | Bác sĩ mất nhiều thời gian soạn bản tóm tắt hồ sơ xuất viện (Discharge Summary) từ bệnh án điện tử + kết quả xét nghiệm, đồng thời phải diễn đạt lại bằng ngôn ngữ dễ hiểu cho bệnh nhân. |

**Nhận xét chọn lọc:** Bài toán **#1 (Vinhomes)**, **#2 (Vinpearl)** và **#3 (VinFast)** là 3 ứng viên mạnh nhất để làm Quick Card — vì (a) khối lượng lặp lại/tốn giờ hoặc lãng phí rõ ràng, (b) mỗi bài đại diện cho một loại kiến trúc khác nhau (LLM văn bản / Agent dự báo trên dữ liệu IoT / Rule số liệu), và (c) rủi ro khi AI sai ở mức kiểm soát được qua HITL. Bài #5 (Vinmec) tuy giá trị cao nhưng thuộc mảng y tế nhạy cảm, ranh giới an toàn phức tạp nên tạm để lại.

---

## 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards

### 🟩 QUICK PROBLEM CARD #1

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1 — Phân loại & điều hướng phản ánh cư dân │
└─────────────────────────────────────────────────────────────┘
```

| Trường | Nội dung |
|---|---|
| **Bài toán (1 câu)** | Tự động phân loại và điều hướng phản ánh cư dân gửi qua App Vinhomes Resident đến đúng ban quản lý phụ trách. |
| **Công ty thành viên** | ☑ Vinhomes |
| **Ai đang đau (Actor)?** | Nhân viên trực app / điều phối viên Ban quản lý tòa nhà. |
| **Workflow thủ công hiện tại** | 1. Cư dân gửi phản ánh (text/ảnh) ──> 2. NV đọc & hiểu nội dung ──> 3. Gán nhãn danh mục (điện/nước/an ninh/vệ sinh…) ──> 4. Chuyển đến bộ phận đúng ──> 5. Theo dõi phản hồi. |
| **Bước tốn thời gian/lỗi nhất** | Bước 2–3 (đọc + phân loại thủ công), ⏱ ~3–5 phút/phản ánh, dễ gán sai danh mục giờ cao điểm. |
| **AI nhảy vào ở bước nào?** | Bước 3: LLM đọc nội dung phản ánh → gợi ý danh mục + mức độ ưu tiên + bộ phận đích. |
| **Metric thành công (có số)** | Giảm thời gian phân loại từ ~4 phút xuống **< 30 giây/phản ánh**; đạt **≥ 90%** phản ánh gán đúng danh mục ngay lần đầu. |
| **Quick Architecture** | ☑ LLM (phân loại văn bản tiếng Việt + trích ý) — có thể kèm 1 lớp rule cho từ khóa khẩn cấp. |
```
```

---

### 🟩 QUICK PROBLEM CARD #2

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2 — Quản lý hiệu quả tài nguyên vận hành   │
└─────────────────────────────────────────────────────────────┘
```

| Trường | Nội dung |
|---|---|
| **Bài toán (1 câu)** | Tối ưu tiêu thụ điện, nước và HVAC (điều hòa) tại khu nghỉ dưỡng Vinpearl bằng dự báo nhu cầu theo công suất phòng + thời tiết và tự động đề xuất setpoint tiết kiệm. |
| **Công ty thành viên** | ☑ Vinpearl (Khác — Du lịch/Nghỉ dưỡng) |
| **Ai đang đau (Actor)?** | Kỹ sư vận hành cơ điện (Facility / Engineering Manager) tại từng cơ sở. |
| **Workflow thủ công hiện tại** | 1. Đọc đồng hồ điện/nước & màn hình BMS ──> 2. Phát hiện bất thường bằng mắt ──> 3. Chỉnh HVAC/chiếu sáng theo kinh nghiệm ──> 4. Ghi log tiêu thụ ──> 5. Báo cáo cuối tháng. |
| **Bước tốn thời gian/lỗi nhất** | Bước 2–3 (giám sát thủ công, phản ứng chậm sau khi đã lãng phí), ⏱ ~60 phút/ngày; điều hòa chạy dư ở khu ít khách, rò rỉ nước phát hiện trễ nhiều ngày. |
| **AI nhảy vào ở bước nào?** | Bước 2–3: mô hình dự báo nhu cầu theo occupancy + thời tiết, phát hiện bất thường (leak/tiêu thụ vượt ngưỡng) và đề xuất/điều khiển setpoint HVAC — có Human duyệt trước khi áp. |
| **Metric thành công (có số)** | Giảm **10–15%** điện năng & **≥ 8%** nước tiêu thụ; phát hiện rò rỉ/bất thường từ *vài ngày xuống < 1 giờ*. |
| **Quick Architecture** | ☑ Agent (vòng lặp tối ưu: dự báo → đề xuất setpoint → HITL duyệt) trên nền dữ liệu IoT/time-series + rule ngưỡng cảnh báo. **Không phải bài toán LLM.** |
```
```

---

### 🟩 QUICK PROBLEM CARD #3

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3 — Đối chiếu hóa đơn sạc điện đối tác     │
└─────────────────────────────────────────────────────────────┘
```

| Trường | Nội dung |
|---|---|
| **Bài toán (1 câu)** | Tự động so khớp dữ liệu sạc điện hằng tuần từ hàng nghìn trụ sạc đối tác với hóa đơn thực nhận về hệ thống tài chính VinFast. |
| **Công ty thành viên** | ☑ VinFast |
| **Ai đang đau (Actor)?** | Chuyên viên kế toán/đối soát (Finance Reconciliation Officer). |
| **Workflow thủ công hiện tại** | 1. Nhận file log sạc ──> 2. Nhận hóa đơn đối tác ──> 3. So khớp kWh & số tiền theo từng trạm ──> 4. Đánh dấu sai lệch ──> 5. Gửi lại đối tác xử lý. |
| **Bước tốn thời gian/lỗi nhất** | Bước 3 (so khớp thủ công trên Excel), ⏱ ~2–3 phút/trạm × hàng nghìn trạm, dễ bỏ sót sai lệch nhỏ. |
| **AI nhảy vào ở bước nào?** | Bước 3–4: tự động join dữ liệu, phát hiện & phân loại sai lệch; LLM chỉ hỗ trợ diễn giải nguyên nhân bất thường. |
| **Metric thành công (có số)** | Giảm thời gian đối soát **≥ 80%** (từ vài ngày xuống vài giờ); phát hiện **100%** sai lệch vượt ngưỡng cấu hình. |
| **Quick Architecture** | ☑ Rule / State-Machine (bài toán số liệu có luật rõ) — **không cần LLM** cho phần lõi. Đây là ví dụ *"Problem First, AI Second"*: rule-based giải quyết tốt hơn. |
```
```

---

## 🧠 Ghi chú tự phản biện (CFO / Trưởng phòng Vận hành)

- **Card #1** dùng **LLM** hợp lý vì đầu vào là ngôn ngữ tự nhiên đa dạng, rule cứng khó bao phủ. Cần metric baseline (độ chính xác phân loại của người hiện tại) để chứng minh AI cải thiện thật.
- **Card #2** dùng **Agent/ML dự báo** trên dữ liệu IoT time-series (điện/nước/HVAC), **không phải LLM** — vì đầu vào là số cảm biến, không phải văn bản. Rủi ro chính là mô hình đề xuất setpoint sai gây khó chịu cho khách, nên bắt buộc **HITL** duyệt trước khi điều khiển.
- **Card #3** cố tình chọn **Rule** thay vì AI: dữ liệu là số có cấu trúc, luật đối soát rõ ràng → dùng LLM là dư thừa và rủi ro sai số. Đây là điểm cộng thể hiện tư duy *chọn đúng kiến trúc*.
- Bộ 3 card phủ đủ 3 mức AI-Fit (**LLM / Agent / Rule**) và đều cần **Human-in-the-loop** ở bước ra quyết định cuối (chuyển bộ phận / áp setpoint / gửi đối tác) để tránh AI/hệ thống hành động sai.