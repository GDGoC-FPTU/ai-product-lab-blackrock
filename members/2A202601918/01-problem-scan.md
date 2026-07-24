# Phase 1 — SCAN: Tìm kiếm cơ hội (Cá nhân)

Sử dụng **4 Lenses** quét qua hoạt động vận hành của các công ty thành viên Vingroup.

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|------------|------|---------------------|
| 1 | **Vinpearl** | Lặp lại | Kiểm kê minibar phòng khách sạn hằng ngày: nhân viên buồng phòng ghi chép thủ công số lượng từng sản phẩm, nhập liệu lên hệ thống PMS để tính phí phòng — quy trình lặp lại 300-500 lượt/ngày tại mỗi resort. |
| 2 | **Vinmec** | Tốn thời gian | Bác sĩ soạn tóm tắt hồ sơ xuất viện (Discharge Summary): trích xuất thông tin từ bệnh án điện tử, kết quả xét nghiệm, ghi chú lâm sàng để viết bản tóm tắt dễ hiểu cho bệnh nhân — mất 20-30 phút/bệnh nhân. |
| 3 | **Vinhomes** | AI có thể tốt hơn | Trợ lý cư dân ảo hỗ trợ thủ tục hành chính: cư dân muốn đăng ký thi công nội thất, gia hạn vé gửi xe, đăng ký thẻ ra vào phải đến quầy ban quản lý nhiều lần vì không nắm rõ quy định và hồ sơ cần thiết. |
| 4 | **Vinpearl** | Pain từ người khác | Quét và phân tích review khách sạn trên OTA (Booking.com, Agoda, Google Maps): Manager không kịp đọc hết hàng trăm review mỗi tuần, bỏ lỡ các phàn nàn khẩn cấp ("phòng bẩn", "mất đồ", "nhân viên thái độ tệ") cần xử lý ngay. |
| 5 | **VinFast** | AI có thể tốt hơn | Trợ lý hướng dẫn trạm sạc thông minh: chủ xe VinFast gọi tổng đài hỏi trạm sạc gần nhất, nhân viên CSKH phải tra cứu thủ công loại cổng sạc phù hợp (CCS2/GBT) theo từng dòng xe (VF5/VF8/VF9) và kiểm tra trạm còn trụ trống — mất 8-10 phút/cuộc gọi. |

---

# Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards (Cá nhân)

Chọn top 3 từ danh sách SCAN: **#5 (VinFast Trạm sạc), #1 (Vinpearl Minibar), #3 (Vinhomes Trợ lý cư dân).**

