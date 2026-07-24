# 01 - Problem Scan

## Thành viên 1 - Trần Quang Thành - Mã HV: 2A202601133

## Phase 1 - SCAN

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | Xanh SM | Stakeholder Pain | Tài xế báo pin thấp giữa ca, điều phối viên phải tra cứu vị trí, trạm sạc và soạn hướng dẫn thủ công. |
| 2 | Xanh SM | Lặp lại | Điều phối viên phân loại lý do hủy chuyến từ ghi chú tài xế và cuộc gọi khách hàng. |
| 3 | Vinhomes | AI-upgrade | CSKH cư dân mất nhiều thời gian phân loại phản ánh về phí, tiện ích, an ninh và chuyển đúng bộ phận. |
| 4 | Vinmec | Tốn thời gian | Bác sĩ/điều dưỡng viết tóm tắt hồ sơ xuất viện thủ công từ nhiều phiếu khám và kết quả xét nghiệm. |
| 5 | VinFast | Lặp lại | Đối soát hóa đơn sạc điện giữa log xe, log trạm sạc và giao dịch thanh toán. |
| 6 | Vinpearl | AI-upgrade | Nhân viên hỗ trợ khách du lịch trả lời lặp lại về lịch vui chơi, vé, phòng và thay đổi lịch trình. |

## Phase 2 - QUICK-ASSESS

### Quick Problem Card #1 - Xanh SM xử lý sự cố pin thấp

| Trường | Nội dung |
|---|---|
| Bài toán | Khi tài xế Xanh SM báo pin thấp, điều phối viên cần nhanh chóng quyết định hướng dẫn đến trạm sạc gần nhất hoặc gọi xe sạc pin di động. |
| Công ty thành viên | Xanh SM |
| Actor | Tài xế đang chờ hỗ trợ và điều phối viên trung tâm. |
| Workflow hiện tại | 1. Tài xế gọi tổng đài -> 2. Điều phối viên hỏi biển số, pin, vị trí -> 3. Tra dashboard trạm sạc -> 4. Soạn hướng dẫn -> 5. Gửi cho tài xế hoặc gọi cứu hộ. |
| Bottleneck | Bước 3-4 mất khoảng 10-12 phút/lượt, dễ sai nếu trạm xa hoặc không phù hợp loại xe. |
| AI hỗ trợ | Gợi ý phương án an toàn và soạn nháp tin nhắn cho dispatcher duyệt. |
| Metric | Giảm thời gian xử lý từ 15 phút xuống dưới 3 phút; 98% đề xuất đúng điều kiện pin và khoảng cách. |
| Quick Architecture | LLM Feature + rule guardrails. |

### Quick Problem Card #2 - Vinhomes phân loại phản ánh cư dân

| Trường | Nội dung |
|---|---|
| Bài toán | Phản ánh cư dân từ app cần được phân loại và chuyển đúng bộ phận nhanh hơn. |
| Công ty thành viên | Vinhomes |
| Actor | Nhân viên CSKH tòa nhà và đội vận hành liên quan. |
| Workflow hiện tại | 1. Cư dân gửi phản ánh -> 2. CSKH đọc nội dung -> 3. Tự phân loại -> 4. Chuyển phòng ban -> 5. Theo dõi phản hồi. |
| Bottleneck | Bước 2-3 mất 5-8 phút/ticket, dễ nhầm nhóm phí/an ninh/kỹ thuật. |
| AI hỗ trợ | Tóm tắt, phân loại, đề xuất bộ phận nhận và mức độ ưu tiên. |
| Metric | 85% ticket được phân loại dưới 10 giây; giảm ticket chuyển sai xuống dưới 5%. |
| Quick Architecture | Rule + LLM Feature. |

### Quick Problem Card #3 - Vinmec tóm tắt hồ sơ xuất viện

