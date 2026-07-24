# Lab 02 — Worksheet: AI Product Scoping (Vin Smart Future)

---

## 🏛️ 1. Bối cảnh thực tế: Vin Smart Future (Vingroup)

**Vingroup** — Tập đoàn tư nhân lớn nhất Việt Nam — vừa sáp nhập toàn bộ các phòng ban công nghệ thuộc các công ty thành viên thành một đơn vị công nghệ thống nhất mang tên **Vin Smart Future**. 

Nhiệm vụ của **Vin Smart Future** là xây dựng các giải pháp AI, số hóa, và tự động hóa cốt lõi để nâng cao hiệu suất vận hành và trải nghiệm khách hàng xuyên suốt các công ty thành viên:
* 🚗 **VinFast:** Hệ thống xe điện thông minh (EV), trợ lý AI ảo trong xe, dự đoán bảo trì pin, và quản lý chuỗi cung ứng sản xuất.
* 🚕 **Xanh SM (GSM):** Vận hành đội xe taxi/xe máy điện thông minh, điều vận thông minh (Smart Dispatching), tối ưu hóa lộ trình di chuyển.
* 🏢 **Vinhomes:** Quản lý đô thị thông minh (Smart Cities), trợ lý cư dân thông minh, tối ưu hóa mức tiêu thụ năng lượng.
* 🏥 **Vinmec:** Y tế thông minh, chẩn đoán hình ảnh bằng AI, tối ưu hóa quản lý hồ sơ bệnh án.
* 🎢 **Vinpearl / VinWonders:** Trải nghiệm du lịch số hóa, quản lý phòng và luồng khách thông minh tại các khu vui chơi.

Trong buổi Lab hôm nay, nhóm của bạn sẽ đóng vai trò là **AI Product Engineer** tại **Vin Smart Future**, tiến hành tìm kiếm, scoping, phân tích độ khả thi, thiết lập ranh giới vận hành, và xây dựng một **bản mẫu kỹ thuật (prompt prototype)** cho một bài toán cụ thể thuộc một trong những mảng kinh doanh trên.

---

## 📊 2. Cơ cấu tính điểm bài lab

### 👥 Điểm nhóm (60 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **G1. Workflow Mapping** | 20 | Problem Deep-Dive | Vẽ chi tiết quy trình hiện tại: các bước, handoff, thời gian, bottleneck |
| **G2. Problem Statement** | 20 | Problem Deep-Dive | Problem Statement 6-field bám sát thực tế, metric có số và ranh giới rõ ràng |
| **G3. AI Fit & Future Flow** | 10 | Problem Deep-Dive | So sánh Rule vs LLM vs Agent, future flow có bước AI, ranh giới và Fallback |
| **G4. Decision Quality** | 10 | Problem Deep-Dive | Quyết định Go/Not Yet/No-Go trung thực và có chứng cứ rõ ràng |

### 👤 Điểm cá nhân (40 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **I1. Scan & Cards** | 15 | Quick Cards | Liệt kê 5 problems sử dụng 3 lenses, hoàn thiện 3 quick cards chất lượng |
| **I2. Prototyping** | 10 | 02-lab/ | Chạy thử nghiệm programmatic prompt prototype thành công |
| **I3. AI Log & Reflection** | 15 | 03-ai-log.md | Phản ánh trung thực về việc dùng AI làm thought-partner (giúp gì, sai gì, sửa gì) |

---

# 🚀 Phase 0 — worked Example: Xanh SM Intelligent Dispatcher (15 min)

*Giảng viên walk-through ví dụ thực tế từ Vin Smart Future để bạn hiểu rõ cách scoping một bài toán AI.*
Đọc chi tiết worked example tại file [02-deliverable-example.md](02-deliverable-example.md).

