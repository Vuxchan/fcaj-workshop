---
title: "Workshop"
date: 2026-07-30
weight: 5
chapter: false
pre: " <b> 5. </b> "
includeInReport: false
---

# CODEXECUTE WORKSHOP: HỆ THỐNG CHẤM BÀI TRỰC TUYẾN & NỀN TẢNG THUẬT TOÁN TỰ ĐỘNG TRÊN AWS SERVERLESS

#### Tổng quan

Workshop **CodExecute** hướng dẫn từng bước thiết kế, triển khai và vận hành hệ thống chấm bài tự động trực tuyến (Online Judge) hoàn toàn trên môi trường **Cloud-Native AWS Serverless**. 

Bài lab kết hợp các dịch vụ Serverless cốt lõi bao gồm **AWS Lambda** (chạy API backend & Sandbox chấm bài cách ly), **Amazon API Gateway** (REST API entrypoint), **Amazon SQS** (Hàng chờ điều tiết nộp bài), **Amazon DynamoDB** (Lưu trữ metadata & bài tập), **Amazon S3** (Lưu trữ bộ Testcases & Frontend static hosting) và **Amazon CloudFront** (CDN phân phối ứng dụng).

#### Các nội dung trong Workshop

1. [Giới thiệu & Tổng quan dự án CodExecute](5.1-Workshop-overview/)
2. [Các bước chuẩn bị & Thiết lập môi trường](5.2-Prerequiste/)
3. [Triển khai Frontend & CloudFront CDN](5.3-fe/)
4. [Triển khai Lambda qua Docker & ECR](5.4-be/)
5. [VPC Endpoint Policies (làm thêm)](5.5-Policy/)
6. [Cấu hình API Gateway cho Lambda API](5.6-APIGateway/)
7. [Dọn dẹp tài nguyên](5.10-Cleanup/)