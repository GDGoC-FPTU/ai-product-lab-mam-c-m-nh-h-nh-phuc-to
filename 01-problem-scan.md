Phase 1

VinAI – Repetitive: AI đánh giá chất lượng dữ liệu gán nhãn (data annotation) và phát hiện các mẫu bị gán nhãn sai trước khi đưa vào huấn luyện mô hình AI.
VinBigData – Time-consuming: AI tự động sinh tài liệu (documentation) cho pipeline xử lý dữ liệu dựa trên metadata và source code, giúp giảm thời gian viết tài liệu thủ công.
VinCSS – Time-consuming: AI điều tra sự cố bảo mật bằng cách tổng hợp log từ nhiều hệ thống và tạo báo cáo điều tra ban đầu cho chuyên viên an ninh mạng.
VinBus – AI-upgrade: AI dự đoán nhu cầu hành khách theo từng tuyến dựa trên dữ liệu thời tiết, ngày lễ và sự kiện để tối ưu số lượng xe vận hành.
VinSchool – Stakeholder Pain: AI phát hiện học sinh có nguy cơ giảm kết quả học tập dựa trên dữ liệu điểm danh, điểm số và phản hồi của giáo viên để hỗ trợ can thiệp sớm.


Phase 2

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: AI điều tra sự cố bảo mật và tạo báo cáo ban đầu. │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [x] Khác: VinCSS           │
│                                                             │
│ Ai đang đau (Actor)? Chuyên viên SOC/An ninh mạng           │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│ 1. Thu thập log → 2. Phân tích log → 3. Điều tra sự cố →    │
│ 4. Viết báo cáo                                             │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Phân tích log (⏱ 30 phút/lượt)                              │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ Phân tích log và tạo báo cáo nháp.                          │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian phân tích từ 30 phút xuống dưới 5 phút.      │
│                                                             │
│ Quick Architecture: [ ] No AI [ ] Rule [x] LLM [ ] Agent    │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: AI dự đoán nhu cầu hành khách theo từng tuyến xe. │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [x] Khác: VinBus           │
│                                                             │
│ Ai đang đau (Actor)? Điều phối viên vận hành               │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│ 1. Thu thập dữ liệu → 2. Phân tích → 3. Dự báo →            │
│ 4. Phân bổ xe                                               │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Dự báo nhu cầu (⏱ 20 phút/lượt)                             │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ Phân tích dữ liệu và dự báo nhu cầu.                        │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Tăng độ chính xác dự báo lên trên 90%.                      │
│                                                             │
│ Quick Architecture: [ ] No AI [ ] Rule [x] LLM [ ] Agent    │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán: AI phát hiện học sinh có nguy cơ giảm học lực.    │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [x] Khác: VinSchool        │
│                                                             │
│ Ai đang đau (Actor)? Giáo viên chủ nhiệm                    │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│ 1. Xem điểm → 2. Xem điểm danh → 3. Đánh giá →              │
│ 4. Liên hệ phụ huynh                                        │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                            │
│ Đánh giá nguy cơ (⏱ 15 phút/học sinh)                       │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ Phân tích dữ liệu và cảnh báo học sinh nguy cơ cao.         │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Phát hiện trên 90% học sinh có nguy cơ trong dưới 1 phút.   │
│                                                             │
│ Quick Architecture: [ ] No AI [ ] Rule [x] LLM [ ] Agent    │
└─────────────────────────────────────────────────────────────┘
