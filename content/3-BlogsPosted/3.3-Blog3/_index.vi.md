---
title: "Blog 3"
date: 2026-29-07
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Triển Khai Persistent Storage Cho AWS Fargate Với Amazon EBS

Chào mọi người, ai đã dùng Fargate chắc đều mê cái sự "khỏi lo quản lý server" của nó, nhưng khi cần chạy những ứng dụng đòi hỏi lưu trữ dữ liệu bền vững --- như WordPress giữ file upload, ứng dụng retail cần catalog sản phẩm, hay pipeline xử lý dữ liệu --- thì bản chất ephemeral (tạm thời) của container lại là một rào cản lớn. Bài viết này hướng dẫn cách tích hợp Amazon EBS trực tiếp vào Fargate task để giải quyết bài toán block storage này.

## Kiến trúc tổng quan

Giải pháp triển khai theo mô hình multi-tier, kết hợp serverless container với block storage trải trên nhiều Availability Zone để đảm bảo tính sẵn sàng cao. Mỗi task sẽ có một volume EBS riêng (loại io2 hoặc gp3), được mã hóa và cho hiệu năng ổn định, đi kèm security group kiểm soát traffic và CloudWatch log để debug.

## Lưu ý quan trọng: EBS là dịch vụ theo zone

Đây là điểm mấu chốt cần hiểu trước khi triển khai: một volume EBS chỉ tồn tại trong một AZ duy nhất và chỉ attach được vào task nằm cùng zone đó. Vì vậy mô hình này phù hợp nhất với các ứng dụng zone-isolated như môi trường dev/test, batch job xử lý dữ liệu cục bộ, hay ứng dụng phục vụ nội dung theo khu vực. Nếu cần dữ liệu khả dụng xuyên nhiều AZ, nên cân nhắc các giải pháp Multi-AZ chuyên dụng (như DRBD), dùng Amazon EFS cho shared storage, hoặc thiết kế ứng dụng stateless kết hợp external data store như RDS/DynamoDB.

## Về mặt triển khai hạ tầng

Bài viết dùng AWS CDK để dựng toàn bộ stack: VPC multi-AZ, ECS cluster bật Container Insights, Fargate task definition có gắn cấu hình volume EBS, container mount volume vào đường dẫn cụ thể (ví dụ /data), cùng với Application Load Balancer có HTTPS listener và health check. Phần ứng dụng minh họa là một Flask app đơn giản cho phép upload/list file vào block storage --- dùng để demo, không phải chuẩn production.

## Bài toán khó nhất: xử lý khi task bị thay thế

Đây là phần thú vị nhất của bài viết. Task Fargate có thể bị terminate và thay thế bất cứ lúc nào --- do update service, bảo trì hạ tầng, Spot interruption, auto-scaling, hay health check fail. Khi đó, volume EBS gắn với task cũ sẽ bị "mồ côi" (orphaned), còn task mới lại cần truy cập đúng dữ liệu đó.

Giải pháp được đề xuất là quản lý vòng đời volume theo hướng event-driven: khi có sự kiện ECS (update, scale, interrupt), CloudWatch Events sẽ kích hoạt một Lambda function để tạo snapshot từ volume cũ, ghi lại reference vào DynamoDB, rồi restore snapshot đó cho volume mới gắn vào task thay thế. Để tránh vòng lặp vô hạn (Lambda tạo task mới → lại sinh ra event mới → lại gọi Lambda), hệ thống cần có cơ chế chống lặp: gắn tag đánh dấu (managed-by: ebs-lifecycle-lambda) lên task được Lambda tạo ra, kết hợp kiểm tra idempotency qua DynamoDB để đảm bảo mỗi cặp volume/task chỉ được xử lý đúng một lần.

Cần lưu ý, cách tiếp cận này phù hợp nhất với các service dạng single-task (DesiredCount=1) hoặc có thể tách nhỏ thành nhiều service single-task riêng lẻ, hơn là mô hình multi-replica truyền thống.

## Một lưu ý về snapshot

Với hệ thống phân tán dùng nhiều volume, snapshot thủ công (ad-hoc) không tự động đảm bảo tính nhất quán giữa các volume với nhau --- cần điều phối thủ công để đảm bảo toàn vẹn dữ liệu. Ngoài ra, việc restore snapshot vốn là thao tác "best effort" với thời gian không cố định, nên có thể cân nhắc dùng tính năng provisioned volume hydration rate để tăng tốc quá trình restore.

## Chi phí

Với cấu hình 2 task chạy liên tục tại us-east-1, chi phí ước tính khoảng $37/tháng, trong đó phần lớn đến từ compute Fargate ($35.55) còn EBS chỉ chiếm phần rất nhỏ ($1.60).

## Tóm lại

Tích hợp EBS trực tiếp vào Fargate mở ra khả năng chạy các ứng dụng cần block storage bền vững mà vẫn giữ được sự đơn giản vốn có của serverless container. Điểm mấu chốt cần đầu tư kỹ là cơ chế quản lý vòng đời volume khi task bị thay thế --- vì đây chính là phần quyết định ứng dụng có mất dữ liệu hay không trong các sự kiện vận hành bình thường như deploy hay auto-scaling.

---

**Nguồn:** [AWS Storage Blog - Attaching block storage with AWS Fargate and Amazon EBS volumes](https://aws.amazon.com/blogs/storage/attaching-block-storage-with-aws-fargate-and-amazon-ebs-volumes/)

**Minh chứng:** <img src="/images/3-BlogsPosted/3.3-Blog3/blog3.png" 
     style="width: 70%; max-width: 600px; height: auto; border-radius: 8px; box-shadow: 0 6px 20px rgba(0,0,0,0.15); display: block; margin: 0 auto;">