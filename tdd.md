# TDD — ACCOUNTING SERVICE OPERATING SYSTEM
## Thiết kế kỹ thuật theo hướng Domain-Discovery-First cho dịch vụ kế toán thuê ngoài

**Phiên bản:** 1.0  
**Trạng thái:** Proposed  
**Đối tượng đọc:** Founder/CTO, Accounting Lead, Product, Backend, Frontend, QA  
**Khách hàng mục tiêu ban đầu:** Doanh nghiệp dịch vụ nhỏ và rất nhỏ  
**Nguyên tắc cốt lõi:** Founder không cần biết toàn bộ kế toán trước khi build; hệ thống phải được xây từ workflow thật do Accounting Lead xác nhận.

---

# 1. Mục tiêu của tài liệu

Tài liệu này trả lời câu hỏi:

> **Một người mạnh về công nghệ nhưng không phải dân kế toán phải thiết kế và build hệ thống dịch vụ kế toán như thế nào mà không làm sai domain?**

Không bắt đầu từ `Database → API → UI → AI`.

Bắt đầu từ:

```text
Case thật
→ Workflow thật
→ Decision point
→ Rule
→ Human review
→ State transition
→ Data model
→ API
→ Code
```

---

# 2. Sản phẩm đang xây là gì?

Không xây phần mềm kế toán mới thay thế MISA/FAST ngay từ đầu.

Sản phẩm là:

> **Accounting Service Operating System — hệ thống vận hành dịch vụ kế toán thuê ngoài.**

Nó giúp công ty dịch vụ kế toán:

- tiếp nhận dữ liệu;
- quản lý chứng từ;
- hiểu nghiệp vụ;
- chuẩn bị bút toán;
- review;
- đối chiếu;
- chốt tháng;
- theo dõi deadline;
- hỏi khách đúng lúc;
- quản lý workload;
- tự động hóa phần việc lặp lại;
- giữ human accountability.

---

# 3. Separation of Responsibility

```mermaid
flowchart LR
    A[Case thực tế] --> B[Accounting Lead]
    B --> C[Workflow + Rule + Exception]
    C --> D[Founder / Product]
    D --> E[Technical Model]
    E --> F[Implementation]
    F --> G[Accounting UAT]
    G --> H{Đúng nghiệp vụ?}
    H -->|Không| B
    H -->|Có| I[Release]
```

**Accounting Lead chịu trách nhiệm:**

- xác nhận flow;
- xác nhận rule;
- phân loại risk;
- xác nhận acceptance criteria;
- test case thật.

**Founder/CTO chịu trách nhiệm:**

- state machine;
- data model;
- rule engine;
- workflow engine;
- AI orchestration;
- audit;
- observability;
- security;
- scalability.

---

# 4. Học domain theo case

Không học toàn bộ kế toán trước rồi mới code.

Mỗi feature bắt đầu bằng một case thật.

Ví dụ:

```text
Khách gửi hóa đơn AWS 22 triệu.
```

Cần hỏi Accounting Lead:

1. Nhận được chứng từ thì làm gì đầu tiên?
2. Kiểm tra các trường nào?
3. Làm sao biết chứng từ đủ điều kiện xử lý?
4. Xác định nghiệp vụ thế nào?
5. Khi nào tự xử lý được?
6. Khi nào hỏi khách?
7. Khi nào cần kế toán trưởng?
8. Output của bước này là gì?
9. Sau đó có cần đối chiếu ngân hàng không?
10. Khi nào case được coi là hoàn tất?

---

# 5. Scope

## In Scope

```text
Document intake
Accounting case
Client action
Review
Journal draft
Bank reconciliation
Month-end closing
Work queue
Audit trail
Basic reporting
Rule engine
AI assistance
```

## Out of Scope

```text
Full ERP
Inventory
Manufacturing costing
Full payroll engine
POS
Full tax engine
Multi-country accounting
Consolidation
Complex revenue recognition engine
Generic chatbot
```

