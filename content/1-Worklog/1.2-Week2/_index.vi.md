---
title: "Worklog Tuần 2"
date: 2026-06-22
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
reportTableColumns:
  - Thứ
  - Công việc
  - Ngày hoàn thành
reportType: worklog
---

**Thời gian:** 15/06/2026 – 21/06/2026
**Chủ đề:** Xây dựng nền tảng lưu trữ, database và IAM bằng Terraform

## Mục tiêu tuần
- Xây dựng nền tảng lưu trữ, database và IAM bằng Terraform.
- Tiếp tục xây dựng CodExecute theo kiến trúc AWS serverless đã thiết kế.
- Ưu tiên Infrastructure as Code, bảo mật least privilege và khả năng tái tạo môi trường.

## Kế hoạch theo ngày

| Ngày | Công việc chính |
|---|---|
| Thứ 2 (15/06) | Tạo các S3 bucket cho frontend static files, testcases và user avatars bằng Terraform. |
| Thứ 3 (16/06) | Cấu hình Block Public Access, encryption, versioning/lifecycle phù hợp và bucket policy theo nguyên tắc least privilege. |
| Thứ 4 (17/06) | Tạo DynamoDB cho dữ liệu người dùng, bài toán và submission; xác định Partition Key, Sort Key và GSI cần thiết. |
| Thứ 5 (18/06) | Chọn On-Demand/Pay-per-request cho môi trường Dev và kiểm tra khả năng truy vấn theo các use case chính. |
| Thứ 6 (19/06) | Tạo IAM roles/policies riêng cho Lambda API Handler và Lambda Code Executor. |

## Kết quả dự kiến
- Có hạ tầng storage/database/IAM có thể tái tạo bằng Terraform và được kiểm tra theo nguyên tắc least privilege.
