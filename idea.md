# AI-Enabled Accounting Services Platform
## Product, Operating Model & Automation Blueprint

**Phiên bản:** 1.0  
**Mục tiêu:** Xây dựng mô hình dịch vụ kế toán truyền thống nhưng được vận hành bằng automation + AI + human review, nhằm tăng năng suất, giảm sai sót, tăng tính minh bạch và nâng trải nghiệm khách hàng.

---

# 1. Executive Summary

Mô hình này **không phát minh ra một loại dịch vụ kế toán mới**.

Các dịch vụ vẫn là những dịch vụ thị trường đã quen thuộc:

- Kế toán thuế trọn gói
- Kế toán bán hàng
- Kế toán công nợ
- Payroll
- BHXH
- Kế toán mua hàng
- Kế toán kho
- Báo cáo quản trị
- Quyết toán thuế
- Thành lập/thay đổi/giải thể doanh nghiệp

Điểm khác biệt nằm ở **cách vận hành**.

Thay vì để kế toán viên thực hiện hầu hết thao tác bằng tay:

```text
Khách gửi chứng từ
        ↓
Kế toán đọc
        ↓
Kế toán nhập liệu
        ↓
Kế toán kiểm tra
        ↓
Kế toán hạch toán
        ↓
Kế toán đối chiếu
        ↓
Kế toán lập báo cáo
```

Mô hình mới chuyển thành:

```text
Khách gửi dữ liệu
        ↓
Automation thu thập
        ↓
AI đọc + phân loại
        ↓
Rule Engine kiểm tra
        ↓
Auto Reconciliation
        ↓
AI đề xuất xử lý
        ↓
Exception Queue
        ↓
Kế toán review
        ↓
Senior review
        ↓
Báo cáo / kê khai / phản hồi khách hàng
```

Triết lý cốt lõi:

> **Máy xử lý giao dịch bình thường. Con người xử lý ngoại lệ, judgement và trách nhiệm nghề nghiệp.**

Mục tiêu dài hạn:

> **80–90% nghiệp vụ chuẩn được xử lý tự động hoặc bán tự động; con người tập trung vào 10–20% exception.**

---

# 2. Product Vision

## 2.1. Khách hàng đang mua gì?

Khách hàng không mua:

- AI
- OCR
- workflow engine
- rule engine
- dashboard
- machine learning

Khách hàng mua:

- sổ sách đúng
- khai thuế đúng hạn
- giảm rủi ro
- biết còn thiếu chứng từ gì
- biết phải nộp bao nhiêu thuế
- biết khách nào chưa trả tiền
- biết tiền sắp phải chi
- được kế toán hỗ trợ khi có vấn đề

Do đó, tên sản phẩm ở phía khách hàng vẫn nên là:

> **Dịch vụ kế toán trọn gói**

hoặc:

> **Phòng kế toán thuê ngoài cho doanh nghiệp nhỏ**

Công nghệ là **engine ở phía sau**.

---

# 3. Strategic Positioning

## 3.1. Không cạnh tranh bằng việc phát minh nghiệp vụ mới

Không cần tạo ra những dịch vụ mà thị trường chưa hiểu.

Có thể cung cấp cùng loại dịch vụ với các công ty kế toán hiện tại, nhưng khác biệt ở:

- tốc độ
- automation
- kiểm soát
- chất lượng
- minh bạch
- chủ động
- trải nghiệm khách hàng
- khả năng scale

---

## 3.2. Positioning đề xuất

> **Dịch vụ kế toán trọn gói cho doanh nghiệp nhỏ, vận hành bằng công nghệ để xử lý nhanh hơn, kiểm tra liên tục, phát hiện thiếu sót sớm và giảm phụ thuộc vào thao tác thủ công.**

Không nên dùng positioning:

> AI Accounting Company

vì khách hàng SME thường không mua công nghệ.

Nên nói bằng outcome:

> **Thiếu chứng từ báo ngay. Thuế biết trước. Công nợ theo dõi liên tục. Báo cáo rõ ràng.**

---

# 4. Target Customer

## 4.1. Giai đoạn đầu

Nên tập trung vào doanh nghiệp dịch vụ nhỏ và rất nhỏ.

Đề xuất:

```text
Quy mô:
1–30 nhân sự

Đặc điểm:
- ít kho
- không sản xuất
- không BOM
- không costing phức tạp
- không nhiều chi nhánh
- chứng từ vừa phải
- nghiệp vụ tương đối chuẩn hóa
```

Ví dụ:

- công ty phần mềm
- agency
- marketing
- consulting
- giáo dục
- di trú
- thiết kế
- outsourcing
- professional services
- công ty thương mại nhỏ đơn giản

---

## 4.2. Không nên làm ngay từ đầu

