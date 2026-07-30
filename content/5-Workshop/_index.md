---
title: "Workshop"
date: 2026-07-30
weight: 5
chapter: false
pre: " <b> 5. </b> "
includeInReport: false
---

# CODEXECUTE WORKSHOP: ONLINE JUDGE & AUTOMATED ALGORITHM EVALUATION ON AWS SERVERLESS

#### Overview

The **CodExecute** workshop guides you step-by-step through designing, deploying, and operating an automated Online Judge evaluation platform built entirely on a **Cloud-Native AWS Serverless** architecture.

This lab integrates core Serverless services including **AWS Lambda** (REST API backend & isolated execution sandbox), **Amazon API Gateway** (REST API entrypoint), **Amazon SQS** (Asynchronous submission buffer queue), **Amazon DynamoDB** (High-speed metadata & problemset storage), **Amazon S3** (Testcase repository & frontend static hosting), and **Amazon CloudFront** (Global CDN content delivery).

#### Workshop Sections

1. [CodExecute Overview & Architecture](5.1-Workshop-overview/)
2. [Prerequisites & Environment Setup](5.2-Prerequiste/)
3. [Deploy Frontend & CloudFront CDN](5.3-fe/)
4. [Access S3 from On-premises](5.4-S3-onprem/)
5. [VPC Endpoint Policies (Bonus)](5.5-Policy/)
6. [Clean up](5.6-Cleanup/)