---
title: "Các bài blogs đã đăng"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
includeInReport: false
---

### [Blog 1 - NÂNG CAO TRẢI NGHIỆM TEST LOCAL CHO ỨNG DỤNG SERVERLESS VỚI LOCALSTACK](3.1-Blog1/)
Bài viết giới thiệu LocalStack và tích hợp với AWS Toolkit cho VS Code, giúp lập trình viên test và debug ứng dụng serverless (Lambda, SQS, DynamoDB, EventBridge) hoàn toàn trên local mà không cần deploy lên cloud. Bài viết đề cập đến setup tự động, quy trình debug, và chiến lược test phân lớp (unit test → integration test với LocalStack → validation cuối trên cloud thật).

### [Blog 2 - TỐI ƯU HIỆU NĂNG STORAGE CHO AMAZON EKS TRÊN AWS OUTPOSTS](3.2-Blog2/)
Bài viết cung cấp hướng dẫn toàn diện về lựa chọn và tối ưu storage cho EKS on Outposts. So sánh 3 loại storage (EBS, EFS, S3 on Outposts), phân tích đặc tính hiệu năng và ràng buộc của từng loại, kèm theo khuyến nghị thực tế để chọn đúng storage dựa trên yêu cầu workload, chỉ số giám sát và best practices bảo mật.

### [Blog 3 - TRIỂN KHAI PERSISTENT STORAGE CHO AWS FARGATE VỚI AMAZON EBS](3.3-Blog3/)
Bài viết khám phá cách tích hợp trực tiếp volume Amazon EBS vào task Fargate để giải quyết bài toán persistent block storage cho container serverless. Bao gồm thiết kế kiến trúc, điểm quan trọng về tính zone-bound của EBS, và giải pháp event-driven quản lý vòng đời volume khi task bị thay thế sử dụng CloudWatch Events, Lambda và DynamoDB.