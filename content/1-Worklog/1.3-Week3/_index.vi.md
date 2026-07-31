---
title: "Worklog Tuần 3"
date: 2026-06-29
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
reportTableColumns:
  - Thứ
  - Công việc
  - Ngày hoàn thành
reportType: worklog
---

**Thời gian:** 22/06/2026 – 28/06/2026
**Chủ đề:** Triển khai Frontend trên S3 và CDN CloudFront

## Mục tiêu tuần
- Triển khai Frontend trên S3 và CDN CloudFront.
- Tiếp tục xây dựng CodExecute theo kiến trúc AWS serverless đã thiết kế.
- Ưu tiên Infrastructure as Code, bảo mật least privilege và khả năng tái tạo môi trường.

## Kế hoạch theo ngày

| Ngày | Công việc chính |
|---|---|
| Thứ 2 (22/06) | Build frontend production và xác định các static assets cần đưa lên S3. |
| Thứ 3 (23/06) | Cấu hình S3 làm origin cho frontend và sử dụng Origin Access Control (OAC) để hạn chế truy cập trực tiếp. |
| Thứ 4 (24/06) | Tạo CloudFront distribution cho frontend, cấu hình HTTPS, caching và default root object. |
| Thứ 5 (25/06) | Cấu hình AWS WAF ở CloudFront để có lớp bảo vệ cơ bản cho public endpoint. |
| Thứ 6 (26/06) | Thiết kế SPA routing/fallback để các route như `/login`, `/problems` và `/submissions` hoạt động đúng khi refresh. |

## Kết quả dự kiến
- Frontend được phục vụ qua CloudFront, S3 không public trực tiếp và SPA routing hoạt động ổn định.