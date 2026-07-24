# Phase 1 & Phase 2: SCAN & QUICK-ASSESS (Báo cáo cá nhân)

> **Họ và tên:** Học viên AI Product Engineer  
> **Đơn vị:** Vin Smart Future (Vingroup)  
> **Dự án:** Lab 02 — AI Product Scoping  

---

## 🔍 Phase 1 — SCAN: Bảng Quét Cơ Hội Tối Ưu Bằng AI

Bảng dưới đây quét qua các hoạt động vận hành thực tế tại các công ty thành viên thuộc Tập đoàn Vingroup sử dụng **4 Thấu kính (4 Lenses)**:

| # | Công ty thành viên | Thấu kính (Lens) | Mô tả ngắn bài toán / Nút thắt vận hành (Bottleneck) |
|---|--------------------|------------------|------------------------------------------------------|
| **1** | **Xanh SM (GSM)** | Tốn thời gian | Điều phối viên xử lý thủ công các báo cáo sự cố xe taxi điện cạn pin khẩn cấp trên đường đón khách (mất 15-20 phút/lượt tra cứu trạm sạc trống và soạn SMS hướng dẫn). |
| **2** | **Vinhomes** | Lặp lại | Ban quản lý tòa nhà phải đọc và phân loại thủ công hàng trăm phản ánh/khiếu nại mỗi ngày của cư dân gửi qua App Vinhomes Resident để chuyển tiếp đến đúng bộ phận kỹ thuật/vệ sinh/an ninh. |
| **3** | **VinFast** | AI-upgrade | Chẩn đoán sơ bộ mã lỗi kỹ thuật xe điện dựa trên mô tả tự do bằng tiếng Việt của khách hàng (vd: *"xe đi qua gờ giảm tốc kêu cụp cụp ở bánh trước"*), hỗ trợ kỹ thuật viên đặt trước phụ tùng. |
| **4** | **Vinpearl** | Pain từ người khác | Quản lý resort mất nhiều thời gian quét qua các đánh giá (reviews) trên Booking.com, Agoda, Google Maps để lọc các phản phàn nàn khẩn cấp (về vệ sinh, thái độ nhân viên) nhằm xử lý tức thì. |
| **5** | **Vinmec** | Tốn thời gian | Bác sĩ mất 20-30 phút/bệnh nhân để trích xuất dữ liệu lâm sàng từ hệ thống EHR và viết tay bản tóm tắt hồ sơ xuất viện (Discharge Summary) bằng ngôn ngữ dễ hiểu cho người bệnh. |

---

## 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards

