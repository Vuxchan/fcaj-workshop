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

### Mục tiêu tuần 5:

* Tìm hiểu Cơ sở dữ liệu quan hệ (Amazon RDS), Cơ sở dữ liệu NoSQL (Amazon DynamoDB) và Bộ cân bằng tải (ALB).
* Thực hành tạo cơ sở dữ liệu RDS MySQL độ sẵn sàng cao, bảng DynamoDB và định tuyến lưu lượng với Application Load Balancer.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu Amazon RDS (Kiến trúc Multi-AZ, DB Subnet Group) và Amazon DynamoDB (Khóa chính Partition/Sort Key) | 13/07/2026 | 13/07/2026 | <https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html> |
| 3 | - Tìm hiểu Elastic Load Balancer (ELB): Application Load Balancer (ALB), Target Group và Listener Rules | 14/07/2026 | 14/07/2026 | <https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html> |
| 4 | - **Thực hành:** <br>&emsp; + Tạo DB Subnet Group và khởi tạo RDS MySQL ở Private Subnet <br>&emsp; + Kết nối ứng dụng EC2 vào RDS MySQL | 15/07/2026 | 15/07/2026 | <https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_VPC.WorkingWithRDSInstanceinaVPC.html> |
| 5 | - **Thực hành:** <br>&emsp; + Thử nghiệm RDS Multi-AZ failover & tạo DB Snapshot <br>&emsp; + Khởi tạo bảng DynamoDB và thực thi các lệnh CRUD dữ liệu qua Python SDK (boto3) | 16/07/2026 | 16/07/2026 | <https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html> |
| 6 | - **Thực hành:** <br>&emsp; + Dựng Application Load Balancer (ALB) ở Public Subnets <br>&emsp; + Đăng ký máy chủ EC2 vào Target Group và kiểm tra cân bằng tải HTTP | 17/07/2026 | 17/07/2026 | <https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html> |


### Kết quả đạt được tuần 5:

* Triển khai thành công cơ sở dữ liệu quan hệ bảo mật độ sẵn sàng cao (RDS MySQL Multi-AZ) trong phân vùng riêng tư.
* Nắm vững tư duy NoSQL và thao tác dữ liệu lập trình với Amazon DynamoDB SDK.
* Định tuyến và điều phối lưu lượng truy cập cân bằng giữa các máy chủ Web bằng Application Load Balancer.