- sản xuất
- xây dựng phức tạp
- nhà hàng chuỗi lớn
- logistics phức tạp
- warehouse nhiều tầng
- manufacturing costing
- đa pháp nhân
- consolidation
- import/export lớn
- project accounting rất phức tạp

Lý do:

> Không phải vì không làm được, mà vì chúng làm tăng số lượng exception và làm giảm tỷ lệ automation.

---

# 5. Service Catalog

Mô hình vẫn giữ các dịch vụ thị trường đang bán.

## 5.1. Core Services

### A. Kế toán thuế trọn gói

Bao gồm:

- tiếp nhận chứng từ
- kiểm tra hóa đơn
- ghi nhận doanh thu
- ghi nhận chi phí
- hạch toán
- lập sổ
- kê khai VAT
- PIT
- CIT
- báo cáo thuế
- báo cáo tài chính
- quyết toán
- theo dõi deadline

---

### B. Payroll

Bao gồm:

- danh sách nhân sự
- bảng công
- lương
- thưởng
- phụ cấp
- khấu trừ
- PIT
- payslip
- báo cáo payroll

---

### C. BHXH

Bao gồm:

- tăng giảm lao động
- hồ sơ BHXH
- theo dõi đóng BHXH
- đối chiếu BHXH
- các nghiệp vụ liên quan

---

### D. Kế toán bán hàng

Bao gồm:

- quotation
- contract
- order
- delivery/service completion
- invoice
- payment request
- revenue recognition
- AR

---

### E. Kế toán công nợ

Bao gồm:

- AR
- AP
- due date
- aging
- payment status
- overdue
- reconciliation
- payment reminder

---

### F. Kế toán mua hàng

Bao gồm:

- purchase document
- supplier
- invoice
- payment
- AP
- document completeness

---

### G. Kế toán kho

Giai đoạn sau:

- receipt
- issue
- balance
- stock count
- reconciliation

---

### H. Báo cáo quản trị

Bao gồm:

- doanh thu
- chi phí
- lợi nhuận
- cash position
- AR
- AP
- cashflow
- variance

---

### I. Quyết toán

Bao gồm:

- document completeness
- reconciliation
- anomaly review
- outstanding issues
- tax risk checklist

---

# 6. Core Operating Principle

Mỗi bước nghiệp vụ phải được phân vào một trong bốn nhóm.

```text
1. Automation
2. Rule Engine
3. AI
4. Human
```

---

# 7. Four-Layer Automation Model

## 7.1. Layer 1 — Automation

Automation phù hợp với việc:

- nhận file
- đổi tên file
- phân folder
- đồng bộ dữ liệu
- import
- export
- scheduling
- notification
- reminder
- task creation
- status update

Ví dụ:

```text
Email có attachment
        ↓
Download tự động
        ↓
Xác định khách hàng
        ↓
Lưu đúng workspace
        ↓
Tạo Document Record
        ↓
Đẩy vào processing queue
```

Không cần AI.

---

## 7.2. Layer 2 — Rule Engine

Rule phù hợp với logic deterministic.

Ví dụ:

```text
Invoice number duplicate
        ↓
FLAG_DUPLICATE
```

Hoặc:

```text
Bank payment > threshold
AND invoice missing
        ↓
MISSING_SUPPORTING_DOCUMENT
```

Hoặc:

```text
Invoice VAT = 10%
but total != subtotal + VAT
        ↓
CALCULATION_ERROR
```

Rule Engine phải là một thành phần first-class.

Không được dùng LLM thay cho tất cả business rule.

---

## 7.3. Layer 3 — AI

AI phù hợp với dữ liệu khó cấu trúc.

Ví dụ:

- OCR
- document classification
- field extraction
- contract understanding
- expense category suggestion
- GL suggestion
- anomaly explanation
- report summary
- question answering

AI nên trả về:

```json
{
  "suggestion": "...",
  "confidence": 0.91,
  "reason": "...",
  "source": [...]
}
```

AI không nên im lặng quyết định các nghiệp vụ có rủi ro cao.

---

## 7.4. Layer 4 — Human

Human bắt buộc ở:

- judgement
- nghiệp vụ chưa chắc chắn
- tax interpretation
- unusual transaction
- policy exception
- large amount
- material adjustment
- final filing
- senior review

Human role chuyển từ:

```text
DATA ENTRY
```

sang:

```text
REVIEW
EXCEPTION HANDLING
JUDGEMENT
APPROVAL
```

---

# 8. End-to-End Architecture

