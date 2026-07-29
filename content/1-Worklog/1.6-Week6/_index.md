---
title: "Week 6 Worklog"
date: 2026-07-20
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
includeInReport: true
reportTableColumns:
  - Day
  - Task
  - Completion Date
reportHeadings:
  - Week 6 Objectives
  - Tasks to be carried out this week
  - Week 6 Achievements
reportType: worklog
---

### Week 6 Objectives:

* Learn EC2 Auto Scaling Groups (ASG), Serverless computing (AWS Lambda & API Gateway), and Infrastructure as Code (IaC).
* Practice automated scaling policies, serverless API integration, and CloudFormation template deployment.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn EC2 Auto Scaling Groups (ASG): Launch Templates, Dynamic Scaling Policies, and Health Checks | 07/20/2026 | 07/20/2026 | <https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html> |
| 3 | - Learn Serverless Architecture: AWS Lambda execution model, API Gateway REST APIs, and CloudFormation/Terraform IaC basics | 07/21/2026 | 07/21/2026 | <https://docs.aws.amazon.com/lambda/latest/dg/welcome.html> |
| 4 | - **Practice:** <br>&emsp; + Create Launch Template with Apache web server User Data <br>&emsp; + Provision ASG spanning 2 AZs connected to ALB Target Group | 07/22/2026 | 07/22/2026 | <https://docs.aws.amazon.com/autoscaling/ec2/userguide/attach-load-balancer-asg.html> |
| 5 | - **Practice:** <br>&emsp; + Write Python Lambda handler to query DynamoDB data <br>&emsp; + Expose HTTP endpoints via API Gateway REST API Proxy Integration | 07/23/2026 | 07/23/2026 | <https://docs.aws.amazon.com/apigateway/latest/developerguide/set-up-lambda-proxy-integrations.html> |
| 6 | - **Practice:** <br>&emsp; + Write CloudFormation YAML template to automate VPC & EC2 deployment <br>&emsp; + Deploy stack via AWS CLI and test resource creation | 07/24/2026 | 07/24/2026 | <https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html> |


### Week 6 Achievements:

* Built a self-healing, auto-scaling compute cluster with EC2 Auto Scaling Groups.
* Developed a fully serverless REST API using API Gateway, AWS Lambda, and DynamoDB.
* Automated AWS resource provisioning using declarative CloudFormation YAML infrastructure templates.
