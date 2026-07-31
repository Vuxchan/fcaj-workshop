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

**Period:** 13/07/2026 – 19/07/2026
**Theme:** Container sandbox, security and Code Executor reliability

## Weekly Objectives
- Container sandbox, security and Code Executor reliability.
- Continue building CodExecute according to the designed AWS serverless architecture.
- Prioritize Infrastructure as Code, least-privilege security and reproducible environments.

## Daily Plan

| Day | Task |
|---|---|
| Monday (13/07) | Create the Docker image for the code execution environment and push it to Amazon ECR. |
| Tuesday (14/07) | Configure the Lambda Code Executor to use an appropriate container image runtime. |
| Wednesday (15/07) | Design limits for execution time, memory and output, and handle compile/runtime errors so one submission cannot disrupt the worker. |
| Thursday (16/07) | Keep test cases separate from submitted code; allow the worker to access test cases through the minimum required IAM permissions. |
| Friday (17/07) | Test SQS retries, visibility timeout, duplicate messages and worker idempotency, test failure cases: missing submission, invalid testcase, timeout, compilation failure and Lambda failure. |

## Expected Outcomes
- The Code Executor has a containerized runtime, resource limits, and appropriate error/retry handling.
