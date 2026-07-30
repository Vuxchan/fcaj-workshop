---
title: "Thiết lập Amazon SQS"
date: 2026-07-30
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

# THIẾT LẬP AMAZON SQS CHO HÀNG ĐỢI CHẤM BÀI CODEXECUTE

Trong phần này, chúng ta ghi lại quá trình cấu hình **Amazon Simple Queue Service (SQS)** làm bộ đệm bất đồng bộ giữa **Lambda API** (`codeexecute-api`) và **Lambda Worker** (`codeexecute-worker`).

Khi người dùng bấm **SUBMIT**, Lambda API không thực thi code trực tiếp. Thay vào đó, nó đẩy một job chấm bài vào SQS queue, trả về kết quả ngay cho người dùng, và Lambda Worker sẽ được kích hoạt tự động để nhận và chấm bài bất đồng bộ.

```
Người dùng bấm SUBMIT
      │
      ▼
Lambda codeexecute-api
  ├─ Lưu Submission vào DynamoDB (Status: "Pending")
  └─ Đẩy job vào SQS Queue
              │
              ▼ (SQS Event Source Mapping)
      Lambda codeexecute-worker
        ├─ Đọc payload bài nộp từ SQS record
        ├─ Lấy testcases từ S3
        ├─ Thực thi code trong sandbox container
        └─ Cập nhật kết quả Submission vào DynamoDB
```

Payload SQS được API đẩy lên có dạng:
```json
{
  "submission_id": "...",
  "user_id": "...",
  "problem_id": "...",
  "language": "python|cpp|java|javascript",
  "code": "..."
}
```

#### Các bước thực hiện

1. [Tạo SQS Queue](5.7.1-create-queue/)
2. [Gắn SQS vào Lambda Worker (Event Source Mapping)](5.7.2-event-source-mapping/)
