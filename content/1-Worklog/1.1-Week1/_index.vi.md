---
title: "Worklog Tuần 1"
date: 2026-06-15
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
reportTableColumns:
  - Thứ
  - Công việc
  - Ngày hoàn thành
reportType: worklog
---

**Thời gian:** 08/06/2026 – 14/06/2026
**Chủ đề:** Khởi động dự án và chuẩn bị môi trường AWS / IaC

## Mục tiêu tuần
- Khởi động dự án và chuẩn bị môi trường AWS / IaC.
- Tiếp tục xây dựng CodExecute theo kiến trúc AWS serverless đã thiết kế.
- Ưu tiên Infrastructure as Code, bảo mật least privilege và khả năng tái tạo môi trường.

## Kế hoạch theo ngày

| Ngày | Công việc chính |
|---|---|
| Thứ 2 (08/06) | Thống nhất phạm vi và mục tiêu của dự án CodExecute, rà soát kiến trúc tổng thể: CloudFront/WAF, S3, API Gateway, Lambda, ECR, SQS, DynamoDB và các bucket testcase/avatar. |
| Thứ 3 (09/06) | Thiết lập AWS account, AWS CLI, region `ap-southeast-1`, IAM và AWS Budgets/cảnh báo chi phí. |
| Thứ 4 (10/06) | Khởi tạo repository và cấu trúc source code cho frontend, backend, Lambda worker và Terraform. |
| Thứ 5 (11/06) | Thiết kế sơ bộ các tài nguyên Terraform và quy ước đặt tên/tag cho môi trường Dev. |
| Thứ 6 (12/06) | Thiết kế dữ liệu ban đầu cho Users, Problems, Submissions và các thực thể cần thiết trong DynamoDB. |

## Kết quả dự kiến
- Hoàn thiện môi trường phát triển, sơ đồ kiến trúc CodExecute và bản thiết kế IaC/data model ban đầu.
