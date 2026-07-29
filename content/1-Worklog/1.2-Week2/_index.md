---
title: "Week 2 Worklog"
date: 2026-06-22
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
includeInReport: true
reportTableColumns:
  - Day
  - Task
  - Completion Date
reportHeadings:
  - Week 2 Objectives
  - Tasks to be carried out this week
  - Week 2 Achievements
reportType: worklog
---

### Week 2 Objectives:

* Understand AWS IAM core concepts: Users, Groups, Roles, and Policies.
* Learn AWS security best practices: Least privilege, MFA, and temporary credentials.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn IAM fundamentals: IAM Users, Groups, and Managed Policies vs Inline Policies | 06/22/2026 | 06/22/2026 | <https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users.html> |
| 3 | - Learn IAM Roles & Trust Relationships (EC2 Service Roles, Cross-account access) | 06/23/2026 | 06/23/2026 | <https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html> |
| 4 | - **Practice:** <br>&emsp; + Create IAM Users and Groups <br>&emsp; + Attach Custom JSON Policies <br>&emsp; + Enforce MFA policy for admin users | 06/24/2026 | 06/24/2026 | <https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html> |
| 5 | - **Practice:** <br>&emsp; + Create IAM Role for EC2 with S3 ReadAccess <br>&emsp; + Attach role to EC2 instance <br>&emsp; + Verify S3 access without hardcoded keys | 06/25/2026 | 06/25/2026 | <https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2.html> |
| 6 | - Learn about AWS Security Token Service (STS) and IAM Access Analyzer | 06/26/2026 | 06/26/2026 | <https://docs.aws.amazon.com/STS/latest/UsingSTS/welcome.html> |


### Week 2 Achievements:

* Understood the structure of IAM Policies (Effect, Action, Resource, Condition).
* Successfully created and configured IAM Roles for EC2 instances to securely access S3 buckets without storing long-term credentials.
* Applied least-privilege principles and configured Multi-Factor Authentication (MFA) enforcement.
