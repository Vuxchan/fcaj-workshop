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

### Mục tiêu tuần 2:

* Nắm vững các khái niệm cốt lõi của AWS IAM: User, Group, Role và Policy.
* Thực hành các quy tắc bảo mật AWS: Quyền tối thiểu (Least Privilege), xác thực 2 lớp (MFA) và vai trò dịch vụ.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu tổng quan IAM: IAM User, IAM Group, Managed Policy và Inline Policy | 22/06/2026 | 22/06/2026 | <https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html> |
| 3 | - Tìm hiểu IAM Role & Trust Relationship (EC2 Service Role, truy cập cross-account) | 23/06/2026 | 23/06/2026 | <https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html> |
| 4 | - **Thực hành:** <br>&emsp; + Tạo IAM User, Group <br>&emsp; + Gán Policy tùy chỉnh bằng JSON <br>&emsp; + Cấu hình chính sách bắt buộc bật MFA | 24/06/2026 | 24/06/2026 | <https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html> |
| 5 | - **Thực hành:** <br>&emsp; + Tạo IAM Role cho EC2 truy cập S3 <br>&emsp; + Gắn IAM Role vào EC2 instance <br>&emsp; + Kiểm tra truy cập S3 từ EC2 không cần Hardcoded Access Key | 25/06/2026 | 25/06/2026 | <https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2.html> |
| 6 | - Tìm hiểu AWS Security Token Service (STS) và IAM Access Analyzer | 26/06/2026 | 26/06/2026 | <https://docs.aws.amazon.com/STS/latest/UsingSTS/welcome.html> |


### Kết quả đạt được tuần 2:

* Hiểu rõ cấu trúc JSON của một IAM Policy (Effect, Action, Resource, Condition).
* Tạo và gắn thành công IAM Role cho EC2 instance để truy cập an toàn tài nguyên S3 mà không cần lưu credentials cố định.
* Áp dụng nguyên tắc quyền tối thiểu và cấu hình chính sách bắt buộc xác thực 2 yếu tố (MFA).
