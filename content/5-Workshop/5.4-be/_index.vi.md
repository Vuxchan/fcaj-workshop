---
title: "Triển khai Lambda qua Docker & ECR"
date: 2026-07-30
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

<!-- # TRIỂN KHAI BACKEND LAMBDA FUNCTIONS BẰNG DOCKER & AMAZON ECR -->

Trong phần này, chúng ta sẽ thực hiện đóng gói dịch vụ **Backend CodExecute** thành các Container Images trên **Amazon ECR**, đồng thời triển khai hai hàm **AWS Lambda Functions** (`codeexecute-worker` và `codeexecute-api`) trực tiếp trên **AWS Console**.

#### Nội dung chi tiết:

1. [Tạo Amazon ECR & Build Docker Image](5.4.1-ECR/)
2. [Khởi tạo & Cấu hình AWS Lambda trên AWS Console](5.4.2-Lambda/)
