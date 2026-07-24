# 📄 01-problem-scan.md — Problem Scan & Quick Problem Cards (Vin Smart Future)

> **Học viên thực hiện:** Lê Nguyễn Minh Đức  
> **MSHV:** 2A202601013  
> **Đơn vị giả định:** Vin Smart Future (Vingroup)

---

# 🔍 Phase 1 — SCAN: Bảng Quét Cơ Hội AI tại các Công Ty Thành Viên Vingroup

Sử dụng **4 Lenses** (Lặp lại, Tốn thời gian, AI-upgrade, Stakeholder Pain) để tìm kiếm các nút thắt vận hành thực tế:

| # | Subsidiary | Lens | Mô tả ngắn bài toán / Nút thắt vận hành |
|---|------------|------|-----------------------------------------|
| 1 | **Vincons (Vinhomes)** | Tốn thời gian | Quản lý tiến độ và chất lượng xây dựng tùy theo công trình, nhà thầu phụ (subcontractor) và đội thợ để điều phối nhân lực hiệu quả (giám định thủ công mất 3-4 giờ/ngày). |
| 2 | **Vinhomes** | Lặp lại | Phân loại và điều hướng tự động hàng trăm phản ánh/khiếu nại của cư dân từ ứng dụng Vinhomes Resident đến đúng Ban Quản Lý (BQL) tòa nhà (đang xử lý thủ công, trễ SLA 12 tiếng). |
| 3 | **VinFast** | Lặp lại | So khớp và đối chiếu hóa đơn sạc điện hằng tuần từ hàng nghìn trụ sạc liên kết của đối tác ngoài với dữ liệu sạc ghi nhận từ hệ thống VinFast. |
| 4 | **Vinmec** | Pain từ người khác | Bác sĩ mất quá nhiều thời gian viết tóm tắt hồ sơ xuất viện (Discharge Summary) từ các kết quả xét nghiệm và bệnh án điện tử (mất 20-30 phút/bệnh nhân, gây quá tải giờ cao điểm). |
| 5 | **Vinpearl / VinWonders** | AI-upgrade | Quét và trích xuất tự động các phản hồi tiêu cực (1-2 sao) của khách hàng trên Agoda/Booking/Google Maps để gắn thẻ độ khẩn cấp và cảnh báo tức thời cho General Manager. |

---

# 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards

Chọn top 3 bài toán từ danh sách trên để lập thẻ đánh giá nhanh:

---

## 📋 QUICK PROBLEM CARD #1 — Vincons: Quản lý tiến độ & điều phối nhân lực công trình