```text
                         CUSTOMER
                             │
          ┌──────────────────┼──────────────────┐
          │                  │                  │
        Zalo               Email              Portal
          │                  │                  │
          └──────────────────┼──────────────────┘
                             ↓
                    DOCUMENT INTAKE
                             │
                             ↓
                     PROCESSING QUEUE
                             │
          ┌──────────────────┼──────────────────┐
          ↓                  ↓                  ↓
        OCR             Classification      Extraction
          │                  │                  │
          └──────────────────┼──────────────────┘
                             ↓
                         RULE ENGINE
                             │
                             ↓
                    MATCH / RECONCILE
                             │
                             ↓
                         AI SUGGEST
                             │
                             ↓
                       RISK SCORING
                             │
               ┌─────────────┴─────────────┐
               ↓                           ↓
          AUTO-PROCESS                 EXCEPTION
                                           │
                                           ↓
                                     ACCOUNTANT
                                           │
                                           ↓
                                    SENIOR REVIEW
                                           │
                                           ↓
                           REPORT / TAX / CUSTOMER
```

---

# 9. Document Intake

Khách hàng không nên bị ép học portal.

Hệ thống cần nhận từ nhiều nguồn:

```text
Email
Zalo
Portal
Upload link
Google Drive
API
Bank data
E-invoice integration
```

Tất cả converging về:

```text
Unified Document Inbox
```

Mỗi document cần:

```text
document_id
customer_id
source
received_at
document_type
processing_status
confidence
accounting_period
review_status
```

---

# 10. Document Processing Pipeline

```text
NEW
 ↓
VIRUS_CHECK
 ↓
OCR
 ↓
CLASSIFY
 ↓
EXTRACT
 ↓
VALIDATE
 ↓
DUPLICATE_CHECK
 ↓
MATCH
 ↓
ACCOUNTING_SUGGESTION
 ↓
RISK_SCORE
 ↓
AUTO / REVIEW
```

---

# 11. Invoice Automation

Ví dụ hóa đơn đầu vào.

## 11.1. Extract

Hệ thống đọc:

```text
Seller
Tax code
Invoice no.
Invoice date
Description
Subtotal
VAT rate
VAT amount
Total
Currency
Payment information
```

---

## 11.2. Validate

Rule Engine kiểm:

```text
Missing field?
Duplicate?
Tax code format?
Amount correct?
VAT calculation correct?
Period correct?
Supplier known?
Contract available?
Bank payment available?
```

---

## 11.3. Suggest

AI có thể đề xuất:

```text
Expense Category:
Marketing Expense

GL Suggestion:
642

VAT:
Potentially deductible

Confidence:
93%
```

---

## 11.4. Human Review

Nếu confidence thấp:

```text
AI confidence < 90%
        ↓
ACCOUNTANT REVIEW
```

Nếu material:

```text
Amount > configured threshold
        ↓
SENIOR REVIEW
```

---

# 12. Bank Reconciliation Automation

Một trong các khu vực nên ưu tiên automation cao.

Input:

```text
Bank transactions
Invoices
Receipts
Payments
Contracts
AR/AP
```

Matching:

```text
Amount
Date
Counterparty
Reference
Invoice number
Description
```

Output:

```text
MATCHED
PARTIAL_MATCH
NO_MATCH
AMBIGUOUS
```

Workflow:

```text
Bank Transaction
      ↓
Auto Match
      ↓
┌─────┴──────┐
↓            ↓
Match       No Match
↓             ↓
Post         Exception Queue
```

---

# 13. Missing Document Detection

Đây là một differentiation rất mạnh.

Ví dụ:

```text
Bank:
-50,000,000 VND
Supplier: ABC
        ↓
No invoice
No contract
        ↓
Exception:
MISSING_SUPPORTING_DOCUMENT
```

System thông báo:

> Khoản thanh toán 50.000.000đ ngày 15/09 chưa có đủ chứng từ.

Không đợi cuối tháng.

---

# 14. Sales Accounting Automation

```text
Quotation
   ↓
Contract
   ↓
Delivery / Acceptance
   ↓
Invoice
   ↓
AR
   ↓
Collection
```

Automation:

- đọc hợp đồng
- extract giá trị
- extract payment term
- extract milestone
- nhắc invoice
- tạo receivable
- match payment
- overdue alert

Ví dụ:

```text
Contract:
Payment due = 15 days
        ↓
Invoice issued
        ↓
Due date generated
        ↓
Bank not matched
        ↓
17 days overdue
        ↓
ALERT
```

---

# 15. AR Automation

System tự động tạo aging:

```text
Customer A    20m    5 days
Customer B    80m    32 days ⚠
Customer C    35m    61 days ⚠⚠
```

Rules:

```text
> 30 days → Warning
> 60 days → High
> 90 days → Critical
```

Có thể hỗ trợ:

- auto reminder draft
- collection task
- owner alert

---

# 16. AP Automation

System theo dõi:

```text
Supplier
Invoice
Amount
Due date
Payment status
Supporting docs
```

Dashboard:

```text
7 ngày tới cần trả:
125,000,000
```

---

# 17. Payroll Automation

Input:

```text
Employee master
Attendance
Leave
Salary
Bonus
Allowance
Deduction
Tax profile
Insurance
```

Pipeline:

```text
Input
 ↓
Validation
 ↓
Payroll calculation
 ↓
PIT calculation
 ↓
BHXH calculation
 ↓
Anomaly detection
 ↓
HR / Accountant review
 ↓
Approve
 ↓
Payslip / payment file
```

AI/rules phát hiện:

```text
Salary +45% month-over-month
Unknown employee
Negative salary
Allowance unusually high
Missing tax code
```

---

# 18. Tax Workflow Automation

Không để kế toán tự nhớ deadline.

System quản lý:

```text
Customer
Tax type
Period
Deadline
Preparation status
Review status
Submission status
Payment status
```

Ví dụ:

```text
VAT Q3
Preparation     Done
Review          Done
Submit          Pending
Payment         Pending
Due             30/10
```

---

# 19. Continuous Accounting

Không nên đợi đến cuối tháng.

Traditional:

```text
Ngày 30
↓
gom dữ liệu
↓
kiểm tra
↓
phát hiện lỗi
```

New model:

```text
Ngày 01 → Ngày 30

Invoice   → Check
Bank      → Reconcile
Expense   → Check
Contract  → Check
Payment   → Check
AR/AP     → Monitor
```

Mục tiêu:

> Phát hiện vấn đề càng gần thời điểm phát sinh càng tốt.

---

# 20. Exception-Driven Accounting

Kế toán viên không nên xem mọi transaction.

Kế toán chỉ xem:

```text
Exception Queue
```

Ví dụ:

```text
Customer A
3 unmatched transactions
2 invoices duplicate
1 missing contract

Customer B
1 payroll anomaly

Customer C
2 tax validation failures
```

Đây là màn hình quan trọng nhất của internal platform.

---

# 21. Exception Model

Mỗi exception có:

```text
id
customer
type
severity
source
description
detected_at
owner
status
due_at
resolution
reviewer
audit_log
```

Severity:

```text
LOW
MEDIUM
HIGH
CRITICAL
```

---

# 22. Risk-Based Review

Không review mọi thứ như nhau.

Ví dụ:

```text
Risk Score =
Transaction Value
+ AI Confidence
+ Rule Violations
+ Counterparty Risk
+ Tax Impact
+ Historical Pattern
```

Flow:

```text
LOW
→ auto approve / sampling

MEDIUM
→ accountant review

HIGH
→ senior accountant

CRITICAL
→ senior + manager
```

---

# 23. Human Review Model

## Level 1 — Accountant

Xử lý:

- missing docs
- mapping
- mismatch
- common exception

## Level 2 — Senior Accountant

Xử lý:

- unusual accounting treatment
- material amount
- tax impact
- complex contract

## Level 3 — Chief Accountant / Tax Specialist

Xử lý:

- tax interpretation
- audit issue
- high-risk transaction
- authority response
- material adjustment

---

# 24. Internal Operations Platform

Đây là sản phẩm nên build trước Client Portal.

Dashboard:

```text
TODAY

Total Customers        72

Auto Processed        1,284
Need Review              68
High Risk                 9
Overdue Tasks             4
```

Customer view:

```text
ABC COMPANY

Documents
Received              52
Processed             47
Need review            3
Missing                2

Bank
Matched               91%
Unmatched               4

Tax
VAT                 READY
PIT                 REVIEW
CIT                 N/A

Exceptions
High                    1
Medium                  3
```

---

# 25. Client Portal

Portal phía khách nên cực đơn giản.

Không để khách thấy:

```text
Journal Entry
Chart of Accounts
General Ledger
Debit/Credit
```

Nên hiển thị:

```text
Tiền
Thuế
Công nợ
Chứng từ thiếu
Việc cần làm
Báo cáo
Hỏi kế toán
```

Ví dụ:

```text
THÁNG 09

Chứng từ
47/50 đã nhận

Thiếu:
- Bank statement
- Invoice ABC
- Contract XYZ

Thuế dự kiến
VAT: 14.2m
PIT: 2.8m

Khách đang nợ
82m

Quá hạn
35m

Việc cần xử lý
3
```

---

# 26. Customer Interaction Model

Không ép khách thay đổi hành vi.

Khách vẫn có thể dùng:

- Zalo
- email
- upload link
- portal

System đứng phía sau gom tất cả.

Nguyên tắc:

> **Công nghệ phải thích nghi với khách hàng, không bắt khách hàng thích nghi với công nghệ.**

---

# 27. AI Q&A

