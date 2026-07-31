---
title: "Blogs Posted"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
includeInReport: false
---

### [Blog 1 - ENHANCING LOCAL TESTING FOR SERVERLESS APPLICATIONS WITH LOCALSTACK](3.1-Blog1/)
This blog introduces LocalStack and its integration with AWS Toolkit for VS Code, enabling developers to test and debug serverless applications (Lambda, SQS, DynamoDB, EventBridge) entirely on local without deploying to the cloud. The article covers automated setup, debugging workflows, and a layered testing strategy (unit tests → integration tests on LocalStack → final validation on real cloud).

### [Blog 2 - OPTIMIZING STORAGE PERFORMANCE FOR AMAZON EKS ON AWS OUTPOSTS](3.2-Blog2/)
This blog provides a comprehensive guide to selecting and optimizing storage options for EKS on Outposts. It compares three storage types (EBS, EFS, S3 on Outposts), analyzes their performance characteristics and constraints, and offers practical recommendations for choosing the right storage based on workload requirements, monitoring metrics, and security best practices.

### [Blog 3 - DEPLOYING PERSISTENT STORAGE FOR AWS FARGATE WITH AMAZON EBS](3.3-Blog3/)
This blog explores how to integrate Amazon EBS volumes directly into Fargate tasks to address the challenge of persistent block storage for serverless containers. It covers architecture design, the critical zone-bound nature of EBS, and an event-driven solution for managing volume lifecycles during task replacement using CloudWatch Events, Lambda, and DynamoDB.