---
title: "Week 7 Worklog"
date: 2026-07-27
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
includeInReport: true
reportTableColumns:
  - Day
  - Task
  - Completion Date
reportHeadings:
  - Week 7 Objectives
  - Tasks to be carried out this week
  - Week 7 Achievements
reportType: worklog
---

**Period:** 20/07/2026 – 26/07/2026
**Theme:** Monitoring, alerting, optimization and system testing

## Weekly Objectives
- Monitoring, alerting, optimization and system testing.
- Continue building CodExecute according to the designed AWS serverless architecture.
- Prioritize Infrastructure as Code, least-privilege security and reproducible environments.

## Daily Plan

| Ngày | Công việc chính |
|---|---|
| Monday (20/07) | Set up CloudWatch Logs for the API Handler and Code Executor with a consistent format including submission/job IDs. |
| Tuesday (21/07) | Create CloudWatch metrics/alarms for Lambda errors, duration, throttles, SQS backlog and other key indicators. |
| Wednesday (22/07) | Set up an SNS topic and Lambda/SNS notifications for required alerts. |
| Thursday (23/07) | Run an appropriate Dev-level load test and observe submission processing time. |
| Friday (24/07) | Review costs and resources that may generate unexpected charges; avoid leaving unnecessary NAT Gateway/resources running. |

## Expected Outcomes
- The system has basic logging, monitoring and alerting, and security/cost risks have been reviewed.
