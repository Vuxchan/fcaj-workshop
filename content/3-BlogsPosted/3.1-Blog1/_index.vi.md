---
title: "Blog 1"
date: 2026-29-07
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
includeInReport: false
---

# Nâng Cao Trải Nghiệm Test Local Cho Ứng Dụng Serverless Với LocalStack

Chào mọi người, đối với những ai thường hay làm việc với các dịch vụ serverless như Lambda, SQS, EventBridge hay DynamoDB, chắc hẳn không ít lần gặp cảnh phải deploy lên cloud chỉ để test thử một thay đổi nhỏ, rồi lại phải nhảy qua nhảy lại giữa IDE, CLI và các công cụ emulator --- vừa mất thời gian, vừa dễ phát sinh lỗi cấu hình không đồng nhất giữa local và cloud. Thì LocalStack chính là giải pháp giúp giải quyết bài toán này, và mới đây AWS đã tích hợp trực tiếp LocalStack vào AWS Toolkit for VS Code để việc test và debug serverless trở nên mượt mà hơn hẳn.

## Vậy LocalStack giúp được gì?

Về cơ bản, đây là một cloud service emulator cho phép mô phỏng lại các dịch vụ AWS ngay trên máy local để mình dev và test mà không cần deploy thật. Sau khi tích hợp vào VS Code, trải nghiệm được cải thiện ở 4 điểm chính:

- Kết nối và quản lý resource local ngay trong VS Code, chung giao diện với resource cloud, khỏi phải mở thêm tool khác.

- Test được cả các tương tác giữa Lambda với SQS, DynamoDB, EventBridge... ngay trên local.

- Debug chỉ với một click, không cần config port thủ công hay sửa code như trước.

- Toàn bộ quy trình deploy - test - debug đều nằm gọn trong IDE, không phải context-switch qua lại nữa.

## Setup thì sao, có phức tạp không?

Cái hay là quá trình setup gần như tự động hoàn toàn. Cài extension xong, nó tự detect xem máy đã config LocalStack chưa, nếu chưa thì có wizard hướng dẫn luôn. Wizard này lo cả phần xác thực (mở browser để login) lẫn tự tạo AWS CLI profile riêng cho LocalStack (update vào ~/.aws/config và ~/.aws/credentials), nên mình không phải tự tay chỉnh endpoint hay credential gì cả. Sau khi setup xong một lần, config này lưu lại luôn cho những lần dùng VS Code sau, không phải làm lại.

## Demo thực tế

Bài viết minh họa bằng một hệ thống xử lý đơn hàng event-driven: request từ API Gateway → đẩy vào SQS → Lambda xử lý → publish qua SNS để gửi email thông báo. Toàn bộ luồng này có thể deploy, debug (set breakpoint, step qua từng dòng như debug bình thường), và validate end-to-end ngay trên LocalStack mà không cần đụng đến tài khoản AWS thật.

## Một vài lưu ý khi áp dụng

Về chiến lược test, nên đi theo hướng phân lớp: bắt đầu bằng unit test cho logic thuần túy, sau đó integration test với LocalStack để check tương tác giữa các service, rồi mới lên cloud thật để validate những thứ LocalStack không mô phỏng chính xác được --- như IAM permission, VPC networking, hay load test hiệu năng thực tế.

Về bảo mật, nhớ cô lập môi trường local (bind LocalStack vào localhost, giới hạn qua Docker network), dùng credential giả (kiểu test/test) thay vì credential AWS thật, và dùng data giả lập thay vì data production.

## Tóm lại

LocalStack + AWS Toolkit giúp rút ngắn đáng kể vòng lặp code-test-debug cho serverless, giảm hẳn việc phải chờ deploy cloud mới biết code có chạy đúng không. Nhưng cũng cần nhớ rõ: local test nhanh và tiết kiệm, còn những thứ liên quan đến hạ tầng thật (IAM, VPC, load test) thì vẫn phải lên cloud để validate lần cuối trước khi release.

---

**Nguồn:** [AWS Compute Blog - Enhance the local testing experience for serverless applications with LocalStack](https://aws.amazon.com/blogs/compute/enhance-the-local-testing-experience-for-serverless-applications-with-localstack/)

**Minh chứng:** <img src="/images/3-BlogsPosted/3.1-Blog1/blog1.png" 
     style="width: 70%; max-width: 600px; height: auto; border-radius: 8px; box-shadow: 0 6px 20px rgba(0,0,0,0.15); display: block; margin: 0 auto;">