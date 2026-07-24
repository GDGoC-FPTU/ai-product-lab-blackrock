# 01 — Problem Scan (Cá nhân)

**Họ và tên:** Phan Hoàng Long
**Vai trò:** AI Product Engineer, Vin Smart Future

---

## 🏛️ Bối cảnh: Tôi là ai?

Tôi là **Long**, AI Engineer mới được điều chuyển về **Vin Smart Future**. Trước buổi thảo luận nhóm, tôi tự khảo sát nhanh (qua tài liệu vận hành công khai, phản ánh của khách hàng trên App/Store review, và trao đổi với vài anh chị vận hành) để tìm ra những điểm nghẽn đang lặp lại, tốn thời gian, hoặc gây khó chịu cho nhân viên/khách hàng tại các công ty thành viên. Danh sách dưới đây là kết quả quét (SCAN) và 3 thẻ bài toán tiềm năng nhất tôi mang vào buổi Lab.

---

# 🔍 Phase 1 — SCAN: Tìm kiếm cơ hội (Cá nhân)

Dùng **4 Lenses** quét qua vận hành của các công ty thành viên Vingroup.

| # | Subsidiary | Lens | Mô tả ngắn |
|---|------------|------|------------|
| 1 | **VinFast** | Lặp lại | So khớp thủ công hàng nghìn giao dịch sạc/tuần với hóa đơn đối tác. |
| 2 | **Xanh SM** | AI-upgrade | Ghi âm cuộc gọi & note tài xế chỉ tổng hợp thủ công cuối tuần, chậm phát hiện lỗi hệ thống. |
| 3 | **Vinhomes** | Lặp lại | Đọc và route thủ công từng khiếu nại (mất nước, hỏng thang máy...) đến đúng ban quản lý. |
| 4 | **Vinmec** | Tốn thời gian | Bác sĩ tự tổng hợp bệnh án + xét nghiệm để soạn discharge summary. |
| 5 | **Vinpearl** | Stakeholder Pain | Quản lý tự đọc hàng trăm review Booking/Agoda/Google Map để bắt phàn nàn khẩn cấp. |
| 6 | **VinFast** | AI-upgrade | Chủ xe tự tra trạm sạc trống + loại cổng phù hợp (CCS2/GB-T) theo từng dòng xe. |

---

# 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards (Cá nhân)

Chọn top 3 từ danh sách SCAN: **#1 (VinFast Đối soát hóa đơn sạc), #3 (Vinhomes Phân loại phản ánh cư dân), #4 (Vinmec Tóm tắt xuất viện).**

