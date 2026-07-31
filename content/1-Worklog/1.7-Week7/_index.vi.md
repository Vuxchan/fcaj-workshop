---
title: "Worklog Tuần 7"
date: 2026-07-27
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
reportTableColumns:
  - Thứ
  - Công việc
  - Ngày hoàn thành
reportType: worklog
---

**Thời gian:** 20/07/2026 – 26/07/2026
**Chủ đề:** Monitoring, alerting, tối ưu và kiểm thử hệ thống

## Mục tiêu tuần
- Monitoring, alerting, tối ưu và kiểm thử hệ thống.
- Tiếp tục xây dựng CodExecute theo kiến trúc AWS serverless đã thiết kế.
- Ưu tiên Infrastructure as Code, bảo mật least privilege và khả năng tái tạo môi trường.

## Kế hoạch theo ngày

| Ngày | Công việc chính |
|---|---|
| Thứ 2 (20/07) | Thiết lập CloudWatch Logs cho API Handler và Code Executor; thống nhất log format có submission/job ID. |
| Thứ 3 (21/07) | Tạo CloudWatch metrics/alarms cho Lambda errors, duration, throttles, SQS backlog và các chỉ số quan trọng. |
| Thứ 4 (22/07) | Thiết lập SNS topic và Lambda/SNS notification cho các cảnh báo cần thiết. |
| Thứ 5 (23/07) | Kiểm thử tải ở mức phù hợp với môi trường Dev và quan sát thời gian xử lý submission. |
| Thứ 6 (24/07) | Kiểm tra chi phí và các resource có nguy cơ phát sinh phí; bảo đảm không để NAT Gateway/tài nguyên không cần thiết chạy ngoài thời gian sử dụng. |

## Kết quả dự kiến
- Hệ thống có logging, monitoring, alerting cơ bản; các điểm yếu về bảo mật và chi phí được rà soát.