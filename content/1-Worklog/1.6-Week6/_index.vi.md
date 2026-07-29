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

### Mục tiêu tuần 6:

* Tìm hiểu tự động mở rộng nhóm EC2 (Auto Scaling Group), kiến trúc Serverless (AWS Lambda & API Gateway) và Cơ sở hạ tầng dưới dạng Mã nguồn (IaC).
* Thực hành cấu hình chính sách mở rộng máy chủ tự động, tích hợp Serverless API và viết mẫu CloudFormation tự động dựng hạ tầng.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu EC2 Auto Scaling Group (ASG): Launch Template, Dynamic Scaling Policy và Health Check | 20/07/2026 | 20/07/2026 | <https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html> |
| 3 | - Tìm hiểu kiến trúc Serverless (AWS Lambda, API Gateway REST API) và hạ tầng dạng mã IaC (CloudFormation/Terraform) | 21/07/2026 | 21/07/2026 | <https://docs.aws.amazon.com/lambda/latest/dg/welcome.html> |
| 4 | - **Thực hành:** <br>&emsp; + Tạo Launch Template chứa script cài đặt Web Server <br>&emsp; + Tạo nhóm ASG trên 2 AZ liên kết với ALB Target Group | 22/07/2026 | 22/07/2026 | <https://docs.aws.amazon.com/autoscaling/ec2/userguide/attach-load-balancer-asg.html> |
| 5 | - **Thực hành:** <br>&emsp; + Viết hàm Lambda (Python) xử lý truy vấn dữ liệu <br>&emsp; + Tạo HTTP endpoint qua API Gateway tích hợp với Lambda | 23/07/2026 | 23/07/2026 | <https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-lambda-proxy-integrations.html> |
| 6 | - **Thực hành:** <br>&emsp; + Viết CloudFormation Template (YAML) khởi tạo tự động VPC và máy chủ EC2 <br>&emsp; + Deploy Stack bằng AWS CLI | 24/07/2026 | 24/07/2026 | <https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html> |


### Kết quả đạt được tuần 6:

* Xây dựng nhóm máy chủ EC2 tự động phục hồi (Auto-Healing) và tự động mở rộng theo nhu cầu lưu lượng.
* Xây dựng thành công dịch vụ Web API không máy chủ (Serverless) bằng API Gateway, Lambda và DynamoDB.
* Tự động hóa quá trình dựng tài nguyên đám mây bằng mẫu CloudFormation YAML.