## Card #1 — VinFast: Đối chiếu hóa đơn sạc điện đối tác

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: Đối chiếu hàng nghìn giao dịch sạc điện từ trụ    │
│ sạc đối tác bên ngoài với hóa đơn thanh toán hằng tuần.     │
│ Công ty thành viên: [x] VinFast                             │
│                                                             │
│ Ai đang đau? Nhân viên phòng Tài chính - Đối soát           │
│ (Reconciliation Analyst).                                   │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Tải file giao dịch sạc từ hệ thống đối tác (~5-8k giao │
│      dịch/tuần)                                             │
│   → 2. Tải hóa đơn PDF/Excel do đối tác gửi qua email       │
│   → 3. Đối chiếu thủ công từng dòng: mã trụ, thời gian, kWh,│
│        đơn giá                                              │
│   → 4. Đánh dấu & liệt kê các giao dịch lệch số liệu        │
│   → 5. Gửi email xác nhận/khiếu nại lại với đối tác         │
│                                                             │
│ Bước nào tốn nhất? Bước 3 (⏱ 6-8 giờ/tuần/nhân viên)       │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 3-4 (auto-match  │
│ theo mã giao dịch/timestamp, tự flag dòng lệch số liệu)     │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian đối soát từ 8 giờ ──> dưới 1 giờ/tuần;       │
│ tỉ lệ phát hiện sai lệch đạt ≥95% so với đối soát thủ công. │
│                                                             │
│ Quick Architecture: [x] Rule / Script  (LLM chỉ hỗ trợ đọc  │
│ hóa đơn PDF không chuẩn format, không cần Agent)            │
└─────────────────────────────────────────────────────────────┘
```

## Card #2 — Vinhomes: Phân loại & điều hướng phản ánh cư dân

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: Phân loại và chuyển tiếp phản ánh/khiếu nại của   │
│ cư dân gửi qua App Vinhomes Resident đến đúng ban quản lý.  │
│ Công ty thành viên: [x] Vinhomes                            │
│                                                             │
│ Ai đang đau? Nhân viên trực CSKH tòa nhà (Building          │
│ Management Officer) và cư dân chờ phản hồi.                 │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Cư dân gửi phản ánh dạng văn bản tự do qua App         │
│   → 2. Nhân viên CSKH đọc và tự phân loại loại sự cố        │
│        (điện/nước/an ninh/tiếng ồn...)                      │
│   → 3. Chuyển tiếp thủ công đến đúng bộ phận kỹ thuật phụ   │
│        trách tòa nhà đó                                     │
│   → 4. Theo dõi & nhắc bộ phận xử lý nếu quá SLA            │
│                                                             │
│ Bước nào tốn nhất? Bước 2-3 (⏱ 5-7 phút/phản ánh, ~200 phản│
│ ánh/ngày toàn khu)                                          │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3 (tự động     │
│ phân loại loại sự cố + mức khẩn cấp + route đúng bộ phận)   │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian phân loại/chuyển tiếp từ 6 phút ──> dưới     │
│ 30 giây/phản ánh; độ chính xác route đúng bộ phận ≥90%.     │
│                                                             │
│ Quick Architecture: [x] LLM Feature (kèm Rule fallback cho  │
│ các case không rõ ràng)                                     │
└─────────────────────────────────────────────────────────────┘
```

## Card #3 — Vinmec: Soạn thảo tóm tắt hồ sơ xuất viện

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán: Bác sĩ mất nhiều thời gian tổng hợp bệnh án điện  │
│ tử để soạn tóm tắt xuất viện (discharge summary) cho bệnh   │
│ nhân.                                                       │
│ Công ty thành viên: [x] Vinmec                              │
│                                                             │
│ Ai đang đau? Bác sĩ điều trị / Bác sĩ nội trú.              │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Bác sĩ tổng hợp toàn bộ ghi chú điều trị trong hồ sơ   │
│      bệnh án điện tử (EMR)                                  │
│   → 2. Trích xuất kết quả xét nghiệm, chẩn đoán hình ảnh    │
│        liên quan                                            │
│   → 3. Soạn thảo tóm tắt xuất viện bằng ngôn ngữ dễ hiểu    │
│        (chẩn đoán, thuốc, lịch tái khám)                    │
│   → 4. Rà soát lại với Trưởng khoa trước khi in cho bệnh nhân│
│                                                             │
│ Bước nào tốn nhất? Bước 1-3 (⏱ 20-30 phút/bệnh nhân, ~30   │
│ bệnh nhân xuất viện/ngày/khoa)                              │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 1-3 (đọc dữ liệu │
│ EMR có cấu trúc, tự động soạn draft tóm tắt xuất viện)      │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian soạn thảo từ 25 phút ──> dưới 5 phút/bệnh    │
│ nhân (bác sĩ chỉ cần review & chỉnh sửa); vẫn giữ 100% yêu  │
│ cầu bác sĩ ký duyệt trước khi phát hành.                    │
│                                                             │
│ Quick Architecture: [x] LLM Feature (bắt buộc HITL — bác sĩ │
│ duyệt trước khi phát hành cho bệnh nhân)                    │
└─────────────────────────────────────────────────────────────┘
```
