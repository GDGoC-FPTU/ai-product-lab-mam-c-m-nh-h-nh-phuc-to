# 02 - Deep Dive Report
Tên nhóm: Nhóm Xanh SM Pin Thấp
Thành viên:
- Trần Quang Thành - Mã HV: 2A202601133
- Hoàng Văn Phái - Mã HV: 2A202601575
- Nguyễn Huy Anh - Mã HV: 2A202601641
- Phạm Trung Kiên - Mã HV: 2A202601986
- Hà Tấn Phong - Mã HV: 2A202601577
- Nguyễn Văn Đại - Mã HV: 2A202601217
## Quyết định lựa chọn
Nhóm chọn bài toán: **Xanh SM xử lý sự cố pin thấp thực địa cho tài xế xe điện**.
Lý do chọn: bài toán có tần suất lặp lại, ảnh hưởng trực tiếp đến vận hành đội xe, có dữ liệu đầu vào rõ như vị trí xe, phần trăm pin, khoảng cách trạm sạc và trạng thái trụ sạc. Rủi ro có thể kiểm soát bằng rule guardrail và bước duyệt của điều phối viên.
## 3.1 Current-State Workflow
```text
Tài xế gọi báo sự cố
  -> Handoff: tổng đài/điều phối viên nhận thông tin (2 phút)
  -> Dispatcher hỏi biển số, vị trí GPS, phần trăm pin (2 phút)
  -> Handoff: dispatcher tra dashboard xe và bản đồ trạm sạc (3 phút)
  -> Bottleneck: kiểm tra trạm sạc còn trống, khoảng cách, loại xe (5 phút)
  -> Bottleneck: soạn tin nhắn hướng dẫn cho tài xế (4 phút)
  -> Dispatcher gửi tin hoặc gọi đội sạc pin di động (1 phút)
Tổng thời gian hiện tại: khoảng 17 phút/lượt.
```
## 3.2 Problem Statement 6-field
| Field | Nội dung |
|---|---|
| Actor / Operator | Điều phối viên trung tâm Xanh SM xử lý yêu cầu hỗ trợ từ tài xế. |
| Current Workflow | Khi tài xế báo pin thấp, dispatcher hỏi thông tin, tra vị trí xe, tra trạm sạc VinFast còn chỗ, kiểm tra khoảng cách và soạn hướng dẫn thủ công. Nếu pin quá thấp thì liên hệ đội sạc pin di động. |
| Bottleneck | Dispatcher mất nhiều thời gian ở bước chọn phương án an toàn và soạn hướng dẫn. Sai sót lớn nhất là đề xuất trạm quá xa khi pin đã rất thấp. |
| Business Impact | Với giả định 80 ca/ngày, quy trình 17 phút/lượt tiêu tốn khoảng 22,7 giờ điều phối/ngày. Xe chờ lâu làm giảm thời gian nhận chuyến, tăng hủy chuyến và giảm trải nghiệm tài xế. |
| Success Metric | Giảm thời gian xử lý từ 17 phút xuống dưới 3 phút/lượt; 98% draft tuân thủ rule pin/khoảng cách; 100% tin nhắn gửi ra ngoài phải được người duyệt. |
| Operational Boundary | AI chỉ được tạo khuyến nghị và nháp tin nhắn. AI không được tự gửi tin, không được bỏ tag `[DRAFT_ONLY]`, không được đề xuất trạm xa hơn 5km khi pin dưới 5%, và phải trả JSON `dispatch_mobile_charger` khi cần cứu hộ sạc pin di động. |
## 3.3 Future-State Flow & AI Fit
AI Fit: **LLM Feature + deterministic rule guardrails**. Không chọn Agent tự trị vì hệ thống chưa nên tự ra lệnh điều phối ngoài hiện trường khi chưa có người duyệt.
```text
Tài xế báo sự cố
  -> Hệ thống auto-pull vị trí xe, phần trăm pin, loại xe
  -> Rule guardrail kiểm tra ngưỡng pin và khoảng cách trạm
  -> AI draft phương án hỗ trợ bằng tiếng Việt
  -> Dispatcher review và chỉnh sửa nếu cần
  -> Dispatcher bấm gửi hoặc gọi đội sạc pin di động
Fallback:
- Nếu thiếu dữ liệu vị trí/pin/khoảng cách, AI yêu cầu bổ sung dữ liệu.
- Nếu Gemini lỗi hoặc confidence thấp, dispatcher xử lý theo quy trình cũ.
- Nếu pin < 5% và trạm > 5km, hệ thống bỏ qua draft chỉ đường và trả action dispatch_mobile_charger.
```
## Phase 5 - Evaluate
| Checklist | Đánh giá |
|---|---|
| Có dữ liệu mẫu/logs sạch để test? | Có thể lấy log tổng đài, GPS xe, pin xe, trạm sạc và lịch sử xử lý sự cố. Cần 2-4 tuần chuẩn hóa dữ liệu trước pilot. |
| Rủi ro khi AI sai có kiểm soát được? | Có. Rule guardrail chạy trước model, mọi tin nhắn đều là `[DRAFT_ONLY]` và dispatcher duyệt trước khi gửi. |
| Stakeholders sẵn sàng đổi quy trình? | Khả thi vì giải pháp giảm thao tác tra cứu và soạn tin, không thay thế quyền quyết định của dispatcher. |
Quyết định: **GO cho prototype scope hẹp**.
Justification: bài toán đủ cụ thể, dữ liệu đầu vào có cấu trúc, metric đo được, chi phí prototype thấp vì dùng LLM cho phần soạn nháp và rule-based guardrail cho quyết định an toàn. Scope pilot nên giới hạn tại một thành phố, một nhóm xe, và chỉ xử lý các ca pin thấp trước khi mở rộng sang sự cố khác.