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

### Mục tiêu tuần 4:

* Tìm hiểu các dịch vụ lưu trữ AWS: Đối tượng (Amazon S3), Khối (Amazon EBS) và Tệp mạng (Amazon EFS).
* Thực hành tạo S3 Bucket, Versioning, host website tĩnh, tạo EBS Snapshot và mount EFS chia sẻ file giữa nhiều máy chủ.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu Amazon S3: Storage Classes, Bucket Policy, Versioning và tính năng Static Website Hosting | 06/07/2026 | 06/07/2026 | <https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html> |
| 3 | - Tìm hiểu loại ổ đĩa EBS (gp3, io2), kỹ thuật Snapshot và dịch vụ tệp mạng Amazon EFS | 07/07/2026 | 07/07/2026 | <https://docs.aws.amazon.com/efs/latest/ug/what-is-efs.html> |
| 4 | - **Thực hành:** <br>&emsp; + Tạo S3 Bucket, cấu hình Versioning & Lifecycle Rules <br>&emsp; + Host website tĩnh trên S3 và phân quyền Bucket Policy | 08/07/2026 | 08/07/2026 | <https://docs.aws.amazon.com/AmazonS3/latest/userguide/HostingWebsiteOnS3Setup.html> |
| 5 | - **Thực hành:** <br>&emsp; + Tạo EBS Snapshot <br>&emsp; + Nâng dung lượng EBS Volume trực tuyến và resize file system Linux | 09/07/2026 | 09/07/2026 | <https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-expansion.html> |
| 6 | - **Thực hành:** <br>&emsp; + Tạo hệ thống tệp Amazon EFS <br>&emsp; + Mount EFS vào 2 máy chủ EC2 đồng thời qua giao thức NFS để chia sẻ dữ liệu | 10/07/2026 | 10/07/2026 | <https://docs.aws.amazon.com/efs/latest/ug/mounting-fs.html> |


### Kết quả đạt được tuần 4:

* Thành thạo thao tác quản lý dữ liệu S3, tối ưu chi phí lưu trữ và triển khai web tĩnh trên S3.
* Nắm vững kỹ thuật sao lưu EBS Snapshot và tăng kích thước ổ cứng trực tuyến không gián đoạn dịch vụ.
* Cấu hình thành công ổ đĩa mạng EFS chia sẻ file giữa nhiều EC2 instances.