---

# 6. Actors

```mermaid
flowchart TB
    OWNER[Chủ doanh nghiệp]
    STAFF[Nhân viên khách]
    ACC[Kế toán viên]
    SENIOR[Kế toán trưởng]
    MANAGER[Quản lý dịch vụ]
    SYS[Hệ thống]

    OWNER --> SYS
    STAFF --> SYS
    ACC --> SYS
    SENIOR --> SYS
    MANAGER --> SYS
```

**Client Owner**: xem status, action, report.  
**Client Staff**: upload chứng từ, trả lời yêu cầu.  
**Accountant**: xử lý case, review, reconcile, closing.  
**Senior Accountant**: high-risk review, closing approval.  
**Service Manager**: workload, deadline, SLA, capacity.

---

# 7. Backbone nghiệp vụ

```mermaid
flowchart LR
    A[Thu thập dữ liệu] --> B[Hiểu nghiệp vụ]
    B --> C[Chuẩn bị hạch toán]
    C --> D[Review]
    D --> E[Đối chiếu]
    E --> F[Chốt kỳ]
    F --> G[Báo cáo]
```

Toàn bộ hệ thống phải phục vụ backbone này.

---

# 8. Aggregate trung tâm — AccountingCase

`AccountingCase` = một vụ việc kế toán cần xử lý đến khi hoàn tất.

Case type:

```text
PURCHASE
SALE
BANK_TRANSACTION
PAYROLL
REFUND
MANUAL_ADJUSTMENT
MISSING_DOCUMENT
OTHER
```

---

# 9. State Machine

```mermaid
stateDiagram-v2
    [*] --> NEW
    NEW --> DATA_READY
    DATA_READY --> UNDERSTOOD
    UNDERSTOOD --> ACCOUNTING_PREPARED

    ACCOUNTING_PREPARED --> READY
    ACCOUNTING_PREPARED --> REVIEW_REQUIRED

    REVIEW_REQUIRED --> APPROVED
    REVIEW_REQUIRED --> REJECTED
    READY --> APPROVED

    APPROVED --> RECORDED
    RECORDED --> RECONCILED
    RECONCILED --> CLOSED

    DATA_READY --> WAITING_CLIENT
    UNDERSTOOD --> WAITING_CLIENT
    ACCOUNTING_PREPARED --> NEED_ACCOUNTANT
    ACCOUNTING_PREPARED --> NEED_SENIOR

    WAITING_CLIENT --> DATA_READY
    NEED_ACCOUNTANT --> UNDERSTOOD
    NEED_SENIOR --> REVIEW_REQUIRED
```

Ý nghĩa:

```text
NEW                  vừa tạo
DATA_READY           có đủ data cơ bản
UNDERSTOOD           hiểu nghiệp vụ là gì
ACCOUNTING_PREPARED  có phương án hạch toán nháp
REVIEW_REQUIRED      cần review
APPROVED             đã duyệt
RECORDED             đã ghi nhận vào system of record
RECONCILED           đã đối chiếu
CLOSED               hoàn tất
```

---

# 10. Event Model

State chỉ đổi vì event.

```text
CASE_CREATED
SOURCE_RECEIVED
DOCUMENT_PARSED
DOCUMENT_VALIDATED
CLASSIFICATION_COMPLETED
JOURNAL_DRAFT_CREATED
CLIENT_INFO_REQUESTED
CLIENT_RESPONDED
REVIEW_REQUESTED
REVIEW_APPROVED
RECORDED
BANK_MATCHED
CASE_CLOSED
```

```mermaid
flowchart TD
    E[Event] --> V[Validate Transition]
    V -->|Invalid| X[Reject]
    V -->|Valid| A[Apply Business Rule]
    A --> S[Update State]
    S --> O[Create Side Effects]
    O --> AU[Write Audit Event]
```

---

# 11. End-to-End tổng thể

