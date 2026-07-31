---
title: "Blog 2"
date: 2026-29-07
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Tối Ưu Hiệu Năng Storage Cho Amazon EKS Trên AWS Outposts

Với những ai đang triển khai hybrid cloud và có nhu cầu chạy Kubernetes ngay tại on-premises, thì Amazon EKS on Outposts chính là giải pháp mang trải nghiệm managed Kubernetes quen thuộc của AWS về tận datacenter của mình. Nhưng đi kèm với đó là bài toán không hề đơn giản: chọn loại storage nào cho phù hợp, vì mỗi loại lại có đặc tính hiệu năng và ràng buộc khác nhau. Bài viết này của AWS đi sâu vào các lựa chọn storage cho EKS on Outposts và cách tối ưu chúng.

## Trước tiên, EKS on Outposts có 2 kiểu triển khai

**Extended cluster** thì control plane vẫn nằm trên AWS Region, còn worker node chạy trên Outposts --- cần kết nối mạng ổn định về Region qua service link. **Local cluster** thì đưa luôn cả control plane xuống Outposts, giúp cluster hoạt động độc lập hơn, ít phụ thuộc kết nối về Region, và giảm latency cho các thao tác quản lý cluster.

## Vậy có những lựa chọn storage nào cho extended cluster?

### Amazon EBS

Là lựa chọn cho khối lượng công việc cần latency thấp, IOPS/throughput cao. Khi chạy trên Outposts, volume EBS được lưu ngay tại phần cứng local, nên hiệu năng vượt trội so với storage qua mạng, và không phụ thuộc kết nối ra ngoài. Điểm cần lưu ý: volume EBS bị "khóa" vào một rack và AZ cụ thể (rủi ro single point of failure), nên nhớ backup định kỳ bằng snapshot về Region, và theo dõi dung lượng vì capacity trên Outposts là hữu hạn.

### Amazon EFS

Phù hợp khi cần shared file system cho nhiều pod cùng truy cập --- ví dụ content management hay xử lý phân tán. Tuy nhiên khác với EBS, EFS không phải service chạy local trên Outposts, mà file system vẫn nằm ở Region, các worker node trên Outposts chỉ mount vào qua service link. Điều này đồng nghĩa sẽ có thêm latency mạng, throughput bị giới hạn bởi băng thông service link, phụ thuộc liên tục vào kết nối Region, và phát sinh thêm chi phí data transfer.

### Amazon S3 on Outposts

Cho phép lưu object storage ngay tại chỗ, dùng chung API với S3 thông thường, phù hợp cho các nhu cầu cần tuân thủ lưu trữ dữ liệu tại chỗ (data residency) như log, audit trail, hay dữ liệu y tế nhạy cảm. Một lưu ý kỹ thuật: nên dùng Access Point ARN thay vì bucket ARN khi tích hợp với EKS.

## Vậy nên chọn cái nào?

Về cơ bản: **EBS** cho khối lượng công việc cần latency thấp, throughput cao dạng block storage; **EFS** khi cần shared file system tuân thủ chuẩn POSIX; và **S3** khi cần object storage có khả năng mở rộng và tương thích API rộng rãi. Ngoài việc chọn đúng loại, còn cần chú ý sizing volume hợp lý, theo dõi usage thường xuyên, cấu hình CPU/memory request chính xác, và tận dụng auto scaling để cân bằng hiệu năng với chi phí.

## Về giám sát và bảo mật

Mỗi loại storage có bộ metric riêng cần theo dõi qua CloudWatch:

- **EBS**: IOPS, throughput, latency, burst balance
- **EFS**: I/O tổng, metadata operations, burst credit
- **S3**: request/error rate, latency, hiệu quả multipart upload

Về bảo mật, nên mã hóa dữ liệu ở cả 3 loại storage (dùng KMS cho EBS, encryption at rest/in transit cho EFS, server/client-side encryption cho S3), áp dụng IAM least privilege kết hợp Kubernetes RBAC để kiểm soát quyền truy cập ở mức pod.

## Tóm lại

EKS on Outposts mở ra khả năng xây dựng ứng dụng hybrid với nhiều lựa chọn storage khác nhau, tùy theo yêu cầu về hiệu năng, tuân thủ và data residency. Việc chọn đúng loại storage cho từng workload, kết hợp tận dụng hạ tầng local của Outposts, sẽ giúp giảm latency, giảm phụ thuộc mạng, và duy trì tính nhất quán giữa môi trường cloud và on-premises.

---

**Nguồn:** [AWS Compute Blog - Optimizing storage performance for Amazon EKS on AWS Outposts](https://aws.amazon.com/blogs/compute/optimizing-storage-performance-for-amazon-eks-on-aws-outposts/)

**Minh chứng:** <img src="/images/3-BlogsPosted/3.2-Blog2/blog2.png" 
     style="width: 70%; max-width: 600px; height: auto; border-radius: 8px; box-shadow: 0 6px 20px rgba(0,0,0,0.15); display: block; margin: 0 auto;">