Owner có thể hỏi:

```text
Tháng này chi phí tăng vì sao?
```

AI trả lời dựa trên dữ liệu công ty:

```text
Chi phí tháng 9 tăng 18%.

Các khoản tăng chính:
Marketing       +42m
Legal           +18m
Salary          +12m
```

Hoặc:

```text
Khách nào nợ trên 30 ngày?
```

Hoặc:

```text
7 ngày tới tôi cần chi bao nhiêu?
```

RAG phải truy xuất từ:

- accounting data
- invoice
- bank
- AR/AP
- contract
- payroll
- reports

---

# 28. Audit Trail

Mọi thao tác quan trọng phải trace được.

Ví dụ:

```text
09:12
Invoice received

09:13
OCR completed

09:13
AI classified as marketing expense

09:13
Rule VAT_CHECK passed

09:14
Bank transaction matched

09:15
Auto suggestion created

10:40
Accountant approved

11:10
Senior reviewed
```

Không được để AI tạo thay đổi mà không trace.

---

# 29. Explainability

Mỗi AI suggestion phải trả lời được:

```text
Why?
Based on what?
Confidence?
Which document?
Which rule?
```

Ví dụ:

```text
Suggested Account:
Marketing Expense

Reason:
Description contains "Facebook Ads"
Supplier previously mapped to Marketing
6 similar transactions existed

Confidence:
96%
```

---

# 30. Confidence Threshold

Ví dụ:

```text
> 97%
Auto-process

90–97%
Accountant quick review

70–90%
Detailed review

< 70%
Manual processing
```

Không hardcode toàn bộ hệ thống.

Threshold phải config theo nghiệp vụ.

---

# 31. Automation KPI

Không nên đo số feature AI.

Nên đo:

## Operational

```text
Auto Processing Rate
Exception Rate
Manual Touch Rate
Average Review Time
Cost per Transaction
Transactions per Accountant
```

## Quality

```text
Error Rate
Rework Rate
Tax Adjustment Rate
Review Rejection Rate
Duplicate Detection Rate
Reconciliation Accuracy
```

## Customer

```text
Response Time
Missing Document Resolution Time
Monthly Close Time
Customer Retention
NPS
```

---

# 32. North Star Metric

Đề xuất:

> **Manual Touch Rate**

Công thức:

```text
Transactions requiring human intervention
-----------------------------------------
Total transactions
```

Ví dụ:

```text
Total: 10,000

Human touched: 1,500

Manual Touch Rate = 15%
```

Mục tiêu:

```text
Phase 1: 50%
Phase 2: 30%
Phase 3: 20%
Phase 4: 10–15%
```

Không được giảm touch rate bằng cách giảm kiểm soát.

---

# 33. Productivity KPI

Ví dụ:

Traditional:

```text
1 accountant
20–30 customers
```

Target:

```text
1 accountant
50–100 customers
```

Tùy complexity.

Không đặt con số cứng trước khi benchmark thực tế.

---

# 34. Unit Economics

Ví dụ giả định:

```text
80 customers
Average fee: 2.5m

Revenue:
200m / month
```

Nếu technology làm giảm:

```text
manual input
reconciliation
document chasing
report generation
```

thì cost phục vụ mỗi khách giảm.

Đó chính là lợi thế kinh tế.

---

# 35. Moat

Moat không phải model AI.

Các công ty khác cũng có thể dùng GPT/Claude/Gemini.

Moat thật sự là:

```text
Accounting workflow
+
Rule Library
+
Customer transaction patterns
+
Exception dataset
+
Human review process
+
Automation integrations
+
Historical resolutions
```

Sau một thời gian:

```text
Exception
    ↓
Human resolves
    ↓
Resolution captured
    ↓
Rule / AI improves
    ↓
Same exception appears less often
```

---

# 36. Accounting Knowledge Base

System nên có knowledge base:

```text
Accounting Rules
Tax Rules
Internal Policies
Customer-specific Rules
Industry Rules
Past Decisions
SOP
Review Checklist
```

Ví dụ:

```text
Rule:
If supplier = Facebook
AND description = ads
→ suggest Marketing Expense
```

Customer-specific:

```text
Customer ABC:
AWS invoices → Cloud Infrastructure
```

---

# 37. Customer Profile

Mỗi customer cần configuration riêng:

```text
Company profile
Industry
Tax method
Accounting method
Bank accounts
Invoice settings
Payroll settings
Chart mapping
Approval rules
Risk thresholds
Recurring vendors
Recurring customers
```

---

# 38. Workflow Engine

Không hardcode business process vào source code toàn bộ.

Workflow nên configurable.

Ví dụ:

```text
Invoice
 ↓
OCR
 ↓
Validation
 ↓
Match
 ↓
Review
 ↓
Approve
```

