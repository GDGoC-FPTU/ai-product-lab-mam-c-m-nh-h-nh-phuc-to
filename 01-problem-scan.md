mam-c-m-nh-h-nh-phuc-to - Pham Trung Kien - 2A202601986



| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | Vinmec | Time-consuming | Đặt lịch khám |
| 2 | VinFast | AI-upgrade | Kiểm tra lỗi xe |
| 3 | VinSchool | Repeatable | Chấm bài |
| 4 | Vinpearl | Stakeholder pain | Trả lời khách hàng |
| 5 | VinBus | AI-upgrade | Theo dõi hành khách |




```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                   │
│                                                             │
│ Bài toán (1 câu): AI-powered Smart Medical Appointment Scheduling │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [X] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Receptionists                          │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Patient requests an appointment ──> 2. Receptionist receives the request ──> 3.Check doctor availability ──> 4. Suggest available time slots and Confirm appointment ──> 5. Send confirmation via SMS/Email               │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Receptionists manually check doctors' schedules. (⏱ 8-10 phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Deploy an LLM-powered scheduling assistant │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Reduce scheduling time from 10 minutes to under 2 minutes; Automate 70% of appointment requests. │
│   VD: "Giảm thời gian soạn phản hồi từ 10 min ──> under 2 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [X] Rule  [X] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                     │
│                                                             │
│ Bài toán (1 câu): AI-assisted Vehicle Fault Diagnosis       │
│ Công ty thành viên: [X] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Vehicle owners                         │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Customer brings vehicle to service center ──> 2. Technician performs manual inspection ──> 3. Read diagnostic codes ──> 4. Inspect vehicle components and Identify fault ──> 5. Recommend repair solution                │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Manual inspection (⏱ 20 phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Use AI to Analyze vehicle sensor data and diagnostic codes and Assist technicians with troubleshooting. │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Achieve 95%+ fault detection accuracy and Reduce maintenance time by 30% │
│   VD: "Giảm thời gian soạn phản hồi từ 10 min ──> under 2 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [X] Agent │
└─────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): AI-powered Customer Service Assistant     │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [X] Vinpearl               │
│                                                             │
│ Ai đang đau (Actor)? Customers                              │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Customer submits an inquiry ──> 2. Customer service agent reviews the request ──> 3. Search for relevant information ──> 4. Compose a response ──> 5. Send the reply                                │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Large volume of repetitive inquiries. (⏱ 5–8 phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Deploy an AI chatbot capable of Answering frequently asked questions and Providing hotel and booking information.│
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Automatically resolve 80% of common inquiries and Reduce average response time to under 1 minute. │
│   VD: "Giảm thời gian soạn phản hồi từ 10 min ──> under 2 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [X] Agent │
└─────────────────────────────────────────────────────────────┘
```