```mermaid
flowchart TD
    A[Source Data] --> B[Document / Transaction]
    B --> C[Accounting Case]
    C --> D[Parse / Normalize]
    D --> E[Validate]
    E --> F{Đủ dữ liệu?}

    F -->|Không| G[Client Action]
    G --> H[WAITING_CLIENT]
    H --> I[Client Responds]
    I --> E

    F -->|Có| J[Understand Business Meaning]
    J --> K[Rule Engine]
    K --> L{Rule đủ chắc?}

    L -->|Có| M[Create Journal Draft]
    L -->|Không| N[AI Suggestion]
    N --> M

    M --> O[Risk Classification]
    O --> P{Risk Level}

    P -->|Low| Q[Accountant Review]
    P -->|Medium| Q
    P -->|High| R[Senior Review]

    Q --> S[Approve]
    R --> S

    S --> T[Record / Export]
    T --> U[Reconcile]
    U --> V[Closing]
    V --> W[Report]
```

---

# 12. Use Case 1 — Purchase Invoice

Ví dụ hóa đơn AWS 22 triệu.

```mermaid
flowchart TD
    A[Upload Invoice] --> B[Store Original]
    B --> C[Duplicate Check]
    C --> D[Extract]
    D --> E[Validate]
    E --> F{Valid?}

    F -->|No| G[Need Accountant / Client]
    F -->|Yes| H[Resolve Supplier]
    H --> I[Find Historical Mapping]
    I --> J{Known Mapping?}

    J -->|Yes| K[Create Journal Draft]
    J -->|No| L[Rule / AI Suggestion]
    L --> K

    K --> M[Validate Journal]
    M --> N[Risk Score]
    N --> O[Review]
    O --> P[Approve]
    P --> Q[Record to Accounting System]
    Q --> R[Wait for Bank Transaction]
    R --> S[Reconcile]
    S --> T[Case Closed]
```

---

# 13. Use Case 2 — Unknown Bank Transaction

```mermaid
flowchart TD
    A[Import Bank Transaction] --> B[Try Matching]
    B --> C{Match Found?}

    C -->|Yes| D[Suggest Match]
    D --> E[Review]
    E --> F[Confirm]
    F --> G[Reconciled]

    C -->|No| H[Create Accounting Case]
    H --> I[Accountant Review]
    I --> J{Accountant Understands?}

    J -->|Yes| K[Create Journal Draft]
    J -->|No| L[Create Client Action]
    L --> M[WAITING_CLIENT]
    M --> N[Client Responds]
    N --> K

    K --> O[Review]
    O --> P[Record]
    P --> G
```

---

# 14. Use Case 3 — Missing Document

```mermaid
flowchart TD
    A[Transaction Detected] --> B[Supporting Document Missing]
    B --> C[Create Client Action]
    C --> D[Notify Client]
    D --> E{Client Uploads?}

    E -->|No| F[Reminder / Escalation]
    F --> E

    E -->|Yes| G[Link Document]
    G --> H[Resume Accounting Case]
```

---

# 15. Use Case 4 — Month-End Closing

```mermaid
flowchart TD
    A[Start Closing] --> B[Document Completeness]
    B --> C[Bank Reconciliation]
    C --> D[AR Review]
    D --> E[AP Review]
    E --> F[Payroll Check]
    F --> G[Revenue Check]
    G --> H[Expense Check]
    H --> I[Tax Checklist]
    I --> J[Exception Review]
    J --> K{Blocker còn?}

    K -->|Có| L[Resolve Blocker]
    L --> J

    K -->|Không| M[Senior Review]
    M --> N[Approve Closing]
    N --> O[Period Closed]
```

---

# 16. ER Diagram