Customer khác:

```text
Invoice
 ↓
OCR
 ↓
Validation
 ↓
Department Approval
 ↓
Accounting Review
 ↓
Approve
```

---

# 39. Rule Engine

Các loại rule:

## Validation

```text
amount > 0
invoice_date valid
tax_code valid
```

## Accounting

```text
vendor category → GL suggestion
```

## Tax

```text
VAT condition
```

## Risk

```text
transaction > threshold
```

## Workflow

```text
high risk → senior approval
```

---

# 40. Initial MVP

Không làm tất cả ngay.

## Phase 1

Chỉ tập trung:

```text
1. Customer Management
2. Document Intake
3. OCR / Extraction
4. Invoice Processing
5. Bank Import
6. Auto Reconciliation
7. Exception Queue
8. Accountant Review
9. Tax Calendar
10. Client Status
```

Đây đã đủ tạo differentiation mạnh.

---

# 41. MVP Customer Flow

```text
Customer
   ↓
Send Invoice
   ↓
System receives
   ↓
OCR
   ↓
Validate
   ↓
Match Bank
   ↓
Suggest Accounting
   ↓
Accountant Review
   ↓
Processed
```

---

# 42. MVP Internal Screens

Cần tối thiểu:

```text
Dashboard
Customers
Documents
Transactions
Reconciliation
Exceptions
Tasks
Tax Calendar
Reports
Audit Logs
```

---

# 43. Không nên build quá sớm

Không cần ngay:

- custom ERP
- full inventory
- manufacturing
- project costing
- mobile native app
- custom video call
- CRM phức tạp
- advanced BI
- marketplace
- accounting software replacement

Mục tiêu:

> **Không replace phần mềm kế toán. Tối ưu service operation trước.**

---

# 44. Integration Strategy

Nền tảng nên đứng ở giữa:

```text
MISA / Accounting Software
Bank
E-Invoice
Email
Drive
Zalo
Payroll Source

        ↓

Accounting Automation Platform
```

Không cần build ledger engine hoàn chỉnh ngay nếu accounting software hiện tại đã xử lý tốt.

---

# 45. Human-in-the-Loop Design

Mọi AI action quan trọng nên hỗ trợ:

```text
Accept
Reject
Modify
Explain
Escalate
```

Human feedback được lưu lại.

Ví dụ:

```text
AI: Office Expense

Accountant:
Change → Marketing Expense

Feedback stored
```

---

# 46. Learning Loop

```text
AI suggestion
      ↓
Human correction
      ↓
Store feedback
      ↓
Update mapping / prompt / rule
      ↓
Next similar transaction
      ↓
Higher accuracy
```

Đây là learning system thực tế.

Không nhất thiết phải train model riêng.

---

# 47. Service Quality Model

Khách hàng cần SLA rõ.

Ví dụ:

```text
Document acknowledgment:
< 1 hour

Standard exception:
< 1 business day

High priority:
< 4 hours

Monthly close:
by day X

Report:
by day Y
```

SLA phải visible trên internal dashboard.

---

# 48. Continuous Controls

Hệ thống chạy controls hàng ngày.

Ví dụ:

```text
Duplicate invoice
Missing invoice
Unmatched bank
Invoice without contract
Payment without supporting docs
Overdue AR
Unusual expense
Payroll anomaly
Tax deadline
```

Output:

```text
CONTROL FAILED
```

thay vì đợi người nhớ kiểm tra.

---

# 49. Monthly Close Automation

```text
Period End
    ↓
Document completeness
    ↓
Bank reconciliation
    ↓
AR reconciliation
    ↓
AP reconciliation
    ↓
Payroll reconciliation
    ↓
Tax reconciliation
    ↓
Exception clearance
    ↓
Review
    ↓
Close
```

Dashboard:

```text
September Close

Documents      ✓
Bank           ✓
AR             ✓
AP             ✓
Payroll        ✓
Tax            !
Review         Pending

Close progress: 86%
```

---

# 50. Customer Experience

Khách hàng không nên hỏi:

> Kế toán làm tới đâu rồi?

Portal/status message đã trả lời.

Không nên hỏi:

> Thiếu gì?

System đã có checklist.

Không nên hỏi:

> Bao giờ đóng thuế?

System đã nhắc.

Không nên hỏi:

> Khách nào nợ tôi?

Dashboard đã có.

---

# 51. Pricing Logic

Không nhất thiết cạnh tranh bằng giá thấp.

Pricing có thể dựa trên:

```text
Base Fee
+
Transaction Volume
+
Employee Count
+
Service Modules
+
Complexity
```

Ví dụ:

```text
Accounting
+ Payroll
+ AR/AP
+ Management Report
```

