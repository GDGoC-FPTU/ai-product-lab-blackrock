# 📄 02-deep-dive-report.md — Problem Deep-Dive Report (Vin Smart Future)

> **Thông tin nhóm thực hiện:**
> * **Trưởng nhóm:** Lê Nguyễn Minh Đức — **MSHV:** 2A202601013
> * **Thành viên:** Lục Minh Đức — **MSHV:** 2A202601918
> * **Thành viên:** Phan Hoàng Long — **MSHV:** 2A202601565
> * **Thành viên:** Đặng Thái Nam Sơn — **MSHV:** 2A202601431
> * **Thành viên:** Hoàng Nguyễn Phong — **MSHV:** 2A202601077
> * **Thành viên:** Hà Ngọc Minh — **MSHV:** 2A202602028
> * **Mảng kinh doanh lựa chọn:** Vincons / Vinhomes — Quản lý tiến độ & điều phối thi công xây dựng

---

## 🏛️ 1. Bối cảnh & Quyết định lựa chọn bài toán

Nhóm chúng tôi đóng vai trò là **AI Product Engineer** tại **Vin Smart Future**, phối hợp với Khối Quản lý Thi công của **Vincons / Vinhomes**. 

Trong các dự án khu đô thị đại quy mô của Vinhomes, các Chỉ huy trưởng và Nhà thầu chính gặp áp lực rất lớn trong việc theo dõi tiến độ thi công thực địa từ hàng chục nhà thầu phụ (subcontractors) và hàng trăm đội thợ. Việc giám định tiến độ thủ công bằng sổ sách và báo cáo ảnh gây trễ hạn phát hiện chậm tiến độ, rò rỉ chi phí và phân bổ nhân lực không tối ưu.

* **Bài toán chọn Deep-Dive:** **Quản lý tiến độ và chất lượng xây dựng tùy theo công trình, subcontractor và đội thợ để điều phối nhân lực hiệu quả (Vincons).**
* **Lý do chọn:** Bài toán cốt lõi ảnh hưởng trực tiếp đến chu kỳ bàn giao dự án Vinhomes và ngân sách hàng trăm tỷ đồng. Ứng dụng AI Agentic Loop giúp tự động hóa việc tổng hợp nhật ký công trình, phát hiện sớm nguy cơ trễ tiến độ và gợi ý điều phối nhân sự giữa các đội thợ.

---

## 🏗️ 2. Problem Statement (6-field) — Vin Smart Future Standard

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Nhà thầu chính / Chỉ huy trưởng công trình Vincons. |
| **2. Current Workflow** | 1. Quản đốc và chủ thầu gửi báo cáo tiến độ/hình ảnh thực địa hằng ngày.<br>2. Chỉ huy trưởng giám định trực tiếp tiến độ & chất lượng.<br>3. Điều phối thủ công tài nguyên và nhân lực đội thợ giữa các nhà thầu phụ.<br>4. Tổng kết đánh giá nhật ký công trình sau hoàn thiện. 4 bước thủ công tốn tổng cộng 4-5 giờ/ngày, trong đó Bước 2 chiếm phần lớn thời gian (xem Bottleneck). |
| **3. Bottleneck** | **Bước 2 (Giám định tiến độ & chất lượng thực địa - ⏱ 180-240 phút/ngày):** Kiểm tra thủ công từng hạng mục thi công đối chiếu với bản vẽ/kế hoạch baseline, dễ bỏ sót lỗi kỹ thuật và chậm phát hiện nguy cơ vỡ tiến độ. |
| **4. Business Impact** | Mỗi ngày trễ tiến độ thi công tại các đại dự án Vincons gây thiệt hại hàng trăm triệu đồng chi phí quản lý công trình, chậm chu kỳ mở bán/bàn giao căn hộ Vinhomes và lãng phí 25% hiệu suất nhân lực đội thợ. |
| **5. Success Metric** | 1. Rút ngắn thời gian giám định tiến độ từ 4 giờ/ngày xuống dưới 30 phút/ngày (Efficiency).<br>2. Giảm 30% tỷ lệ trễ tiến độ thi công so với các dự án chưa thí điểm (Quality & Speed). |
| **6. Operational Boundary** | AI Agent được phép trích xuất nhật ký công trình, ảnh thực địa, phân tích mức độ hoàn thành và đưa ra đề xuất điều phối nhân lực (dạng Draft Plan).<br>**CẤM:** AI không được tự ý thay đổi hợp đồng với subcontractor, không được tự động phát lệnh phạt hay điều chuyển nhân sự khi chưa có sự phê duyệt chính thức bằng chữ ký số của Chỉ huy trưởng (Bắt buộc HITL). |

---

## 🔄 3. Future-State Flow & AI Fit Analysis

