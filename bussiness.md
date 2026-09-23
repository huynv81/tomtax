# BUSINESS DESIGN DOCUMENT
# Dịch vụ kế toán thuê ngoài ứng dụng AI cho doanh nghiệp dịch vụ nhỏ

## 1. Tóm tắt ý tưởng

Chúng ta không xây một phần mềm kế toán mới để cạnh tranh trực tiếp với MISA.

Chúng ta xây một **dịch vụ phòng kế toán thuê ngoài cho doanh nghiệp dịch vụ nhỏ và rất nhỏ**, được vận hành bằng quy trình chuẩn, phần mềm nội bộ và AI để giảm thao tác thủ công, tăng khả năng kiểm soát và phục vụ nhiều khách hàng hơn trên mỗi kế toán viên.

Khách hàng không mua AI. Khách hàng mua kết quả:

- không phải tự quản kế toán hằng ngày;
- biết tháng này đang làm tới đâu;
- biết còn thiếu gì;
- biết việc nào cần xử lý;
- giảm rủi ro bỏ sót deadline;
- có đầu mối chịu trách nhiệm.

AI và automation nằm phía sau để làm economics tốt hơn.

---

## 2. Bài toán khách hàng

Một doanh nghiệp dịch vụ rất nhỏ thường có hai lựa chọn.

### Tự thuê kế toán

Ưu điểm: có người nội bộ.

Nhược điểm:

- chi phí cố định;
- owner phải quản nhân sự;
- chất lượng phụ thuộc một người;
- khó tuyển người giỏi khi doanh nghiệp còn nhỏ.

### Thuê dịch vụ kế toán

Ưu điểm: rẻ hơn tuyển full-time.

Pain thường gặp:

- giao tiếp qua Zalo/email;
- chứng từ gửi rải rác;
- khó biết tiến độ;
- không biết tháng này còn thiếu gì;
- chỉ được hỏi khi gần deadline;
- phụ thuộc rất nhiều vào người phụ trách.

Vì vậy pain thật không chỉ là “hạch toán”.

Pain thật là:

> **Tôi không muốn phải tự quản hoạt động kế toán của công ty mình.**

---

## 3. Jobs To Be Done

Khách hàng thuê chúng ta để giải quyết bốn công việc.

### 3.1. Đừng để tôi sai

Bao gồm chứng từ, kê khai, hồ sơ, báo cáo và deadline.

### 3.2. Đừng để tôi mù

Owner phải nhìn được:

- tiến độ kế toán;
- hồ sơ còn thiếu;
- việc đang chờ mình;
- thuế dự kiến;
- công nợ cơ bản;
- vấn đề quan trọng.

### 3.3. Đừng bắt tôi quản kế toán

Không phải hỏi từng task, tự tìm file hay nhắc deadline.

### 3.4. Chỉ hỏi tôi khi thật sự cần

Nguyên tắc trải nghiệm:

```text
Normal case
→ hệ thống + kế toán tự xử lý

Exception
→ mới hỏi khách
```

---

## 4. Khách hàng mục tiêu ban đầu

Ideal Customer Profile:

```text
Doanh nghiệp dịch vụ
1–20 nhân sự
Doanh thu khoảng 1–30 tỷ/năm
10–200 chứng từ/tháng
1–3 tài khoản ngân hàng
Không sản xuất
Không tồn kho phức tạp
Không nhiều pháp nhân
Owner trực tiếp quản công ty
```

Ví dụ:

- agency;
- software outsourcing;
- consulting;
- design;
- education;
- immigration;
- marketing;
- professional services;
- small B2B services.

Nguyên tắc chiến lược:

> **Khách hàng đầu vào hẹp, nhưng accounting core phải đủ tổng quát.**

---

## 5. Khách chưa nên phục vụ

Giai đoạn đầu không ưu tiên:

- sản xuất;
- bán lẻ nhiều SKU;
- logistics phức tạp;
- xây dựng nhiều công trình;
- chuỗi F&B;
- tập đoàn nhiều pháp nhân;
- consolidation;
- costing phức tạp;
- khách có quá nhiều cash transaction.

Lý do: complexity tăng nhanh hơn doanh thu và phá khả năng chuẩn hóa.

---

## 6. Value Proposition

Không nên nói:

> Dịch vụ kế toán AI.

Nên nói:

> **Phòng kế toán thuê ngoài dành cho doanh nghiệp dịch vụ nhỏ — chủ động, minh bạch và ít việc cho chủ doanh nghiệp.**

Promise:

> **Anh/chị tập trung kinh doanh. Chúng tôi vận hành phần kế toán, chủ động báo cái gì đã xong, cái gì còn thiếu và việc nào cần anh/chị xử lý.**

---

## 7. Khác biệt với dịch vụ kế toán truyền thống

Mô hình truyền thống:

```text
Khách gửi chứng từ
↓
Kế toán xử lý
↓
Thiếu thì nhắn Zalo
↓
Cuối tháng/quý gửi kết quả
```

Mô hình của mình:

```text
Khách cung cấp dữ liệu
↓
Hệ thống theo dõi trạng thái
↓
Automation xử lý phần lặp lại
↓
Kế toán xử lý exception
↓
Khách chỉ nhận action cần thiết
↓
Luôn thấy tiến độ
```

Khác biệt nằm ở:

```text
LESS CUSTOMER EFFORT
+
MORE VISIBILITY
+
MORE PROACTIVE
+
MORE STANDARDIZED
```

---

## 8. Dịch vụ cốt lõi

Gói ban đầu:

1. Tiếp nhận và quản lý chứng từ.
2. Kiểm tra thiếu/trùng.
3. Hạch toán nghiệp vụ thông thường.
4. Đối chiếu ngân hàng cơ bản.
5. Theo dõi công nợ cơ bản.
6. Checklist thuế.
7. Chốt sổ tháng.
8. Báo cáo kế toán cơ bản.
9. Danh sách việc khách cần xử lý.
10. Hỗ trợ trao đổi nghiệp vụ.

Không cần bán CFO ngay từ đầu.

---

## 9. Service Ladder

```text
Accounting Operations
        ↓
AR/AP Control
        ↓
Cash Visibility
        ↓
Management Reporting
        ↓
Virtual Controller / CFO
```

Accounting là entry product. Giá trị cao hơn nằm ở các tầng trên.

---

## 10. Customer Journey

```text
Lead
↓
Qualification
↓
Báo giá
↓
Onboarding
↓
Monthly Operations
↓
Closing
↓
Monthly Review
↓
Renew / Upsell
```

Qualification phải kiểm tra:

- ngành;
- số chứng từ;
- số nhân sự;
- ngân hàng;
- software đang dùng;
- complexity;
- vấn đề tồn đọng.

---

## 11. Trải nghiệm khách hàng

Khách không cần thấy nghiệp vụ nội bộ.

Họ chỉ cần thấy:

```text
Kế toán tháng 09

Tiến độ: 82%
Cần bạn xử lý: 2
Thiếu chứng từ: 3
Thuế dự kiến: 18.5m
Dự kiến hoàn tất: 10/10
```

Action:

```text
1. Gửi hợp đồng ABC
2. Xác nhận giao dịch 18m
```

---

## 12. Operating Model

Không vận hành theo:

```text
1 kế toán
=
một nhóm khách
=
tự nhớ mọi việc
```

Mà theo:

```text
Workflow
+
Work Queue
+
Rule
+
Review
+
Escalation
```

Mỗi việc phải có:

```text
owner
status
deadline
risk
next action
```

---

## 13. Exception-Based Accounting

Đây là nguyên lý scale chính.

```text
Normal
→ automation chuẩn bị/xử lý

Exception
→ accountant xử lý

High Risk
→ senior xử lý
```

Mục tiêu dài hạn có thể là 80–90% case lặp lại được chuẩn hóa, nhưng tỷ lệ thật phải đo bằng pilot.

---

## 14. Vai trò của AI

AI hỗ trợ:

- đọc chứng từ;
- phân loại;
- matching;
- phát hiện bất thường;
- tìm dữ liệu thiếu;
- viết summary;
- gợi ý nghiệp vụ.

AI không phải người chịu trách nhiệm cuối cùng.

Business moat không phải model AI.

Moat là:

```text
workflow
+
rule library
+
historical corrections
+
accounting expertise
+
operating discipline
+
distribution
```

---

## 15. Portal khách hàng

Portal là công cụ giảm friction, không phải sản phẩm chính.

MVP chỉ cần:

```text
Home
Documents
Actions
Reports
```

Giá trị:

- giảm Zalo;
- giảm thất lạc;
- giảm support;
- tăng transparency.

---

## 16. Internal Operations quan trọng hơn Portal

Trong 6 tháng đầu, hệ thống nội bộ phải trả lời được:

```text
Khách nào trễ?
Ai đang phụ trách?
Khách nào thiếu chứng từ?
Ai đang quá tải?
Closing nào có nguy cơ trễ?
Có bao nhiêu exception?
```