| Trường | Nội dung |
|---|---|
| Bài toán | Nhân viên y tế mất nhiều thời gian viết bản tóm tắt xuất viện từ hồ sơ bệnh án. |
| Công ty thành viên | Vinmec |
| Actor | Bác sĩ điều trị, điều dưỡng hành chính, bệnh nhân chờ giấy tờ. |
| Workflow hiện tại | 1. Mở bệnh án -> 2. Đọc ghi chú khám -> 3. Tổng hợp xét nghiệm -> 4. Viết tóm tắt -> 5. Bác sĩ kiểm tra. |
| Bottleneck | Bước 2-4 mất 20-30 phút/bệnh nhân và có rủi ro bỏ sót thông tin. |
| AI hỗ trợ | Sinh nháp tóm tắt theo cấu trúc, bác sĩ duyệt trước khi ký. |
| Metric | Giảm thời gian soạn nháp xuống dưới 7 phút; 100% bản cuối vẫn do bác sĩ duyệt. |
| Quick Architecture | LLM Feature có Human-in-the-loop. |

## Thành viên 2 - Hoàng Văn Phái - 2A202601575

### Phase 1 - SCAN

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | Xanh SM | Lặp lại | Điều phối viên phải nhắn lại cùng một mẫu hướng dẫn khi tài xế cần đổi điểm đón. |
| 2 | Vinhomes | Tốn thời gian | CSKH lọc và gán nhóm cho phản ánh cư dân về nước, điện, phí, an ninh. |
| 3 | VinFast | AI-upgrade | Đội vận hành cần tóm tắt nhanh trạng thái lỗi từ nhiều log bảo trì khác nhau. |
| 4 | Vinmec | Stakeholder Pain | Nhân viên bệnh viện mất thời gian viết lại tóm tắt hồ sơ cho bệnh nhân xuất viện. |
| 5 | Vinpearl | Lặp lại | Nhân viên lễ tân trả lời lặp lại các câu hỏi về giờ check-in, dịch vụ và tiện ích. |

### Phase 2 - QUICK-ASSESS

#### Quick Problem Card #1

| Trường | Nội dung |
|---|---|
| Bài toán | Phân loại phản ánh cư dân Vinhomes và chuyển đúng bộ phận nhanh hơn. |
| Công ty thành viên | Vinhomes |
| Actor | Nhân viên CSKH nội khu. |
| Workflow hiện tại | 1. Nhận phản ánh -> 2. Đọc nội dung -> 3. Phân loại thủ công -> 4. Gán phòng ban -> 5. Theo dõi xử lý. |
| Bottleneck | Bước 2-3, khoảng 5-7 phút/ticket. |
| AI hỗ trợ | Tóm tắt và gợi ý nhãn xử lý. |
| Metric | 80% ticket được gán dưới 15 giây. |
| Quick Architecture | LLM Feature. |

#### Quick Problem Card #2

| Trường | Nội dung |
|---|---|
| Bài toán | Soạn nháp thông báo chuẩn khi tài xế Xanh SM gặp sự cố pin thấp. |
| Công ty thành viên | Xanh SM |
| Actor | Điều phối viên. |
| Workflow hiện tại | 1. Nhận cuộc gọi -> 2. Xác nhận vị trí -> 3. Tra trạm sạc -> 4. Soạn tin -> 5. Gửi cho tài xế duyệt. |
| Bottleneck | Bước 3-4, khoảng 8-10 phút/lượt. |
| AI hỗ trợ | Gợi ý trạm và viết draft tin nhắn. |
| Metric | Giảm thời gian soạn từ 10 phút xuống dưới 3 phút. |
| Quick Architecture | LLM + rule guardrail. |

#### Quick Problem Card #3

| Trường | Nội dung |
|---|---|
| Bài toán | Tóm tắt bệnh án xuất viện từ nhiều tài liệu y khoa. |
| Công ty thành viên | Vinmec |
| Actor | Bác sĩ điều trị. |
| Workflow hiện tại | 1. Mở hồ sơ -> 2. Đọc xét nghiệm -> 3. Gom thông tin -> 4. Viết tóm tắt -> 5. Duyệt ký. |
| Bottleneck | Bước 2-4, khoảng 20 phút/bệnh nhân. |
| AI hỗ trợ | Tạo bản nháp có cấu trúc. |
| Metric | Soạn nháp dưới 7 phút/bệnh nhân. |
| Quick Architecture | LLM Feature có HITL. |