```mermaid
erDiagram
    TENANT ||--o{ TENANT_MEMBERSHIP : has
    USER ||--o{ TENANT_MEMBERSHIP : joins

    TENANT ||--o{ DOCUMENT : owns
    DOCUMENT ||--o{ DOCUMENT_VERSION : versions
    DOCUMENT ||--o| NORMALIZED_DOCUMENT : produces

    TENANT ||--o{ ACCOUNTING_CASE : owns
    ACCOUNTING_CASE ||--o{ CASE_EVENT : events
    ACCOUNTING_CASE ||--o{ REVIEW : reviews
    ACCOUNTING_CASE ||--o{ CLIENT_ACTION : actions
    ACCOUNTING_CASE ||--o| JOURNAL_DRAFT : prepares

    JOURNAL_DRAFT ||--o{ JOURNAL_DRAFT_LINE : lines

    TENANT ||--o{ PARTY : parties
    TENANT ||--o{ BANK_ACCOUNT : accounts
    BANK_ACCOUNT ||--o{ BANK_TRANSACTION : transactions
    BANK_TRANSACTION ||--o{ RECONCILIATION : reconciliations

    TENANT ||--o{ CLOSING_PERIOD : periods
    CLOSING_PERIOD ||--o{ CLOSING_TASK : tasks

    TENANT ||--o{ RULE : rules
    RULE ||--o{ RULE_VERSION : versions

    ACCOUNTING_CASE ||--o{ AI_SUGGESTION : suggestions
    TENANT ||--o{ AUDIT_EVENT : audit
```

---

# 17. Core Entities

## AccountingCase

```text
id
tenant_id
case_type
source_type
source_id
status
risk_level
assigned_to
period
priority
created_at
updated_at
```

Index:

```text
tenant_id + status
tenant_id + period
assigned_to + status
tenant_id + risk_level
```

## Document

```text
id
tenant_id
document_type
source
original_filename
mime_type
storage_key
sha256
status
uploaded_by
uploaded_at
```

## JournalDraft

```text
id
tenant_id
accounting_case_id
status
risk_level
source
created_by_type
created_at
```

JournalDraftLine:

```text
account_code
debit
credit
party_id
description
project_id
cost_center
```

---

# 18. Accounting Invariants

Luôn enforce bằng code:

```text
sum(debit) == sum(credit)
account tồn tại
account active
period open
amount hợp lệ
party có nếu bắt buộc
posted data không bị xóa im lặng
closed period không sửa bình thường
```

---

# 19. Rule Engine

Rule engine lưu kiến thức chắc chắn.

```yaml
id: KNOWN_VENDOR_AWS
version: 1

when:
  vendor_tax_code: "031..."
  document_type: PURCHASE_INVOICE

then:
  category: CLOUD_SERVICE
  suggested_account: "642"
  risk: LOW
```

Rule phải có:

```text
version
effective_from
effective_to
status
approved_by
audit
```

```mermaid
flowchart TD
    A[Case] --> B[Exact Rule]
    B --> C{Found?}
    C -->|Yes| D[Apply Rule]
    C -->|No| E[Historical Mapping]
    E --> F{Found?}
    F -->|Yes| G[Use Mapping]
    F -->|No| H[AI Suggestion]
    H --> I[Human Review]
```

---

# 20. AI Layer

AI chỉ xử lý ambiguity.

Phù hợp:

```text
document extraction
classification
semantic matching
anomaly explanation
client-friendly summary
```

Không dùng AI cho:

```text
arithmetic
permission
period locking
unique constraints
state transition rules
```

AI output bắt buộc structured:

```json
{
  "decision": "CLOUD_SERVICE",
  "confidence": 0.94,
  "evidence": [
    {
      "field": "description",
      "value": "AWS infrastructure services"
    }
  ]
}
```

```mermaid
flowchart LR
    A[Input] --> B[Prompt Registry]
    B --> C[AI Provider]
    C --> D[Structured Output]
    D --> E[Schema Validation]
    E --> F[Business Validation]
    F --> G[Suggestion]
    G --> H[Human Review]
```

---

# 21. Risk Engine