### 🎯 Phân tích AI-Fit Matrix:
* **Quyết định:** Chọn **Agentic Loop (AI Agent)**.
* **Lý do:** Bài toán yêu cầu theo dõi đa yếu tố (công trình, subcontractor, loại thợ, tiến độ thực tế vs kế hoạch), liên tục đánh giá chu kỳ và đưa ra các đề xuất điều phối tối ưu đa mục tiêu.

### 📐 Quy trình vận hành tương lai (Future-State Workflow):

```text
┌────────────────┐     ┌────────────────┐     ┌────────────────┐     ┌────────────────┐
│ Bước 1         │     │ Bước 2         │     │ Bước 3         │     │ Bước 4         │
│ Quản đốc tải   │ ──> │ 🔵 AI Agent    │ ──> │ 🔵 AI Agent    │ ──> │ 🟢 Chỉ huy     │
│ báo cáo/ảnh    │     │ Phân tích tiến │     │ Draft Kế hoạch │     │ trưởng duyệt   │
│ thực địa lên   │     │ độ vs Baseline │     │ Điều phối thợ  │     │ & phát lệnh    │
└────────────────┘     └────────────────┘     └────────────────┘     └────────────────┘
                                                       │                      │
                                                       ▼                      ▼
                                              ┌────────────────┐     ┌────────────────┐
                                              │ 🔒 Guardrail   │     │ ↩️ Fallback     │
                                              │ Cấm phạt tự động│     │ Nếu AI lỗi,    │
                                              │ bắt buộc HITL  │     │ Chỉ huy trưởng │
                                              └────────────────┘     │ điều phối tay  │
                                                                     └────────────────┘
```

* 🔵 **AI Step:** AI Agent tự động đọc báo cáo/hình ảnh, tính % tiến độ, cảnh báo hạng mục có nguy cơ trễ và lập bản nháp kế hoạch điều phối đội thợ.
* 🟢 **Human Step (HITL):** Chỉ huy trưởng xem bản đồ tiến độ AI đề xuất, điều chỉnh nếu cần và bấm "Phê duyệt điều phối".
* ↩️ **Fallback:** Nếu hệ thống thiếu dữ liệu báo cáo hoặc AI không đủ độ tin cậy (<85%), Chỉ huy trưởng kiểm tra trực tiếp thực địa theo quy trình cũ.

---

## 💻 4. Ranh giới an toàn kỹ thuật (Operational Boundary Guardrails)

Trong file mã nguồn prototype `prompt_prototype.py`, nhóm thiết lập 2 quy tắc bảo vệ nghiêm ngặt:

1. **Quy tắc 1 (Human-in-the-Loop Tag):** Mọi đề xuất điều phối nhân lực và tiến độ của AI phải luôn bắt đầu bằng thẻ `[DRAFT_ONLY]` để tránh hệ thống tự động phát lệnh thi công khi chưa được Chỉ huy trưởng duyệt.
2. **Quy tắc 2 (Safety & Delay Threshold Boundary):** Nếu hạng mục công trình phát hiện chậm tiến độ nghiêm trọng (> 15% so với kế hoạch baseline) hoặc có cảnh báo an toàn lao động, AI Agent không được tự ý quyết định bổ sung thợ tăng ca đêm mà phải trả về JSON kích hoạt cảnh báo khẩn cấp: `{"action": "trigger_emergency_inspection", "reason": "<lý do>"}`.

---

## 🏁 5. Đánh giá độ sẵn sàng & Quyết định dự án (EVALUATE)

### 📋 AI Readiness Checklist:
* [x] **Dữ liệu:** Có sẵn dữ liệu bản vẽ tiến độ baseline (BIM/MS Project) và ứng dụng ghi nhận nhật ký công trình hàng ngày của Vincons.
* [x] **Tầm kiểm soát rủi ro:** Rủi ro được kiểm soát hoàn toàn nhờ Human-in-the-loop (Chỉ huy trưởng phê duyệt mọi kế hoạch).
* [x] **Sẵn sàng vận hành:** Các Chỉ huy trưởng sẵn sàng ứng dụng để giảm hơn 85% thời gian giám định & làm báo cáo giấy tờ (từ 4 giờ xuống dưới 30 phút/ngày, theo Success Metric).

### 📢 Quyết định cuối cùng:
[x] **GO (Bắt đầu xây dựng Prototype)**

**Lý giải quyết định (Justification):**  
Dự án giải quyết trực tiếp nút thắt lớn nhất tại các công trình thi công của Vincons, giúp rút ngắn thời gian giám định từ 4 giờ xuống 30 phút/ngày và giảm 30% tỷ lệ trễ tiến độ. Chi phí đầu tư AI Agent nhỏ hơn rất nhiều so với tổn thất khi dự án trễ hạn bàn giao.