## Thành viên 3 - Nguyễn Huy Anh - 2A202601641

### Phase 1 - SCAN

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | Xanh SM | Stakeholder Pain | Tài xế than phiền khi chờ phản hồi từ điều phối quá lâu vào giờ cao điểm. |
| 2 | VinFast | Lặp lại | So khớp hóa đơn sạc và đối soát giao dịch đối tác. |
| 3 | Vinhomes | AI-upgrade | Gợi ý trả lời khách cư dân theo ngữ cảnh thay vì mẫu cứng. |
| 4 | Vinmec | Tốn thời gian | Lọc thông tin từ kết quả xét nghiệm để tạo bản tóm tắt điều trị. |
| 5 | Vinpearl | AI-upgrade | Tự động gợi ý lịch trình tham quan theo nhu cầu khách. |

### Phase 2 - QUICK-ASSESS

#### Quick Problem Card #1

| Trường | Nội dung |
|---|---|
| Bài toán | Điều phối sự cố pin thấp cho tài xế Xanh SM. |
| Công ty thành viên | Xanh SM |
| Actor | Dispatcher trung tâm. |
| Workflow hiện tại | 1. Nhận báo cáo -> 2. Hỏi pin và vị trí -> 3. Tra cứu trạm -> 4. Soạn hướng dẫn -> 5. Gửi tin. |
| Bottleneck | Tra cứu và soạn hướng dẫn, 10 phút/lượt. |
| AI hỗ trợ | Draft route và cảnh báo ngưỡng an toàn. |
| Metric | Xử lý dưới 3 phút/lượt. |
| Quick Architecture | LLM Feature. |

#### Quick Problem Card #2

| Trường | Nội dung |
|---|---|
| Bài toán | Tóm tắt khiếu nại cư dân để chuyển đúng bộ phận. |
| Công ty thành viên | Vinhomes |
| Actor | CSKH. |
| Workflow hiện tại | 1. Nhận tin -> 2. Đọc nội dung -> 3. Phân loại -> 4. Chuyển phòng ban -> 5. Chờ phản hồi. |
| Bottleneck | Phân loại thủ công, 5 phút/ticket. |
| AI hỗ trợ | Tóm tắt + gợi ý nhãn. |
| Metric | 85% ticket gán đúng. |
| Quick Architecture | Rule + LLM. |

#### Quick Problem Card #3

| Trường | Nội dung |
|---|---|
| Bài toán | Tự sinh nháp tóm tắt xuất viện. |
| Công ty thành viên | Vinmec |
| Actor | Bác sĩ. |
| Workflow hiện tại | 1. Xem hồ sơ -> 2. Tổng hợp kết quả -> 3. Viết nháp -> 4. Duyệt -> 5. Ký. |
| Bottleneck | Tổng hợp và viết nháp, 20-30 phút/bệnh nhân. |
| AI hỗ trợ | Sinh nháp có cấu trúc. |
| Metric | Dưới 7 phút/bệnh nhân. |
| Quick Architecture | LLM + HITL. |

## Thành viên 4 - Phạm Trung Kiên - 2A202601986

### Phase 1 - SCAN

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | Xanh SM | Tốn thời gian | Điều phối viên phải đọc log thủ công để biết lý do tài xế trễ chuyến. |
| 2 | VinFast | Stakeholder Pain | Kỹ thuật viên xưởng cần tra nhanh lịch bảo trì xe theo từng nhóm lỗi. |
| 3 | Vinhomes | Lặp lại | Lọc các phản ánh trùng lặp từ cư dân theo cùng một chủ đề. |
| 4 | Vinmec | AI-upgrade | Gợi ý tóm tắt bệnh án theo template chuyên khoa. |
| 5 | Vinpearl | AI-upgrade | Tư vấn đặt phòng, đổi lịch và trả lời câu hỏi lặp lại cho khách. |

### Phase 2 - QUICK-ASSESS

#### Quick Problem Card #1