Khách mua dịch vụ quen thuộc.

Technology giúp mình có margin cao hơn.

---

# 52. Go-to-Market

Không quảng cáo:

> "AI-powered autonomous accounting platform"

Nên quảng cáo:

> "Dịch vụ kế toán trọn gói cho doanh nghiệp nhỏ."

Sau đó differentiation:

```text
✓ thiếu chứng từ báo sớm
✓ theo dõi tiến độ rõ ràng
✓ công nợ cập nhật
✓ kiểm tra nhiều lớp
✓ giảm nhập liệu thủ công
✓ phản hồi nhanh
```

---

# 53. Initial Sales Proposition

Một proposition đơn giản:

> **Bạn vẫn có kế toán phụ trách như dịch vụ truyền thống, nhưng phía sau là hệ thống tự động theo dõi chứng từ, đối chiếu dữ liệu, phát hiện lỗi và nhắc việc liên tục.**

---

# 54. Competitive Strategy

Không cố thắng công ty lớn bằng:

```text
nhiều chi nhánh hơn
SEO mạnh hơn
giá rẻ hơn
dịch vụ nhiều hơn
```

Nên thắng bằng:

```text
Operational Excellence
Automation
Faster Close
Lower Error Rate
Better Visibility
Better Client Experience
```

---

# 55. Key Differentiators

## 1. Continuous Accounting

Không đợi cuối kỳ.

## 2. Exception-Driven Operation

Kế toán xử lý exception thay vì nhập liệu.

## 3. Automated Reconciliation

Giảm workload thủ công.

## 4. Missing Document Detection

Phát hiện sớm.

## 5. Human Review

Không để AI tự quyết định nghiệp vụ rủi ro.

## 6. Transparent Workflow

Khách biết trạng thái.

## 7. Management Insight

Owner nhìn được tiền, công nợ, thuế.

---

# 56. Security Principles

Dữ liệu kế toán rất nhạy cảm.

Bắt buộc:

```text
Tenant Isolation
Encryption at Rest
Encryption in Transit
RBAC
Audit Log
MFA
Least Privilege
Data Retention
Backup
Disaster Recovery
```

AI access phải theo:

```text
Customer Boundary
```

Không được rò dữ liệu giữa customers.

---

# 57. AI Security

Không đưa toàn bộ database thẳng vào model.

Nên có:

```text
AI Gateway
 ↓
Access Control
 ↓
Data Minimization
 ↓
Prompt Construction
 ↓
Model
```

PII/sensitive data cần policy riêng.

---

# 58. Data Architecture

Core entities:

```text
Customer
User
Employee
Supplier
Buyer
Document
Invoice
BankTransaction
Payment
Receipt
Contract
JournalSuggestion
Exception
Task
TaxPeriod
Report
AuditEvent
```

---

# 59. Event-Driven Model

Có thể thiết kế dạng event:

```text
DOCUMENT_RECEIVED
DOCUMENT_CLASSIFIED
DOCUMENT_EXTRACTED
VALIDATION_FAILED
TRANSACTION_MATCHED
EXCEPTION_CREATED
REVIEW_COMPLETED
TAX_READY
REPORT_READY
```

Ưu điểm:

- trace tốt
- automation dễ
- scalable
- integration dễ

---

# 60. Example Full Flow

Khách gửi hóa đơn qua email.

```text
EMAIL_RECEIVED
        ↓
Attachment extracted
        ↓
Customer detected
        ↓
DOCUMENT_RECEIVED
        ↓
OCR
        ↓
INVOICE_DETECTED
        ↓
Fields extracted
        ↓
Validation
        ↓
Duplicate check
        ↓
Bank matching
        ↓
Expense classification
        ↓
GL suggestion
        ↓
Risk score
        ↓
Low risk
        ↓
Accountant quick review
        ↓
Approved
        ↓
Accounting software sync
        ↓
Audit log
```

---

# 61. Example Exception Flow

```text
Payment:
30,000,000

No invoice
No contract

        ↓

Exception:
MISSING_DOCUMENT

Severity:
HIGH

        ↓

Accountant notified

        ↓

Customer notified

        ↓

Customer uploads invoice

        ↓

System auto re-runs validation

        ↓

Exception resolved
```

---

# 62. System Design Principle

Hệ thống không thay accountant.

Hệ thống thay:

```text
copy
paste
download
rename
lookup
match
compare
remind
check repeatedly
```

Accountant giữ:

```text
judgement
review
decision
communication
responsibility
```

---

# 63. Roadmap

## Phase 1 — Internal Efficiency

- intake
- OCR
- classify
- invoice
- bank
- reconciliation
- exception queue
- review

## Phase 2 — Customer Experience

- client portal
- tax status
- document checklist
- AR/AP
- notifications