Chọn **Top 3 bài toán tiềm năng nhất** từ Phase 1 (#1 Xanh SM, #2 Vinhomes, #3 VinFast) để phân tích chi tiết:

---

### 🎴 QUICK PROBLEM CARD #1: Xanh SM — Xử Lý Sự Cố Sạc Pin Thực Địa Khẩn Cấp

```text
┌─────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                                   │
│                                                                         │
│ Bài toán: Tài xế Xanh SM báo sự cố xe cạn pin giữa đường, cần chỉ dẫn   │
│ trạm sạc VinFast gần nhất hoặc điều xe cứu hộ sạc pin di động.          │
│ Công ty thành viên: [x] Xanh SM (GSM)                                   │
│                                                                         │
│ Ai đang đau (Actor)?                                                    │
│ - Tài xế (hoang mang, nguy cơ hủy cuốc đón khách VIP).                  │
│ - Điều phối viên Dispatcher (quá tải vào giờ cao điểm).                 │
│                                                                         │
│ Workflow thủ công hiện tại (5 bước):                                    │
│   1. Tài xế gọi hotline điều vận báo sự cố hết pin.                    │
│   ──> 2. Điều phối viên tra cứu tọa độ GPS thực tế của xe trên bản đồ.  │
│   ──> 3. Tra cứu thủ công Dashboard trạm sạc VinFast còn trụ trống.     │
│   ──> 4. Soạn tin nhắn chỉ đường chi tiết gửi qua App tài xế.           │
│   ──> 5. Gọi xe cứu hộ pin lưu động nếu lượng pin dưới ngưỡng nguy hiểm.│
│                                                                         │
│ Bước tốn thời gian/gây lỗi nhất?                                        │
│ - Bước 3 & 4: Tra cứu trụ sạc tương thích và soạn SMS (⏱ 10-12 phút).    │
│                                                                         │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                                  │
│ - Bước 3 & 4: Tự động pull vị trí GPS -> tra cứu trạm trống phù hợp     │
│   -> AI Draft sẵn nội dung chỉ đường có mã định vị.                     │
│                                                                         │
│ Đo thành công bằng gì (Metric có số)?                                   │
│ - Giảm thời gian xử lý sự cố từ 15 phút ──> dưới 3 phút/lượt.           │
│ - Tỉ lệ hướng dẫn đúng trạm sạc còn trụ trống đạt >= 98%.               │
│                                                                         │
│ Quick Architecture: [x] LLM Feature (Có Human-in-the-loop duyệt tin nháp)│
└─────────────────────────────────────────────────────────────────────────┘
```

---

### 🎴 QUICK PROBLEM CARD #2: Vinhomes — Phân Loại & Điều Hướng Phản Ánh Cư Dân

```text
┌─────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                                   │
│                                                                         │
│ Bài toán: Phân loại và định tuyến tự động ý kiến/khiếu nại của cư dân   │
│ gửi trên App Vinhomes Resident đến đúng Ban Quản Lý (BQL) từng tòa nhà. │
│ Công ty thành viên: [x] Vinhomes                                        │
│                                                                         │
│ Ai đang đau (Actor)?                                                    │
│ - Cư dân Vinhomes (chờ đợi phản hồi lâu, CSKH rập khuôn).               │
│ - Nhân viên CSKH BQL (mất thời gian đọc và chuyển tiếp thủ công).       │
│                                                                         │
│ Workflow thủ công hiện tại (4 bước):                                    │
│   1. Cư dân gửi ticket khiếu nại (text + ảnh) lên App Vinhomes Resident.│
│   ──> 2. Nhân viên CSKH tổng đọc thủ công nội dung ticket.              │
│   ──> 3. Phân loại thủ công (Vệ sinh / Kỹ thuật / An ninh / Bãi xe...). │
│   ──> 4. Tạo task thủ công chuyển về BQL khu đô thị tương ứng.          │
│                                                                         │
│ Bước tốn thời gian/gây lỗi nhất?                                        │
│ - Bước 2 & 3: Đọc và phân loại sai phòng ban (⏱ 10-15 phút/ticket).      │
│                                                                         │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                                  │
│ - Bước 2 & 3: LLM tự động đọc nội dung ticket, phân tích mức độ khẩn   │
│   cấp và tự động gán nhãn Route đến đúng BQL tòa nhà trong < 5 giây.   │
│                                                                         │
│ Đo thành công bằng gì (Metric có số)?                                   │
│ - Giảm thời gian điều hướng ticket từ 15 phút ──> dưới 30 giây.          │
│ - Độ chính xác phân loại tự động đạt >= 95%.                            │
│                                                                         │
│ Quick Architecture: [x] LLM Feature (kèm Rule-based router)             │
└─────────────────────────────────────────────────────────────────────────┘
```

---

### 🎴 QUICK PROBLEM CARD #3: VinFast — Chẩn Đoán Sơ Bộ Mã Lỗi Xe Điện Từ Mô Tả Tiếng Việt

```text
┌─────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                                   │
│                                                                         │
│ Bài toán: Phân tích mô tả sự cố bằng tiếng Việt tự nhiên của chủ xe VF │
│ để gợi ý mã lỗi kỹ thuật ban đầu, hỗ trợ Xưởng dịch vụ chuẩn bị phụ tùng│
│ Công ty thành viên: [x] VinFast                                         │
│                                                                         │
│ Ai đang đau (Actor)?                                                    │
│ - Khách hàng đi xe VinFast (không biết dùng từ ngữ kỹ thuật chuyên môn). │
│ - Kỹ thuật viên Xưởng dịch vụ (mất thời gian chẩn đoán lại từ đầu).     │
│                                                                         │
│ Workflow thủ công hiện tại (4 bước):                                    │
│   1. Khách hàng gọi/nhắn tin mô tả hiện tượng hư hỏng trên xe.          │
│   ──> 2. Cố vấn dịch vụ đọc/nghe và ghi chú lại lời kể khách hàng.      │
│   ──> 3. Đưa xe vào cầu nâng để kỹ thuật viên kiểm tra đọc lỗi OBD.    │
│   ──> 4. Tra cứu kho phụ tùng xem có sẵn vật tư thay thế hay không.     │
│                                                                         │
│ Bước tốn thời gian/gây lỗi nhất?                                        │
│ - Bước 2 & 4: Suy đoán lỗi thủ công và thiếu sẵn phụ tùng (⏱ 45 phút).   │
│                                                                         │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                                  │
│ - Bước 2: AI đọc mô tả ngôn ngữ tự nhiên, đối chiếu cơ sở kiến thức    │
│   (Knowledge Base) kỹ thuật VinFast để xuất ra top 3 mã lỗi nghi vấn.   │
│                                                                         │
│ Đo thành công bằng gì (Metric có số)?                                   │
│ - Tăng tỉ lệ chẩn đoán đúng ngay từ lần đầu (First-Time Fix) lên 90%.   │
│ - Rút ngắn thời gian tiếp nhận xe tại Xưởng dịch vụ từ 45m ──> 15m.    │
│                                                                         │
│ Quick Architecture: [x] LLM Feature + RAG (Retrieval-Augmented Gen)     │
└─────────────────────────────────────────────────────────────────────────┘
```