Nếu internal operation chưa chuẩn thì portal chỉ là lớp giao diện đẹp.

---

## 17. Pricing Hypothesis

Chưa phải bảng giá chính thức.

### Micro

```text
1–5 người
<50 chứng từ/tháng
≈ 1–1.5 triệu/tháng
```

### Small

```text
5–20 người
50–200 chứng từ/tháng
≈ 2–4 triệu/tháng
```

Add-on:

- AR/AP control;
- cash reporting;
- management reporting;
- foreign transactions;
- payroll administration;
- complex tax advisory.

---

## 18. Logic định giá

Không chỉ dựa vào doanh thu.

```text
Base fee
+
Document volume
+
Bank accounts
+
Employee count
+
Complexity
+
Add-ons
```

Mục tiêu: khách hiểu được, nội bộ forecast margin được.

---

## 19. Unit Economics

Công thức:

```text
Revenue/client
-
Accountant labor
-
Senior review
-
AI/API
-
Infrastructure
-
Support
=
Contribution Margin
```

Ví dụ giả định:

```text
Revenue                2.5m
Accountant              700k
Senior review           200k
AI + infra              150k
Support                 250k
----------------------------
Contribution           1.2m
```

Đây chỉ là framework để đo, không phải forecast.

---

## 20. North Star Metric

> **Số khách hàng có thể được phục vụ an toàn trên mỗi kế toán viên.**

Supporting metrics:

- human minutes/client/month;
- human minutes/document;
- automation rate;
- exception rate;
- closing duration;
- rework rate;
- support contacts/client.

---

## 21. Khi nào automation tạo lợi thế?

Không phải khi AI demo hay.

Mà khi:

```text
Trước:
1 khách = 6 giờ kế toán/tháng

Sau:
1 khách = 2 giờ/tháng
```

trong khi:

```text
quality không giảm
risk không tăng
```

Đó mới là competitive advantage.

---

## 22. Sales Strategy

10 khách đầu nên đến từ:

- referral;
- network;
- partner luật/doanh nghiệp;
- cộng đồng startup;
- agency/software communities;
- content.

Mục tiêu 10 khách đầu là học, không phải scale.

---

## 23. Landing Page Message

Hero:

> **Phòng kế toán thuê ngoài cho công ty dịch vụ nhỏ.**

Subheadline:

> **Chúng tôi xử lý kế toán, theo dõi tiến độ và chủ động báo những việc anh/chị cần xử lý — không phải tự quản kế toán mỗi ngày.**

Không đưa AI thành headline.

---

## 24. Onboarding

```text
Contract / NDA
↓
Thông tin công ty
↓
Quyền truy cập dữ liệu
↓
Accounting software
↓
Bank process
↓
Opening data
↓
Setup checklist
↓
Assign accountant
↓
Go-live
```

---

## 25. Quality Model

Ba lớp:

```text
Automation / Rules
↓
Accountant
↓
Senior Review
```

Senior không review mọi thứ.

Senior chỉ xử lý:

- high-risk;
- tax-sensitive;
- unusual;
- closing review.

---

## 26. Knowledge Capture

```text
Kế toán trưởng sửa case
↓
Lưu correction + reason
↓
Tạo rule candidate
↓
Review
↓
Rule dùng lại cho nhiều khách
```

Đây là cách chuyển kinh nghiệm con người thành tài sản công ty.

---

## 27. Competitive Position

Không cạnh tranh với MISA bằng cách viết accounting software tốt hơn.

Không cạnh tranh với accounting firm bằng cách rẻ nhất.

Cạnh tranh bằng:

```text
less effort
more proactive
clearer status
faster operations
standardized quality
```

---

## 28. Trust Strategy

Khách phải hiểu:

- dữ liệu thuộc khách hàng;
- khách quyết định quyền truy cập;
- không bắt migrate khỏi hệ thống hiện tại;
- có audit trail;
- có data export;
- quyền có thể bị thu hồi.

Trust là business requirement.

---

## 29. Data Strategy

Giai đoạn đầu:

```text
MISA / FAST / Existing Software
=
System of Record

Our Platform
=
System of Work
+
System of Control
+
System of Intelligence
```

Không rebuild ledger quá sớm.

---

## 30. 10 khách đầu tiên

Mục tiêu:

```text
không scale
không tối ưu doanh thu
không build quá nhiều
```

Mục tiêu thật:

