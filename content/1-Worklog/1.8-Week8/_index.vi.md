---
title: "Worklog Tuần 8"
date: 2026-08-03
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
reportTableColumns:
  - Thứ
  - Công việc
  - Ngày hoàn thành
reportType: worklog
---

**Thời gian:** 27/07/2026 – 02/08/2026
**Chủ đề:** Tích hợp cuối, tài liệu hóa, demo và hoàn thiện báo cáo

## Mục tiêu tuần
- Tích hợp cuối, tài liệu hóa, demo và hoàn thiện báo cáo.
- Tiếp tục xây dựng CodExecute theo kiến trúc AWS serverless đã thiết kế.
- Ưu tiên Infrastructure as Code, bảo mật least privilege và khả năng tái tạo môi trường.

## Kế hoạch theo ngày

| Ngày | Công việc chính |
|---|---|
| Thứ 2 (27/07) | Chạy kiểm thử end-to-end toàn hệ thống từ đăng nhập, xem bài, submit code đến nhận kết quả chấm. |
| Thứ 3 (28/07) | Kiểm tra các luồng lỗi và khả năng phục hồi: API error, SQS retry, Lambda failure, timeout và dữ liệu không hợp lệ. |
| Thứ 4 (29/07) | Hoàn thiện Terraform modules, variables, outputs và README để có thể dựng lại môi trường. |
| Thứ 5 (30/07) | Kiểm tra toàn bộ tài nguyên AWS, quyền IAM và cấu hình production/dev trước khi demo. |
| Thứ 6 (31/07) | Chụp screenshot các bước triển khai quan trọng: S3, CloudFront/OAC/WAF, API Gateway, Lambda/ECR, DynamoDB, SQS, CloudWatch và SNS, viết tài liệu kiến trúc, flow submit/chấm bài, data model, security và hướng dẫn chạy/deploy. |

## Kết quả dự kiến
- CodExecute có bản triển khai tích hợp hoàn chỉnh, tài liệu kỹ thuật, ảnh minh chứng và nội dung demo/báo cáo cuối kỳ.