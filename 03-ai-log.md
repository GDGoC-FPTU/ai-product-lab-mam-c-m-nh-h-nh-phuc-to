# 03 - AI Log & Reflection

## Thành viên 1 - Trần Quang Thành - Mã HV: 2A202601133

## AI đã giúp gì

Tôi dùng AI như thought-partner để brainstorm các pain point vận hành trong hệ sinh thái Vingroup, đặc biệt là Xanh SM, Vinhomes và Vinmec. AI giúp chuyển các ý tưởng rộng thành problem card có actor, workflow, bottleneck, metric và kiến trúc sơ bộ.

Trong phần prototype, AI hỗ trợ xác định ranh giới vận hành cho prompt: luôn gắn `[DRAFT_ONLY]`, không tự gửi tin, không đề xuất trạm xa khi pin dưới 5%, và phải có human-in-the-loop.

## AI đã sai hoặc còn yếu ở đâu

AI có xu hướng đề xuất hệ thống Agent tự động điều phối toàn bộ, trong khi bài toán này có rủi ro hiện trường: nếu hướng dẫn sai trạm sạc hoặc sai khoảng cách, xe có thể hết pin giữa đường. AI cũng đôi lúc đưa metric quá tham vọng mà không gắn với baseline, ví dụ giảm gần như toàn bộ thời gian xử lý mà chưa tính bước dispatcher duyệt.

## Tôi đã sửa như thế nào

Tôi thu hẹp scope thành LLM Feature có rule guardrail thay vì Agent tự trị. Prompt được bổ sung ranh giới cứng: mọi tin gửi ra phải là nháp `[DRAFT_ONLY]`; pin dưới 5% không được hướng dẫn tới trạm xa hơn 5km; nếu vi phạm ngưỡng an toàn thì trả action `dispatch_mobile_charger`.

Tôi cũng thêm adversarial tests để ép mô hình đối mặt với yêu cầu nguy hiểm như bỏ tag nháp, gửi thẳng tin, hoặc đề xuất trạm xa khi xe chỉ còn 2% pin.

## Thành viên 2 - Điền tên - Điền MSSV

### AI đã giúp gì

AI giúp tôi lấy lại khung tư duy theo rubric: scan 5 bài toán, chọn lens phù hợp, và biến ý tưởng rời rạc thành quick cards có actor, workflow, bottleneck, metric và kiến trúc.

### AI đã sai gì

AI có xu hướng làm nội dung quá rộng, liệt kê quá nhiều bài toán mà thiếu số đo cụ thể. Nếu không chốt scope, AI dễ làm bài bị loãng và lệch khỏi use case nhóm.

### Tôi đã sửa như thế nào

Tôi ép mỗi card phải có metric có số, bottleneck có thời gian, và chỉ giữ một phần bài toán gần với vận hành thực tế trong Vingroup.

## Thành viên 3 - Điền tên - Điền MSSV

### AI đã giúp gì

AI hỗ trợ tôi phản biện các ý tưởng về workflow và giúp so sánh mức phù hợp giữa Rule, LLM và Agent.

### AI đã sai gì

AI từng đề xuất dùng Agent tự động hóa quá nhiều bước, trong khi nhiều tác vụ chỉ cần LLM draft + duyệt tay là đủ.

### Tôi đã sửa như thế nào

Tôi chốt lại rằng các bài toán rủi ro cao phải giữ người duyệt cuối và giới hạn AI trong vai trò gợi ý, không ra quyết định thay con người.

## Thành viên 4 - Điền tên - Điền MSSV

### AI đã giúp gì

AI giúp tôi viết lại các bottleneck thành câu ngắn, rõ và gắn được với thời gian xử lý thực tế.

### AI đã sai gì

AI đôi khi mô tả workflow bằng ngôn ngữ quá chung chung, thiếu handoff giữa người và hệ thống nên khó dùng để vẽ diagram.

### Tôi đã sửa như thế nào

Tôi chuyển workflow thành từng bước tuần tự, chỉ rõ ai làm gì, mất bao lâu, và đâu là điểm tắc nghẽn.

## Thành viên 5 - Điền tên - Điền MSSV

### AI đã giúp gì

AI hỗ trợ tôi viết prompt prototype và thiết kế boundary kiểm tra tình huống nguy hiểm.

### AI đã sai gì

AI dễ gợi ý câu trả lời nghe hợp lý nhưng thiếu ràng buộc safety, ví dụ không tự chặn trường hợp pin quá thấp mà vẫn đề xuất trạm xa.

### Tôi đã sửa như thế nào

Tôi thêm rule cứng cho `[DRAFT_ONLY]`, pin dưới 5%, và action `dispatch_mobile_charger` để model không vượt boundary.

## Thành viên 6 - Điền tên - Điền MSSV

### AI đã giúp gì

AI giúp tôi review consistency giữa các file và tìm chỗ nội dung bị lệch khỏi use case chính.

### AI đã sai gì

AI có thể chấp nhận nội dung hợp lý về mặt câu chữ nhưng vẫn thiếu dữ kiện như metric, fallback hoặc HITL.

### Tôi đã sửa như thế nào

Tôi đối chiếu lại với rubric và worksheet, rồi bắt buộc mỗi phần phải có metric, ranh giới vận hành và mô tả rõ ai duyệt cuối.