Risk inputs:

```text
amount deviation
new vendor
new category
foreign transaction
manual journal
tax-sensitive
missing document
related party
historical correction frequency
```

```mermaid
flowchart TD
    A[Risk Score] --> B{Risk}
    B -->|LOW| C[Accountant Fast Review]
    B -->|MEDIUM| D[Accountant Full Review]
    B -->|HIGH| E[Senior Review]
    E --> F{Approved?}
    D --> F
    C --> F
```

---

# 22. ClientAction

Các loại:

```text
UPLOAD_DOCUMENT
CONFIRM_TRANSACTION
ANSWER_QUESTION
APPROVE_INFORMATION
```

Fields:

```text
id
tenant_id
accounting_case_id
action_type
question
status
due_date
assigned_client_user
response
created_at
resolved_at
```

---

# 23. Work Queue

Ưu tiên:

```text
1. Critical overdue
2. Due today
3. High-risk review
4. Closing blocker
5. Normal tasks
```

```mermaid
flowchart TD
    A[All Open Work] --> B[Priority Engine]
    B --> C[Critical]
    B --> D[Due Today]
    B --> E[High Risk]
    B --> F[Closing Blocker]
    B --> G[Normal]
```

---

# 24. Internal Dashboard

Manager cần thấy:

```text
Active clients
Open cases
Waiting client
Review required
Closing at risk
Tax deadlines
Accountant capacity
SLA breaches
```

Ví dụ:

```text
50 active clients
17 waiting client
11 review required
4 closing at risk

Accountant A: 12 clients
Accountant B: 18 clients
Accountant C: 10 clients
```

---

# 25. Client Portal

MVP chỉ cần:

```text
Home
Documents
Actions
Reports
```

Bên trong hệ thống:

```text
VAT validation
journal draft
mapping
reconciliation
review
```

Khách chỉ thấy:

```text
Đã nhận
Đang xử lý
Cần bạn xử lý
Hoàn tất
```

---

# 26. System Architecture

```mermaid
flowchart TB
    subgraph UI
        CP[Client Portal]
        OP[Internal Operations]
    end

    subgraph APP[Modular Monolith]
        IAM[Identity/Tenant]
        DOC[Documents]
        CASE[Accounting Cases]
        ACC[Accounting]
        BANK[Banking]
        REV[Reviews]
        CA[Client Actions]
        CLOSE[Closing]
        RULE[Rules]
        AI[AI Orchestrator]
        REPORT[Reporting]
        AUDIT[Audit]
    end

    CP --> APP
    OP --> APP

    DOC --> OBJ[(Object Storage)]
    CASE --> DB[(PostgreSQL)]
    ACC --> DB
    BANK --> DB
    REV --> DB
    CA --> DB
    CLOSE --> DB
    RULE --> DB
    AI --> DB
    REPORT --> DB
    AUDIT --> DB

    AI --> LLM[AI Provider]
    ACC --> ADAPTER[Accounting Adapter]
    ADAPTER --> MISA[MISA / FAST / Other]
```

---

# 27. Tech Stack đề xuất

```text
Backend: Java 21 + Spring Boot + Gradle + jOOQ
Database: PostgreSQL
Frontend: React / Next.js / TypeScript
Storage: S3-compatible
Observability: OpenTelemetry + Prometheus + Grafana
Async MVP: PostgreSQL Outbox / Job Queue
Scale later: Kafka/SQS nếu cần
```

---

# 28. Backend Modules

```text
identity
tenants
clients
documents
cases
parties
accounting
banking
receivables
payables
reviews
client-actions
closing
workflow
rules
ai
reporting
integrations
audit
```

---

# 29. Async Processing + Outbox

```mermaid
sequenceDiagram
    participant API
    participant DB
    participant Worker
    participant AI

    API->>DB: Save Case + Outbox Event
    DB-->>API: Commit
    API-->>API: Return Response

    Worker->>DB: Read Outbox
    Worker->>AI: Process AI Task
    AI-->>Worker: Result
    Worker->>DB: Update Case
```