| Trường | Nội dung |
|---|---|
| Bài toán | Gộp và phân loại báo cáo lỗi xe điện từ xưởng VinFast. |
| Công ty thành viên | VinFast |
| Actor | Kỹ thuật viên và giám sát xưởng. |
| Workflow hiện tại | 1. Nhận log -> 2. Đọc lỗi -> 3. Ghi nhóm lỗi -> 4. Tạo ticket -> 5. Chuyển đội phụ trách. |
| Bottleneck | Đọc log và gán nhóm lỗi, 12 phút/lượt. |
| AI hỗ trợ | Tóm tắt và gợi ý nhóm lỗi. |
| Metric | Rút xuống dưới 2 phút/lượt. |
| Quick Architecture | LLM Feature. |

#### Quick Problem Card #2

| Trường | Nội dung |
|---|---|
| Bài toán | Xử lý câu hỏi lặp lại của khách Vinpearl theo ngữ cảnh đặt phòng. |
| Công ty thành viên | Vinpearl |
| Actor | Nhân viên CSKH. |
| Workflow hiện tại | 1. Khách hỏi -> 2. Đọc yêu cầu -> 3. Tra thông tin -> 4. Soạn trả lời -> 5. Gửi. |
| Bottleneck | Tra cứu và soạn trả lời, 6-8 phút. |
| AI hỗ trợ | Soạn draft trả lời. |
| Metric | 90% câu hỏi được soạn dưới 10 giây. |
| Quick Architecture | LLM Feature. |

#### Quick Problem Card #3

| Trường | Nội dung |
|---|---|
| Bài toán | Tóm tắt lý do hủy chuyến Xanh SM từ cuộc gọi và ghi chú. |
| Công ty thành viên | Xanh SM |
| Actor | Điều phối viên phân tích hậu kiểm. |
| Workflow hiện tại | 1. Thu dữ liệu -> 2. Đọc ghi chú -> 3. Gán lý do -> 4. Thống kê -> 5. Báo cáo. |
| Bottleneck | Bước đọc và gán lý do, 5-10 phút/case. |
| AI hỗ trợ | Tóm tắt và phân loại lý do hủy. |
| Metric | 85% case gán dưới 15 giây. |
| Quick Architecture | Rule + LLM. |

## Thành viên 5 - Hà Tấn Phong - 2A202601577

### Phase 1 - SCAN

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | Xanh SM | AI-upgrade | Tự gợi ý câu trả lời cho tài xế khi hệ thống điều vận có sự cố. |
| 2 | VinFast | Lặp lại | Đối chiếu hóa đơn dịch vụ và bảo hành định kỳ. |
| 3 | Vinmec | Tốn thời gian | Viết lại ghi chú khám thành báo cáo hành chính. |
| 4 | Vinhomes | Stakeholder Pain | Xử lý phản ánh cư dân về tiếng ồn và tiện ích chung. |
| 5 | Vinpearl | Lặp lại | Xử lý yêu cầu đổi phòng, hủy phòng, hỏi giờ dịch vụ. |

### Phase 2 - QUICK-ASSESS

#### Quick Problem Card #1

| Trường | Nội dung |
|---|---|
| Bài toán | Soạn nháp thông tin phản hồi cho tài xế Xanh SM khi pin thấp. |
| Công ty thành viên | Xanh SM |
| Actor | Dispatcher. |
| Workflow hiện tại | 1. Nhận yêu cầu -> 2. Kiểm tra xe -> 3. Tra trạm -> 4. Soạn tin -> 5. Gửi draft. |
| Bottleneck | Soạn tin và kiểm tra đúng trạm, 8 phút/lượt. |
| AI hỗ trợ | Draft message theo rule. |
| Metric | Dưới 3 phút/lượt. |
| Quick Architecture | LLM + Guardrail. |

#### Quick Problem Card #2