- hiểu workflow;
- đo thời gian;
- phát hiện exception;
- tìm automation opportunity;
- hiểu customer communication;
- xác định willingness-to-pay.

---

## 31. Pilot Metrics

Mỗi khách đo:

```text
document count
human hours
questions to client
missing documents
exception count
closing days
support interactions
rework
monthly fee
```

Pilot ít nhất vài chu kỳ kế toán mới đủ dữ liệu.

---

## 32. Go / No-Go

Tín hiệu tốt:

```text
khách renew
khách referral
human time/client giảm
workflow lặp lại
automation xử lý normal case
support không tăng tuyến tính
```

Tín hiệu xấu:

```text
mỗi khách là một custom project
accountant vẫn làm gần như thủ công
support quá nhiều
willingness-to-pay thấp
quality khó kiểm soát
```

Nếu xấu, đổi ICP/service design trước khi build tiếp.

---

## 33. Roadmap Business 6 tháng

### Tháng 1

5 khách pilot, manual-first, ghi lại toàn bộ workflow.

### Tháng 2

Chuẩn hóa intake, checklist, work queue.

### Tháng 3

Automate document processing và client actions.

### Tháng 4

Accounting suggestions và rule library.

### Tháng 5

Bank reconciliation và closing workflow.

### Tháng 6

Đo unit economics, chốt ICP, chốt pricing và quyết định scale.

---

## 34. Roadmap tăng trưởng

```text
0–10 khách
→ learn

10–30
→ standardize

30–100
→ automate

100–300
→ prove economics

300+
→ distribution + scale
```

---

## 35. Team ban đầu

```text
Founder / Product / Tech
Accounting Lead
1 accountant
```

Sau traction:

```text
additional accountant
customer success
engineering
```

Không cần đội sales lớn ngay.

---

## 36. Rủi ro chính

1. Giá thị trường quá thấp.
2. Mỗi khách quá custom.
3. Khách không tin đưa dữ liệu.
4. Automation sai.
5. Chất lượng phụ thuộc con người.
6. Điều kiện pháp lý của dịch vụ kế toán.
7. Phụ thuộc integration bên thứ ba.

---

## 37. Những thứ không build sớm

```text
full ERP
full accounting ledger
mobile app
chat platform
advanced CFO dashboard
multi-country tax
payroll engine
inventory
generic AI chatbot
```

Tất cả đều làm chậm business validation.

---

## 38. MVP Business Offer

> **Dịch vụ kế toán trọn gói cho doanh nghiệp dịch vụ nhỏ, với quy trình số hóa giúp khách luôn biết tiến độ, thiếu gì và cần làm gì.**

Bao gồm:

- bookkeeping;
- document control;
- tax workflow;
- bank reconciliation;
- monthly closing;
- basic reports;
- customer action list.

---

## 39. Ba promise ban đầu

```text
1. Anh/chị không cần tự theo dõi kế toán mỗi ngày.

2. Thiếu gì, chúng tôi chủ động báo.

3. Mỗi kỳ, anh/chị biết rõ kế toán đã hoàn thành đến đâu.
```

---

## 40. Mối quan hệ Business → Technical

Business document trả lời:

```text
Ai mua?
Tại sao mua?
Mua gì?
Giá thế nào?
Dịch vụ vận hành ra sao?
Thắng đối thủ bằng gì?
Economics có ổn không?
```

Technical document trả lời:

```text
Software hỗ trợ mô hình đó thế nào?
Workflow?
State?
Data?
Rule?
AI?
API?
Database?
```

Thứ tự phải là:

```text
BUSINESS
↓
OPERATIONS
↓
PRODUCT
↓
TECHNOLOGY
```

---

# Kết luận

Thứ mình xây gồm ba lớp:

```text
SERVICE
+
OPERATING SYSTEM
+
AUTOMATION
```

Trong đó:

```text
Service
→ thứ khách mua

Operating System
→ thứ giúp đội kế toán vận hành nhất quán

AI / Automation
→ thứ làm unit economics tốt hơn
```

Nếu chỉ có service thì khó scale.

Nếu chỉ có software thì khách nhỏ vẫn phải tự làm.

Nếu chỉ có AI thì không có accountability.

Ba phần kết hợp mới tạo thành business model.

> **Chiến lược: bắt đầu bằng dịch vụ kế toán đơn giản cho một nhóm doanh nghiệp dịch vụ nhỏ rõ ràng, dùng công nghệ để vận hành tốt hơn, sau đó mới mở rộng lên Finance Operations và các dịch vụ có giá trị cao hơn.**