Các job chạy async:

```text
document extraction
AI calls
bank matching
report generation
anomaly scan
```

---

# 30. API Design

```http
POST /v1/documents
GET  /v1/documents/{id}

GET  /v1/accounting-cases/{id}
GET  /v1/accounting-cases?status=...

GET  /v1/work-items

POST /v1/reviews/{id}/decision

POST /v1/client-actions/{id}/response

POST /v1/closing-periods/{period}/start
POST /v1/closing-periods/{period}/approve
```

---

# 31. Multi-Tenancy

Mọi business table có:

```text
tenant_id
```

Tenant lấy từ authenticated context.

Không tin tenant ID gửi từ frontend.

Bắt buộc test:

```text
User tenant A không được đọc/ghi tenant B.
```

---

# 32. Audit Trail

AuditEvent:

```text
id
tenant_id
actor_type
actor_id
event_type
entity_type
entity_id
before_json
after_json
reason
timestamp
```

Audit bắt buộc cho:

```text
review
journal changes
rule changes
permission changes
closing
client response
AI suggestion
```

---

# 33. Security Baseline

```text
TLS
RBAC
MFA cho internal users
encrypted object storage
secret manager
signed URLs
audit log
backups
rate limiting
PII access control
```

Không gửi lên AI:

```text
password
bank credential
API secret
private key
authentication token
```

---

# 34. Data Ownership

Nguyên tắc:

> **Data belongs to customer.**

Phải có:

```text
export
access revoke
audit
retention policy
termination process
```

---

# 35. System of Record Strategy

Giai đoạn đầu:

```text
MISA / FAST / Existing System
=
System of Record
```

Our Platform:

```text
System of Work
+
System of Control
+
System of Intelligence
```

Không rebuild full accounting ledger quá sớm.

---

# 36. Accounting System Adapter

```java
interface AccountingSystemAdapter {

    List<Account> fetchAccounts();

    List<Party> fetchParties();

    List<JournalEntry> fetchJournalEntries(
        AccountingPeriod period
    );

    SyncResult syncApprovedDraft(
        JournalDraft draft
    );
}
```

MVP có thể import/export file trước, API integration sau.

---

# 37. Testing Strategy

## Unit

```text
rule engine
state transition
risk calculation
journal validation
```

## Integration

```text
database
storage
external adapters
AI schema validation
```

## E2E

```text
upload
→ case
→ classify
→ draft
→ review
→ record
→ reconcile
→ close
```

---

# 38. Accounting Acceptance Tests

Mỗi feature phải có acceptance test do Accounting Lead xác nhận.

Ví dụ:

```text
GIVEN:
AWS invoice 22m

WHEN:
system processes invoice

THEN:
- supplier resolved correctly
- total validated
- journal draft created
- risk LOW
- accountant review requested
- source document linked
```

Không release nếu chỉ pass technical test.

---

# 39. Golden Dataset

Case thật đã được senior xác nhận có thể trở thành golden record.

```text
input
expected classification
expected journal
expected risk
expected reviewer
reason
```

Dùng để regression test rule + AI.

---

# 40. Metrics

Technical:

```text
API p95
job latency
AI latency
AI schema failure
document processing time
error rate
```

Business/Operations:

```text
human_minutes_per_client
human_minutes_per_document
automation_rate
exception_rate
review_rate
closing_duration
client_response_time
rework_rate
clients_per_accountant
```

---

# 41. Definition of Done

Một automation feature chưa Done nếu thiếu:

```text
[ ] workflow nghiệp vụ được Accounting Lead xác nhận
[ ] state transition rõ
[ ] input/output rõ
[ ] rule rõ
[ ] exception rõ
[ ] human fallback
[ ] audit
[ ] permission
[ ] metrics
[ ] test case thật
[ ] acceptance test
```