## Phase 3 — AI Assistant

- Q&A
- report analysis
- anomaly explanation
- contract extraction

## Phase 4 — Advanced Automation

- auto processing
- risk-based review
- workflow optimization
- predictive cashflow

---

# 64. Build Order

Đề xuất thứ tự:

```text
1. Map nghiệp vụ
2. SOP chuẩn
3. Define inputs/outputs
4. Define rules
5. Define exceptions
6. Build internal workflow
7. Add automation
8. Add AI
9. Add client visibility
10. Optimize
```

Không bắt đầu bằng AI chatbot.

---

# 65. First Principle

Muốn automate một nghiệp vụ cần trả lời:

```text
Input là gì?
Output là gì?
Rule là gì?
Exception là gì?
Ai quyết định?
Risk là gì?
Evidence là gì?
```

Nếu chưa trả lời rõ 6 câu này thì chưa nên code.

---

# 66. Automation Assessment Matrix

Mỗi workflow cần bảng:

| Step | Input | Output | Rule | AI | Human | Risk |
|---|---|---|---|---|---|---|
| Receive invoice | File | Document | Yes | No | No | Low |
| OCR | Image/PDF | Fields | No | Yes | No | Low |
| Duplicate check | Invoice | Result | Yes | No | No | Medium |
| Expense classify | Content | Category | Partial | Yes | Review | Medium |
| VAT eligibility | Invoice | Result | Yes | Assist | Yes | High |
| GL mapping | Invoice | Account | Partial | Yes | Yes | Medium |
| Filing | Tax data | Submission | Yes | No | Approve | High |

---

# 67. Definition of Done cho một automated workflow

Một workflow chỉ coi là hoàn chỉnh khi có:

```text
Input
Output
Happy Path
Exception Path
Rules
AI behavior
Confidence threshold
Human reviewer
SLA
Audit log
Metrics
Fallback
```

---

# 68. Success Criteria

Business thành công khi đạt đồng thời:

```text
High automation
+
Low error rate
+
Fast response
+
Strong review
+
Satisfied customers
+
Positive unit economics
```

Không coi việc AI làm được nhiều là mục tiêu.

---

# 69. Final Product Philosophy

Sản phẩm không phải:

> "Một phần mềm kế toán mới."

Cũng không phải:

> "Một chatbot AI làm kế toán."

Sản phẩm là:

> **Một công ty dịch vụ kế toán được vận hành như một hệ thống phần mềm hiện đại.**

Phía khách hàng:

```text
Simple
Human
Reliable
Clear
```

Phía vận hành:

```text
Automated
Measured
Traceable
Exception-driven
AI-assisted
```

---

# 70. Final Architecture

```text
                          CUSTOMER
                              │
            ┌─────────────────┼─────────────────┐
            │                 │                 │
          Zalo              Email             Portal
            │                 │                 │
            └─────────────────┼─────────────────┘
                              ▼
                       INTAKE LAYER
                              │
                              ▼
                     DOCUMENT PLATFORM
                              │
            ┌─────────────────┼─────────────────┐
            ↓                 ↓                 ↓
           OCR          CLASSIFICATION       EXTRACTION
            │                 │                 │
            └─────────────────┼─────────────────┘
                              ▼
                         RULE ENGINE
                              │
                              ▼
                       RECONCILIATION
                              │
                              ▼
                         AI ASSISTANT
                              │
                              ▼
                        RISK ENGINE
                              │
                 ┌────────────┴─────────────┐
                 ↓                          ↓
              AUTO                     EXCEPTION
                                            │
                                            ▼
                                       ACCOUNTANT
                                            │
                                            ▼
                                     SENIOR REVIEW
                                            │
                    ┌───────────────────────┼───────────────────────┐
                    ↓                       ↓                       ↓
                 TAX                    REPORTING              CUSTOMER
```

---

# 71. Kết luận

Chiến lược không phải tạo thêm nghiệp vụ kế toán mới.

Chiến lược là:

```text
Lấy nghiệp vụ hiện có
        ↓
Chuẩn hóa
        ↓
Phân rã
        ↓
Automation
        ↓
Rule Engine
        ↓
AI
        ↓
Human Review
        ↓
Continuous Improvement
```

Giá trị lớn nhất nằm ở việc chuyển:

```text
MANUAL ACCOUNTING SERVICE
```

thành:

```text
TECH-ENABLED ACCOUNTING SERVICE
```

và cuối cùng thành:

```text
EXCEPTION-DRIVEN ACCOUNTING OPERATION
```

Khách hàng vẫn mua đúng dịch vụ họ đã hiểu từ trước.

Nhưng công ty vận hành bên trong hoàn toàn khác.

Đó chính là lợi thế cạnh tranh.