| Trường | Nội dung |
|---|---|
| Bài toán | Chuẩn hóa phản hồi khi cư dân hỏi cùng một mẫu câu. |
| Công ty thành viên | Vinhomes |
| Actor | CSKH. |
| Workflow hiện tại | 1. Đọc câu hỏi -> 2. Chọn mẫu -> 3. Chỉnh sửa -> 4. Gửi trả lời. |
| Bottleneck | Chọn và chỉnh mẫu, 4 phút/ticket. |
| AI hỗ trợ | Gợi ý mẫu phù hợp. |
| Metric | 80% ticket dưới 10 giây. |
| Quick Architecture | LLM Feature. |

#### Quick Problem Card #3

| Trường | Nội dung |
|---|---|
| Bài toán | Tổng hợp dữ liệu bệnh án thành bản nháp ngắn. |
| Công ty thành viên | Vinmec |
| Actor | Bác sĩ điều trị. |
| Workflow hiện tại | 1. Xem hồ sơ -> 2. Chọn dữ liệu -> 3. Viết nháp -> 4. Duyệt -> 5. Lưu. |
| Bottleneck | Chọn dữ liệu và viết nháp, 15-20 phút. |
| AI hỗ trợ | Sinh nháp chuẩn hóa. |
| Metric | Dưới 5 phút/bệnh nhân. |
| Quick Architecture | LLM + HITL. |

## Thành viên 6 - Nguyễn Văn Đại - 2A202601217

### Phase 1 - SCAN

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | Xanh SM | Stakeholder Pain | Tài xế bực vì phải chờ quyết định điều phối trong giờ cao điểm. |
| 2 | Vinhomes | AI-upgrade | Gợi ý ưu tiên ticket theo mức độ khẩn cấp. |
| 3 | VinFast | Tốn thời gian | Tự động hóa đối soát dữ liệu sạc xe. |
| 4 | Vinmec | Lặp lại | Tóm tắt hồ sơ y tế cho bác sĩ tuyến sau. |
| 5 | Vinpearl | AI-upgrade | Trả lời câu hỏi du khách và gợi ý lịch trình. |

### Phase 2 - QUICK-ASSESS

#### Quick Problem Card #1

| Trường | Nội dung |
|---|---|
| Bài toán | Điều phối trạm sạc di động khi xe Xanh SM báo pin dưới ngưỡng. |
| Công ty thành viên | Xanh SM |
| Actor | Điều phối viên. |
| Workflow hiện tại | 1. Nhận cảnh báo -> 2. Xác minh vị trí -> 3. Kiểm tra ngưỡng pin -> 4. Gọi đội hỗ trợ -> 5. Ghi nhận. |
| Bottleneck | Xác minh vị trí và gọi hỗ trợ, 7-9 phút/lượt. |
| AI hỗ trợ | Cảnh báo rủi ro và soạn lệnh nháp. |
| Metric | Gọi hỗ trợ dưới 2 phút. |
| Quick Architecture | LLM + Rule. |

#### Quick Problem Card #2

| Trường | Nội dung |
|---|---|
| Bài toán | Phân loại ticket Vinhomes để giảm chuyển nhầm. |
| Công ty thành viên | Vinhomes |
| Actor | Bộ phận CSKH. |
| Workflow hiện tại | 1. Nhận ticket -> 2. Đọc nội dung -> 3. Phân nhóm -> 4. Chuyển người xử lý -> 5. Theo dõi. |
| Bottleneck | Phân nhóm thủ công, 5 phút/ticket. |
| AI hỗ trợ | Gợi ý nhãn và bộ phận. |
| Metric | 90% ticket gán đúng. |
| Quick Architecture | Rule + LLM. |

#### Quick Problem Card #3

| Trường | Nội dung |
|---|---|
| Bài toán | Tóm tắt lời phàn nàn và yêu cầu của khách Vinpearl. |
| Công ty thành viên | Vinpearl |
| Actor | Nhân viên chăm sóc khách hàng. |
| Workflow hiện tại | 1. Nhận tin -> 2. Chọn thông tin chính -> 3. Soạn phản hồi -> 4. Duyệt -> 5. Gửi. |
| Bottleneck | Chọn thông tin chính và soạn phản hồi, 6 phút/case. |
| AI hỗ trợ | Tạo draft phản hồi. |
| Metric | Dưới 10 giây/case. |
| Quick Architecture | LLM Feature. |