## Card #1 — VinFast: Trợ lý hướng dẫn trạm sạc thông minh

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Chủ xe VinFast cần tìm trạm sạc trống   │
│ phù hợp loại cổng sạc của xe nhưng nhân viên CSKH phải     │
│ tra cứu thủ công mất 8-10 phút/cuộc gọi.                   │
│ Công ty thành viên: [x] VinFast                             │
│                                                             │
│ Ai đang đau (Actor)? Chủ xe VinFast (chờ đợi lâu) và       │
│ Nhân viên CSKH VinFast (xử lý quá tải ~200 cuộc/ngày).     │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Khách gọi tổng đài hỏi trạm sạc gần vị trí hiện tại  │
│   ──> 2. Nhân viên tra cứu dòng xe để xác định loại cổng   │
│         sạc (CCS2 cho VF8/VF9 hay GBT cho VF5/VFe34)       │
│   ──> 3. Mở dashboard trạm sạc, lọc thủ công trạm có trụ  │
│         trống & đúng loại cổng trong bán kính gần nhất      │
│   ──> 4. Soạn hướng dẫn đường đi chi tiết bằng văn bản     │
│   ──> 5. Gửi tin nhắn/SMS hướng dẫn cho khách hàng         │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 (⏱ 5 phút/lượt)   │
│   Tra cứu thủ công dashboard trạm sạc: phải lọc theo loại  │
│   cổng, kiểm tra trạng thái real-time, đối chiếu khoảng    │
│   cách — dễ sai khi có nhiều cuộc gọi cùng lúc.            │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3-4           │
│   (Auto-match dòng xe → loại cổng sạc → tìm trạm trống    │
│   gần nhất → draft hướng dẫn đường đi)                     │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   "Giảm thời gian xử lý từ 8 phút ──> dưới 1 phút/cuộc    │
│   gọi. Tỉ lệ gợi ý đúng loại cổng sạc đạt 99%."          │
│                                                             │
│ Quick Architecture: [x] LLM Feature                         │
│   (Gọi API trạm sạc + LLM soạn hướng dẫn đường đi)        │
└─────────────────────────────────────────────────────────────┘
```

---

## Card #2 — Vinpearl: Kiểm kê minibar phòng khách sạn bằng AI Vision

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Nhân viên buồng phòng Vinpearl kiểm kê   │
│ minibar thủ công 300-500 phòng/ngày, ghi chép giấy rồi     │
│ nhập liệu hệ thống PMS — tốn thời gian và dễ sai sót.      │
│ Công ty thành viên: [ ] Vinpearl / VinWonders               │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên buồng phòng (Housekeeping)  │
│ — mất nhiều thời gian ghi chép; Bộ phận kế toán — phải đối │
│ chiếu sai lệch số lượng thường xuyên.                       │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Nhân viên mở tủ minibar, đếm từng sản phẩm theo       │
│      danh sách chuẩn (nước, bia, snack, rượu mini...)       │
│   ──> 2. Ghi số lượng thiếu/đã dùng lên phiếu kiểm kê giấy│
│   ──> 3. Mang phiếu về quầy, nhập liệu thủ công vào hệ    │
│         thống quản lý khách sạn (PMS)                        │
│   ──> 4. Kế toán đối chiếu số liệu minibar với hóa đơn     │
│         phòng để tính phí check-out                          │
│   ──> 5. Xử lý sai lệch nếu khách khiếu nại tính phí sai  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2-3 (⏱ 8 phút/phòng)│
│   Ghi chép giấy dễ nhầm số lượng, nhập liệu thủ công gây  │
│   sai lệch ~12% đơn hàng minibar mỗi tháng.                │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 1-2-3           │
│   (Chụp ảnh minibar → AI Vision nhận dạng sản phẩm còn/    │
│   thiếu → Tự động cập nhật PMS)                             │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   "Giảm thời gian kiểm kê từ 8 phút ──> 2 phút/phòng.      │
│   Giảm tỉ lệ sai lệch minibar từ 12% ──> dưới 2%."        │
│                                                             │
│ Quick Architecture: [x] LLM (Vision)                         │
│   (Dùng LLM Vision nhận dạng ảnh chụp minibar)              │
└─────────────────────────────────────────────────────────────┘
```

---

## Card #3 — Vinhomes: Trợ lý cư dân ảo hỗ trợ thủ tục hành chính

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Cư dân Vinhomes muốn đăng ký thi công    │
│ nội thất, gia hạn vé gửi xe, hoặc cấp thẻ ra vào phải đến │
│ quầy ban quản lý 2-3 lần vì không nắm rõ quy định và hồ   │
│ sơ cần thiết.                                                │
│ Công ty thành viên: [x] Vinhomes                             │
│                                                             │
│ Ai đang đau (Actor)? Cư dân (mất thời gian đi lại nhiều    │
│ lần) và Nhân viên ban quản lý tòa nhà (trả lời câu hỏi     │
│ lặp đi lặp lại ~50 lượt/ngày).                              │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Cư dân đến quầy ban quản lý hoặc gọi điện hỏi thủ tục│
│   ──> 2. Nhân viên tra cứu quy định nội bộ (thi công chỉ   │
│         được trong khung giờ nào, cần giấy tờ gì...)        │
│   ──> 3. Nhân viên hướng dẫn miệng danh sách hồ sơ cần     │
│         chuẩn bị                                             │
│   ──> 4. Cư dân về chuẩn bị hồ sơ, thường thiếu 1-2 giấy  │
│         tờ → phải quay lại hỏi thêm lần 2-3                 │
│   ──> 5. Nộp hồ sơ hoàn chỉnh, nhân viên kiểm tra và xử lý│
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2-3-4                │
│   (⏱ 30 phút tổng cộng cho toàn bộ quy trình)              │
│   Nhân viên tra cứu quy định thủ công, hướng dẫn miệng     │
│   thiếu sót khiến cư dân phải quay lại nhiều lần.           │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 1-2-3-4         │
│   (Chatbot tra cứu quy định tự động + tạo checklist hồ sơ  │
│   cá nhân hóa + draft đơn đăng ký sẵn cho cư dân)          │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   "Giảm số lần cư dân phải đến quầy từ 2-3 lần ──> 0 lần  │
│   (tự phục vụ online). Giảm thời gian hoàn tất thủ tục     │
│   từ 30 phút ──> dưới 5 phút."                              │
│                                                             │
│ Quick Architecture: [x] Agent                                │
│   (Agent tra cứu knowledge base quy định + tạo form/đơn)    │
└─────────────────────────────────────────────────────────────┘
```