```text
┌─────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                                   │
│                                                                         │
│ Bài toán: Quản lý tiến độ và chất lượng xây dựng tùy theo công trình,   │
│ nhà thầu phụ (subcontractor) và đội thợ để điều phối nhân lực hiệu quả. │
│ Công ty thành viên: [x] Vincons / Vinhomes                              │
│                                                                         │
│ Ai đang đau (Actor)? Nhà thầu chính / Chỉ huy trưởng công trình         │
│                                                                         │
│ Workflow thủ công hiện tại (4 bước):                                    │
│   1. Quản đốc và chủ thầu báo cáo tại chỗ                               │
│   ──> 2. Chủ thầu giám định tiến độ / chất lượng thực địa               │
│   ──> 3. Điều phối tài nguyên và nhân lực đội thợ                       │
│   ──> 4. Đánh giá sau hoàn thiện và tổng kết nhật ký công trình         │
│                                                                         │
│ Bước nào tốn thời gian / dễ lỗi nhất?                                   │
│ - Bước 2 (Giám định tiến độ & chất lượng thực địa): ⏱ 180-240 phút/ngày │
│                                                                         │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                                   │
│ - Quản lý tiến độ và chu kỳ thi công, tự động tổng hợp nhật ký công     │
│   trình và điều phối nhân sự tối ưu cho từng hạng mục công trình.       │
│                                                                         │
│ Đo thành công bằng gì (Metric có số)?                                   │
│ - Rút ngắn thời gian giám định tiến độ từ 4 giờ/ngày ──> dưới 30 phút.   │
│ - Giảm 30% tỷ lệ trễ tiến độ thi công so với các dự án chưa thí điểm.   │
│                                                                         │
│ Quick Architecture: [x] Agent (Agentic Loop điều phối thi công)          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📋 QUICK PROBLEM CARD #2 — Vinhomes: Phân loại & điều hướng khiếu nại cư dân

```text
┌─────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                                   │
│                                                                         │
│ Bài toán: Tự động phân loại, trích xuất độ ưu tiên và điều hướng các    │
│ khiếu nại/phản ánh của cư dân gửi qua ứng dụng Vinhomes Resident.       │
│ Công ty thành viên: [x] Vinhomes                                        │
│                                                                         │
│ Ai đang đau (Actor)?                                                    │
│ - Cư dân đô thị Vinhomes (chờ đợi phản hồi lâu, thái độ bức xúc).       │
│ - Nhân viên CSKH / BQL Tòa nhà (mất thời gian đọc và chuyển tiếp thủ công).│
│                                                                         │
│ Workflow thủ công hiện tại (4 bước):                                    │
│   1. Cư dân gửi phản ánh bằng văn bản/hình ảnh lên App Vinhomes Resident │
│   ──> 2. Nhân viên CSKH tổng đọc nội dung, phân loại loại hình sự cố   │
│   ──> 3. Chọn thủ công Ban Quản Lý (Kỹ thuật/Vệ sinh/An ninh) từng tòa  │
│   ──> 4. Tạo ticket công việc và gửi thông báo cho đội xử lý thực địa   │
│                                                                         │
│ Bước nào tốn thời gian / dễ lỗi nhất?                                   │
│ - Bước 2 & 3 (Đọc phản ánh tự do & phân loại thủ công): ⏱ 15-20 min/ticket │
│                                                                         │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                                   │
│ - AI phân tích ngữ nghĩa văn bản ──> Phân loại nhóm sự cố ──> Trích xuất│
│   độ khẩn cấp (Emergency Tag) ──> Draft ticket đề xuất cho CSKH click duyệt.│
│                                                                         │
│ Đo thành công bằng gì (Metric có số)?                                   │
│ - Giảm thời gian phân loại và chuyển giao ticket từ 12 giờ ──> dưới 15 phút.│
│ - Tỷ lệ phân loại đúng BQL chuyên trách đạt > 92%.                      │
│                                                                         │
│ Quick Architecture: [x] LLM Feature (Text Classification & Extraction)  │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 📋 QUICK PROBLEM CARD #3 — Vinmec: Tự động tóm tắt hồ sơ xuất viện (Discharge Summary)

```text
┌─────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                                   │
│                                                                         │
│ Bài toán: Trích xuất thông tin lâm sàng từ hồ sơ bệnh án điện tử (EMR)  │
│ để tự động draft bản tóm tắt hồ sơ xuất viện bằng ngôn ngữ dễ hiểu.     │
│ Công ty thành viên: [x] Vinmec                                          │
│                                                                         │
│ Ai đang đau (Actor)?                                                    │
│ - Bác sĩ điều trị (quá tải hành chính, tốn 20-30 phút/bệnh nhân).       │
│ - Bệnh nhân xuất viện (nhận tờ tóm tắt chậm, thuật ngữ y khoa khó hiểu).│
│                                                                         │
│ Workflow thủ công hiện tại (4 bước):                                    │
│   1. Bác sĩ mở hệ thống EMR đọc lại lịch sử điều trị, kết quả xét nghiệm│
│   ──> 2. Gõ thủ công văn bản tóm tắt quá trình bệnh lý và hướng dẫn thuốc│
│   ──> 3. Dịch các thuật ngữ chuyên môn sang hướng dẫn chăm sóc tại nhà  │
│   ──> 4. In ấn, ký tên và bàn giao cho bệnh nhân xuất viện              │
│                                                                         │
│ Bước nào tốn thời gian / dễ lỗi nhất?                                   │
│ - Bước 1 & 2 (Đọc gom dữ liệu EMR & viết bản tóm tắt): ⏱ 25 phút/lượt   │
│                                                                         │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                                   │
│ - AI trích xuất thông tin từ EMR ──> Tự động Draft bản tóm tắt xuất viện│
│   dễ hiểu ──> Bác sĩ kiểm tra, chỉnh sửa nhẹ và duyệt (Bắt buộc HITL).   │
│                                                                         │
│ Đo thành công bằng gì (Metric có số)?                                   │
│ - Giảm thời gian bác sĩ soạn tóm tắt từ 25 phút ──> dưới 5 phút/bệnh nhân.│
│ - 100% bản tóm tắt phải được bác sĩ phê duyệt trước khi phát hành.      │
│                                                                         │
│ Quick Architecture: [x] LLM Feature (Summarization with strict HITL)    │
└─────────────────────────────────────────────────────────────────────────┘
```
