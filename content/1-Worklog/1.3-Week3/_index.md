---
title: "Week 3 Worklog"
date: 2026-06-29
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
includeInReport: true
reportTableColumns:
  - Day
  - Task
  - Completion Date
reportHeadings:
  - Week 3 Objectives
  - Tasks to be carried out this week
  - Week 3 Achievements
reportType: worklog
---

### Week 3 Objectives:

* Understand Amazon Virtual Private Cloud (VPC) core networking concepts.
* Learn CIDR block planning, Public vs Private Subnets, Internet Gateway, NAT Gateway, Route Tables, and Network Security (Security Groups & Bastion Host).

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn VPC fundamentals: IPv4 CIDR Blocks (`10.0.0.0/16`), Subnetting (Public/Private Subnets across multi-AZ) | 06/29/2026 | 06/29/2026 | <https://docs.aws.amazon.com/vpc/latest/userguide/configure-your-vpc.html> |
| 3 | - Learn Internet Gateway (IGW) and Route Tables (Local routing & Default `0.0.0.0/0` internet route) | 06/30/2026 | 06/30/2026 | <https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Internet_Gateway.html> |
| 4 | - **Practice:** <br>&emsp; + Create a Custom VPC <br>&emsp; + Provision 2 Public Subnets & 2 Private Subnets <br>&emsp; + Attach Internet Gateway and configure Public Route Table | 07/01/2026 | 07/01/2026 | <https://docs.aws.amazon.com/vpc/latest/userguide/vpc-subnets-routing.html> |
| 5 | - **Practice:** <br>&emsp; + Provision NAT Gateway in Public Subnet <br>&emsp; + Configure Private Route Table to route outbound traffic via NAT Gateway | 07/02/2026 | 07/02/2026 | <https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html> |
| 6 | - **Practice:** <br>&emsp; + Launch Bastion Host in Public Subnet <br>&emsp; + Configure stateful Security Groups and SSH into EC2 instance in Private Subnet | 07/03/2026 | 07/03/2026 | <https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html> |


### Week 3 Achievements:

* Designed and built a multi-AZ custom VPC architecture with isolated Public and Private Subnets.
* Configured Internet Gateway and NAT Gateway for controlled inbound/outbound internet routing.
* Implemented Bastion Host jump server and Security Groups for secure remote management of private workloads.
