---
title: "Worklog Tuần 4"
date: 2026-07-06
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
reportTableColumns:
  - Thứ
  - Công việc
  - Ngày hoàn thành
reportType: worklog
---

**Thời gian:** 29/06/2026 – 05/07/2026
**Chủ đề:** API Gateway, Lambda API Handler và xác thực

## Mục tiêu tuần
- API Gateway, Lambda API Handler và xác thực.
- Tiếp tục xây dựng CodExecute theo kiến trúc AWS serverless đã thiết kế.
- Ưu tiên Infrastructure as Code, bảo mật least privilege và khả năng tái tạo môi trường.

## Kế hoạch theo ngày

| Ngày | Công việc chính |
|---|---|
| Thứ 2 (29/06) | Chuẩn hóa backend API và xác định các endpoint chính cho users, problems và submissions. |
| Thứ 3 (30/06) | Đóng gói API Handler Lambda và cấu hình execution role bằng IAM. |
| Thứ 4 (01/07) | Tạo API Gateway REST API và kết nối các route với Lambda API Handler. |
| Thứ 5 (02/07) | Cấu hình CloudFront multi-origin routing: frontend mặc định qua S3 và `/api/*` chuyển tới API Gateway. |
| Thứ 6 (03/07) | Tích hợp/chuẩn bị luồng OAuth Google và GitHub; xác định callback và cách lưu thông tin người dùng. |

## Kết quả dự kiến
- Có API serverless hoạt động qua CloudFront/API Gateway và có nền tảng xác thực người dùng.