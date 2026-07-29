---
title: "Week 5 Worklog"
date: 2026-07-13
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
includeInReport: true
reportTableColumns:
  - Day
  - Task
  - Completion Date
reportHeadings:
  - Week 5 Objectives
  - Tasks to be carried out this week
  - Week 5 Achievements
reportType: worklog
---

### Week 5 Objectives:

* Understand Relational Databases (Amazon RDS), NoSQL Databases (Amazon DynamoDB), and Load Balancing (ALB).
* Practice provisioning high-availability RDS MySQL instances, DynamoDB tables, and Application Load Balancer target routing.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn Amazon RDS architecture (Multi-AZ failover, DB Subnet Groups) and Amazon DynamoDB (Partition/Sort Keys) | 07/13/2026 | 07/13/2026 | <https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html> |
| 3 | - Learn Elastic Load Balancing (ELB): Application Load Balancer (ALB), Target Groups, and Listener Rules | 07/14/2026 | 07/14/2026 | <https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html> |
| 4 | - **Practice:** <br>&emsp; + Create DB Subnet Group & launch RDS MySQL instance in private subnets <br>&emsp; + Connect to RDS MySQL from EC2 application server | 07/15/2026 | 07/15/2026 | <https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_VPC.WorkingWithRDSInstanceinaVPC.html> |
| 5 | - **Practice:** <br>&emsp; + Test RDS Multi-AZ failover and restore database from manual DB Snapshot <br>&emsp; + Create DynamoDB table and perform CRUD operations via Python SDK (boto3) | 07/16/2026 | 07/16/2026 | <https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html> |
| 6 | - **Practice:** <br>&emsp; + Provision Application Load Balancer (ALB) in Public Subnets <br>&emsp; + Register EC2 web instances into Target Group and test traffic distribution | 07/17/2026 | 07/17/2026 | <https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html> |


### Week 5 Achievements:

* Deployed a secure, high-availability relational database (RDS MySQL Multi-AZ) inside private subnets.
* Mastered NoSQL table design and programmatic data CRUD operations using Amazon DynamoDB.
* Configured an Application Load Balancer (ALB) to distribute web traffic evenly across EC2 instances.