---

# 42. MVP Roadmap

## Phase 0 — Domain Discovery

Chưa code automation.

Làm:

```text
20–50 case thật
workflow mapping
decision table
exception catalog
```

Output:

```text
Domain Playbook
```

## Phase 1 — Operational Backbone

```text
Tenant
User
Document
AccountingCase
Work Queue
ClientAction
Review
Audit
```

## Phase 2 — Document Intelligence

```text
XML parsing
PDF/image extraction
duplicate check
normalized document
classification
```

## Phase 3 — Accounting Assistance

```text
chart of accounts
party
rule engine
historical mapping
journal draft
validation
human review
```

## Phase 4 — Banking

```text
bank import
matching
reconciliation
unmatched queue
```

## Phase 5 — Closing

```text
closing period
closing checklist
blocker
senior review
close
```

## Phase 6 — Client Portal

```text
Home
Documents
Actions
Reports
```

---

# 43. Domain Discovery Workshop

Mỗi buổi 60–90 phút, chỉ xử lý **một case thật**.

Template:

```text
1. Trigger là gì?
2. Input là gì?
3. Accountant làm gì?
4. Quyết định gì?
5. Rule nào chắc chắn?
6. Exception nào hay gặp?
7. Khi nào hỏi khách?
8. Khi nào cần senior?
9. Output là gì?
10. Khi nào Done?
```

---

# 44. Decision Table

Ví dụ:

| Điều kiện | Kết quả |
|---|---|
| Vendor đã biết + amount bình thường + đủ chứng từ | LOW risk |
| Vendor mới + đủ chứng từ | MEDIUM |
| Foreign transaction | HIGH |
| Thiếu hợp đồng bắt buộc | WAITING_CLIENT |
| Không xác định được nghiệp vụ | NEED_ACCOUNTANT |

Mỗi bảng phải được Accounting Lead approve.

---

# 45. Exception Catalog

Exception là first-class concept.

```text
MISSING_DOCUMENT
UNKNOWN_PARTY
UNMATCHED_BANK_TRANSACTION
DUPLICATE_INVOICE
INVALID_TOTAL
CLOSED_PERIOD
HIGH_AMOUNT_DEVIATION
FOREIGN_TRANSACTION
MANUAL_JOURNAL
```

Mỗi exception có:

```text
severity
owner
resolution_flow
SLA
escalation
```

---

# 46. Domain Knowledge Registry

Không để knowledge nằm trong Zalo/chat.

Repo:

```text
docs/
└── accounting-domain/
    ├── purchase-invoice.md
    ├── sales-invoice.md
    ├── bank-reconciliation.md
    ├── closing.md
    ├── exceptions.md
    └── decisions/
```

---

# 47. Repository đề xuất

```text
accounting-os/
├── apps/
│   ├── backend/
│   └── web/
├── modules/
│   ├── documents/
│   ├── cases/
│   ├── accounting/
│   ├── banking/
│   ├── closing/
│   ├── reviews/
│   ├── client-actions/
│   ├── rules/
│   ├── ai/
│   └── audit/
├── docs/
│   ├── domain/
│   ├── architecture/
│   ├── adr/
│   └── api/
├── rules/
├── prompts/
├── schemas/
├── evals/
└── scripts/
```

---

# 48. ADR cần viết

```text
ADR-001 Modular Monolith
ADR-002 PostgreSQL
ADR-003 External System of Record
ADR-004 Human-in-the-loop
ADR-005 Rule Before AI
ADR-006 AccountingCase Aggregate
ADR-007 Immutable Audit
ADR-008 Rule Versioning
```

---

# 49. Sequence — Invoice Processing

