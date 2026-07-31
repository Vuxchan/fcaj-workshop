---
title: "Blog 2"
date: 2026-29-07
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# Optimizing Storage Performance for Amazon EKS on AWS Outposts

For those deploying hybrid cloud solutions and needing Kubernetes running on-premises, Amazon EKS on Outposts brings the familiar AWS managed Kubernetes experience directly to your datacenter. But this comes with a critical challenge: choosing the right storage option, as each type has different performance characteristics and constraints. This AWS article dives deep into storage options for EKS on Outposts and how to optimize them.

## First, EKS on Outposts Has 2 Deployment Types

**Extended cluster** keeps the control plane in the AWS Region while worker nodes run on Outposts — requiring stable network connectivity to the Region via service link. **Local cluster** places the entire control plane on Outposts, making the cluster more independent, less dependent on Regional connectivity, and reducing latency for cluster management operations.

## What Storage Options Are Available for Extended Clusters?

### Amazon EBS

This is the choice for workloads requiring low latency and high IOPS/throughput. When running on Outposts, EBS volumes are stored on local hardware, delivering superior performance compared to network-based storage, with no dependency on external connectivity. Key consideration: EBS volumes are "locked" to a specific rack and AZ (creating a single point of failure risk), so remember to back up regularly with snapshots to the Region, and monitor capacity since Outposts capacity is finite.

### Amazon EFS

Suitable when you need a shared file system accessible by multiple pods — for example, content management or distributed processing. However, unlike EBS, EFS is not a local service on Outposts. The file system remains in the Region, and worker nodes on Outposts mount it via the service link. This means additional network latency, throughput limited by service link bandwidth, continuous dependency on Regional connectivity, and additional data transfer costs.

### Amazon S3 on Outposts

This enables local object storage, using the same API as standard S3, making it suitable for data residency requirements such as logs, audit trails, or sensitive healthcare data. A technical note: use Access Point ARN instead of bucket ARN when integrating with EKS.

## Which One Should You Choose?

In essence: **EBS** for workloads requiring low-latency, high-throughput block storage; **EFS** when you need POSIX-compliant shared file systems; and **S3** when you need scalable object storage with broad API compatibility. Beyond choosing the right type, pay attention to proper volume sizing, regular usage monitoring, accurate CPU/memory request configuration, and leveraging auto-scaling to balance performance with cost.

## Monitoring and Security

Each storage type has specific metrics to monitor via CloudWatch:

- **EBS**: IOPS, throughput, latency, burst balance
- **EFS**: Total I/O, metadata operations, burst credit
- **S3**: Request/error rate, latency, multipart upload efficiency

For security, encrypt data across all three storage types (use KMS for EBS, encryption at rest/in transit for EFS, server/client-side encryption for S3), apply IAM least privilege combined with Kubernetes RBAC for pod-level access control.

## Summary

EKS on Outposts enables hybrid application development with diverse storage options, tailored to performance, compliance, and data residency requirements. Choosing the right storage for each workload, combined with leveraging Outposts' local infrastructure, helps reduce latency, minimize network dependency, and maintain consistency between cloud and on-premises environments.

---

**Source:** [AWS Compute Blog - Optimizing storage performance for Amazon EKS on AWS Outposts](https://aws.amazon.com/blogs/compute/optimizing-storage-performance-for-amazon-eks-on-aws-outposts/)

**Proof:** <img src="/images/3-BlogsPosted/3.2-Blog2/blog2.png" 
     style="width: 70%; max-width: 600px; height: auto; border-radius: 8px; box-shadow: 0 6px 20px rgba(0,0,0,0.15); display: block; margin: 0 auto;">