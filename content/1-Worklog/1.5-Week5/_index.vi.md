---
title: "Worklog Tuần 5"
date: 2026-07-13
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
reportTableColumns:
  - Thứ
  - Công việc
  - Ngày hoàn thành
reportType: worklog
---

**Thời gian:** 06/07/2026 – 12/07/2026
**Chủ đề:** Xây dựng pipeline chấm bài bất đồng bộ với SQS và Lambda Worker

## Mục tiêu tuần
- Xây dựng pipeline chấm bài bất đồng bộ với SQS và Lambda Worker.
- Tiếp tục xây dựng CodExecute theo kiến trúc AWS serverless đã thiết kế.
- Ưu tiên Infrastructure as Code, bảo mật least privilege và khả năng tái tạo môi trường.

## Kế hoạch theo ngày

| Ngày | Công việc chính |
|---|---|
| Thứ 2 (06/07) | Thiết kế trạng thái submission: pending, running, accepted/wrong answer/runtime error/compile error và các trạng thái cần thiết. |
| Thứ 3 (07/07) | Khi user submit code, API Handler lưu metadata/code cần thiết vào DynamoDB và gửi execution job vào SQS. |
| Thứ 4 (08/07) | Tạo SQS queue và cấu hình Lambda Worker làm event source. |
| Thứ 5 (09/07) | Xây dựng Lambda Code Executor đọc message, lấy submission từ DynamoDB và testcase từ S3. |
| Thứ 6 (10/07) | Thiết kế payload/job metadata để worker có thể xử lý submission độc lập và có khả năng retry, cập nhật kết quả chấm về DynamoDB và để frontend có thể truy vấn trạng thái/kết quả. |

## Kết quả dự kiến
- Hoàn thành pipeline submit/chấm bài bất đồng bộ và có thể xử lý submission thông qua SQS-triggered worker.

