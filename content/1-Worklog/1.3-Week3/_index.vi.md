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

### Mục tiêu tuần 3:

* Hiểu mạng ảo Amazon VPC (Virtual Private Cloud) và các thành phần hạ tầng mạng cốt lõi.
* Nắm vững kỹ thuật phân chia CIDR, Public/Private Subnet, Internet Gateway, NAT Gateway, Route Table và bảo mật với Security Group & Bastion Host.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu cơ bản về VPC: IPv4 CIDR Block (`10.0.0.0/16`), quy hoạch chia Subnet (Public/Private Subnet đa vùng AZ) | 29/06/2026 | 29/06/2026 | <https://docs.aws.amazon.com/vpc/latest/userguide/configure-your-vpc.html> |
| 3 | - Tìm hiểu Internet Gateway (IGW) và Route Table (Định tuyến Local & Default `0.0.0.0/0`) | 30/06/2026 | 30/06/2026 | <https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html> |
| 4 | - **Thực hành:** <br>&emsp; + Khởi tạo Custom VPC <br>&emsp; + Phân chia 2 Public Subnet & 2 Private Subnet <br>&emsp; + Đính kèm Internet Gateway và cấu hình Public Route Table | 01/07/2026 | 01/07/2026 | <https://docs.aws.amazon.com/vpc/latest/userguide/vpc-subnets-routing.html> |
| 5 | - **Thực hành:** <br>&emsp; + Tạo NAT Gateway ở Public Subnet <br>&emsp; + Cấu hình Private Route Table trỏ traffic chiều ra qua NAT Gateway | 02/07/2026 | 02/07/2026 | <https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html> |
| 6 | - **Thực hành:** <br>&emsp; + Tạo Bastion Host ở Public Subnet <br>&emsp; + Thiết lập Security Groups và kết nối SSH an toàn tới máy chủ EC2 ở Private Subnet | 03/07/2026 | 03/07/2026 | <https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html> |


### Kết quả đạt được tuần 3:

* Thiết kế và xây dựng thành công hạ tầng Custom VPC đa vùng sẵn sàng (Multi-AZ) cô lập môi trường Public và Private.
* Cấu hình thành công Internet Gateway và NAT Gateway điều phối lưu lượng mạng chiều vào và chiều ra an toàn.
* Triển khai mô hình Bastion Host kết hợp Security Groups để quản trị các máy chủ nội bộ.
