---
title: "Worklog Tuần 6"
date: 2026-07-20
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
reportTableColumns:
  - Thứ
  - Công việc
  - Ngày hoàn thành
reportType: worklog
---

**Thời gian:** 13/07/2026 – 19/07/2026
**Chủ đề:** Container sandbox, bảo mật và độ tin cậy của Code Executor

## Mục tiêu tuần
- Container sandbox, bảo mật và độ tin cậy của Code Executor.
- Tiếp tục xây dựng CodExecute theo kiến trúc AWS serverless đã thiết kế.
- Ưu tiên Infrastructure as Code, bảo mật least privilege và khả năng tái tạo môi trường.

## Kế hoạch theo ngày

| Ngày | Công việc chính |
|---|---|
| Thứ 2 (13/07) | Tạo Docker image cho môi trường thực thi code và đẩy image lên Amazon ECR. |
| Thứ 3 (14/07) | Cấu hình Lambda Code Executor sử dụng container image phù hợp với runtime thực thi. |
| Thứ 4 (15/07) | Thiết kế giới hạn thời gian, memory, output và xử lý compile/runtime error để tránh một submission làm ảnh hưởng worker. |
| Thứ 5 (16/07) | Tách testcase khỏi code submission; worker chỉ đọc testcase từ S3 bằng IAM role cần thiết. |
| Thứ 6 (17/07) | Kiểm tra retry của SQS, visibility timeout, duplicate message và tính idempotent của worker, kiểm tra các trường hợp lỗi: submission không tồn tại, testcase lỗi, code timeout, compile failure và Lambda failure. |

## Kết quả dự kiến
- Code Executor có môi trường container hóa, giới hạn tài nguyên và cơ chế xử lý lỗi/retry phù hợp.