```mermaid
sequenceDiagram
    participant Client
    participant API
    participant Case
    participant Worker
    participant Rule
    participant AI
    participant Accountant

    Client->>API: Upload invoice
    API->>Case: Create AccountingCase
    API-->>Client: Received

    Worker->>Case: Parse + validate
    Worker->>Rule: Find matching rule

    alt Rule found
        Rule-->>Worker: Accounting suggestion
    else No rule
        Worker->>AI: Request suggestion
        AI-->>Worker: Structured suggestion
    end

    Worker->>Case: Create JournalDraft
    Case->>Accountant: Review task
    Accountant->>Case: Approve / Correct
    Case-->>Client: Status updated
```

---

# 50. Sequence — Client Missing Info

```mermaid
sequenceDiagram
    participant System
    participant Accountant
    participant Client
    participant Case

    System->>Accountant: Exception detected
    Accountant->>Case: Confirm missing info
    Case->>Client: Create action
    Client->>Case: Submit response
    Case->>Accountant: Resume work
    Accountant->>Case: Continue processing
```

---

# 51. Sequence — Closing

```mermaid
sequenceDiagram
    participant Manager
    participant Closing
    participant Accountant
    participant Senior

    Manager->>Closing: Start period close
    Closing->>Accountant: Generate checklist
    Accountant->>Closing: Complete tasks
    Closing->>Closing: Validate blockers

    alt Blockers remain
        Closing-->>Accountant: Resolve blockers
    else Ready
        Closing->>Senior: Review
        Senior->>Closing: Approve
        Closing->>Closing: Mark CLOSED
    end
```

---

# 52. Component Diagram

```mermaid
flowchart LR
    UI[Web UI]

    UI --> API[Backend API]

    API --> CASE[Case Module]
    API --> DOC[Document Module]
    API --> ACC[Accounting Module]
    API --> BANK[Banking Module]
    API --> CLOSE[Closing Module]
    API --> REVIEW[Review Module]
    API --> RULE[Rule Module]
    API --> AI[AI Module]

    DOC --> S3[(Object Storage)]
    CASE --> PG[(PostgreSQL)]
    ACC --> PG
    BANK --> PG
    CLOSE --> PG
    REVIEW --> PG
    RULE --> PG
    AI --> PG

    AI --> MODEL[AI Provider]
    ACC --> EXT[Accounting Adapter]
```

---

# 53. Deployment Diagram

```mermaid
flowchart TB
    USER[Users]
    LB[Load Balancer]
    WEB[Web App]
    API[Backend]
    WORKER[Background Worker]
    DB[(PostgreSQL)]
    OBJ[(Object Storage)]
    AI[AI Provider]
    EXT[Accounting System]

    USER --> LB
    LB --> WEB
    WEB --> API
    API --> DB
    API --> OBJ
    API --> WORKER
    WORKER --> DB
    WORKER --> AI
    WORKER --> EXT
```

---

# 54. Failure Handling

**AI unavailable**

```text
retry limited
→ manual review queue
```

**Integration unavailable**

```text
store pending sync
→ retry
→ alert nếu quá SLA
```

**Document parsing failed**

```text
NEED_ACCOUNTANT
```

Workflow không được chết im lặng.

---

# 55. Quy tắc phát triển cuối cùng

Mọi feature mới phải bắt đầu bằng:

```text
Case thật
↓
Accounting Lead giải thích
↓
Workflow
↓
Decision Table
↓
Exception
↓
State Machine
↓
Acceptance Test
↓
Technical Design
↓
Code
```

Không được đảo ngược.

---

# 56. Kết luận

Hệ thống có thể được build bởi founder không phải dân kế toán nếu separation of responsibility rõ:

```text
Accounting Lead
= định nghĩa đúng nghiệp vụ

Founder/CTO
= biến nghiệp vụ thành hệ thống
```

Technical core:

```text
AccountingCase
+
State Machine
+
Rule Engine
+
Review
+
Client Action
+
Reconciliation
+
Closing
+
Audit
```

AI chỉ là lớp hỗ trợ.

> **Không code kế toán từ trí nhớ. Code workflow đã được domain expert xác nhận.**