---

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
| 5 | Vincons |  |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                     │
│                                                             │
│ Bài toán (1 câu): Quản lý tiến độ và chất lượng xây dựng tùy theo công trình, subcontractor và đội thợ để điều phối nhân lực hiệu quả  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ) Vincons  │
│                                                             │
│ Ai đang đau (Actor)? Nhà thầu chính                          │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Quản đốc và chủ thầu báo cáo tại chỗ ──> 2. Chủ thầu giám định tiến độ/chất lượng ──> 3. Điều phối tài nguyên và nhân lực ──> 4. Đánh giá sau hoàn thiện                   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Giám định tiến độ (⏱ N phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Quản lý tiến độ và chu kỳ thi công, quản lý nhân sự trong công trình │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Tiến độ thi công giảm rõ so với các dự án chưa thí điểm │
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

---

# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

## 3.1. Current-State Workflow Mapping (25 min)
**Vẽ quy trình hiện tại lên bảng/giấy A3.** Sử dụng các ký hiệu:
* 🔴 **Bottleneck:** Bước gây tắc nghẽn, tốn thời gian, hoặc sai sót nhiều nhất.
* 🔄 **Handoff:** Điểm chuyển giao thông tin giữa người và hệ thống, hoặc giữa các bộ phận.
* Ghi rõ thời gian vận hành trung bình: **Tổng cộng = ____ phút/lượt**.



## 3.2. Problem Statement (6-field) & Metrics (15 min)
Điền đầy đủ 6 trường thông tin của bài toán:

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Ai đang thực hiện tác vụ hằng ngày? |
| **2. Current Workflow** | Mô tả tóm tắt quy trình thủ công hiện tại và công cụ sử dụng. |
| **3. Bottleneck** | Bước nào chậm, lỗi, hoặc cần xử lý ngôn ngữ tự động nhiều nhất? |
| **4. Business Impact** | Tổn thất thực tế đo bằng thời gian, chi phí, hoặc SLA của Vingroup. |
| **5. Success Metric** | AI giải quyết được thì đạt ngưỡng số mấy? (Ví dụ: *"85% vé được phân loại dưới 10s"*). |
| **6. Operational Boundary** | AI được phép làm gì, TUYỆT ĐỐI không được làm gì, điểm nào cần duyệt? |

## 3.3. Future-State Flow & AI Fit (25 min)
* **Xác định mức AI Fit (AI-Fit Matrix):** Giải pháp thuộc nhóm nào? [ ] Rule / State-Machine [ ] LLM Feature [ ] Agentic Loop.
* **Vẽ Future-State Flow:** Đánh dấu rõ:
  * 🔵 **AI Step:** Tác vụ LLM xử lý.
  * 🟢 **Human Step (HITL):** Bước con người phê duyệt/review (Human-in-the-loop).
  * ↩️ **Fallback:** Kế hoạch dự phòng khi LLM trả về kết quả lỗi hoặc không tự tin.

---

# 💻 Phase 4 — TECHNICAL PROMPT PROTOTYPE (Nhóm, 30 min)

Để đảm bảo kỹ sư của Vin Smart Future luôn giữ vững năng lực lập trình, nhóm của bạn sẽ tiến hành **lập trình bản mẫu prompt** trực tiếp trên **Gemini 2.5 Flash** bằng Python để stress-test hệ thống.

### Hướng dẫn thực hiện:
1. Mở file [starter-code/prompt_prototype.py](starter-code/prompt_prototype.py) bằng VS Code/Cursor.
2. Hoàn thiện các nội dung sau:
   * **System Prompt:** Viết chỉ thị cực kỳ nghiêm ngặt quy định vai trò, nhiệm vụ, định dạng output và **Operational Boundary (Ranh giới cấm)** của mô hình.
   * **Structured Output:** Định nghĩa định dạng JSON output rõ ràng.
   * **Adversarial Test Cases:** Viết ít nhất 3 prompts "tấn công" (Adversarial inputs) cố tình dụ AI vượt ranh giới hoặc đưa ra câu trả lời không được phép để kiểm tra xem ranh giới của bạn có thực sự vững chắc.
3. Chạy file python:
   ```bash
   python3 prompt_prototype.py
   ```
4. Kiểm tra xem các ranh giới an toàn có bị LLM phá vỡ hay không và ghi lại kết quả vào worksheet.

---

# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)

### AI Readiness Checklist:
1. [ ] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test?
2. [ ] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?
3. [ ] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[ ] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[ ] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.

**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
> *Viết lý giải chi tiết tại đây*

---

# 📝 Phase 6 — REFLECTION (Cá nhân)
*Ghi nhận phản ánh của cá nhân bạn về việc phối hợp với AI trong buổi học hôm nay vào file `03-ai-log.md`.*
