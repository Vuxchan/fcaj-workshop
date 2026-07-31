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

**Period:** 06/07/2026 – 12/07/2026
**Theme:** Build the asynchronous judging pipeline with SQS and Lambda Worker

## Weekly Objectives
- Build the asynchronous judging pipeline with SQS and Lambda Worker.
- Continue building CodExecute according to the designed AWS serverless architecture.
- Prioritize Infrastructure as Code, least-privilege security and reproducible environments.

## Daily Plan

| Day | Task |
|---|---|
| Monday (06/07) | Define submission states: pending, running, accepted, wrong answer, runtime error, compile error and other required states. |
| Tuesday (07/07) | When a user submits code, have the API Handler store the required code/metadata in DynamoDB and send an execution job to SQS. |
| Wednesday (08/07) | Create the SQS queue and configure the Lambda Worker as an event source. |
| Thursday (09/07) | Implement the Lambda Code Executor to read the message, retrieve the submission from DynamoDB and test cases from S3. |
| Friday (10/07) | Design the job payload/metadata so the worker can process submissions independently and support retries, save judging results back to DynamoDB so the frontend can query status and results. |

## Expected Outcomes
- The asynchronous submission/judging pipeline is implemented and submissions can be processed through an SQS-triggered worker.