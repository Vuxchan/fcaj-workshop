---
title: "Week 4 Worklog"
date: 2026-07-06
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
includeInReport: true
reportTableColumns:
  - Day
  - Task
  - Completion Date
reportHeadings:
  - Week 4 Objectives
  - Tasks to be carried out this week
  - Week 4 Achievements
reportType: worklog
---

**Period:** 29/06/2026 – 05/07/2026
**Theme:** API Gateway, Lambda API Handler and authentication

## Weekly Objectives
- API Gateway, Lambda API Handler and authentication.
- Continue building CodExecute according to the designed AWS serverless architecture.
- Prioritize Infrastructure as Code, least-privilege security and reproducible environments.

## Daily Plan

| Day | Task |
|---|---|
| Monday (29/06) | Standardize the backend API and define the main endpoints for users, problems and submissions. |
| Tuesday (30/06) | Package the API Handler Lambda and configure its execution role with IAM. |
| Wednesday (01/07) | Create an API Gateway REST API and connect the routes to the Lambda API Handler. |
| Thursday (02/07) | Configure CloudFront multi-origin routing: S3 for the frontend by default and `/api/*` to API Gateway. |
| Friday (03/07) | Integrate/prepare Google and GitHub OAuth flows, including callbacks and user data handling. |

## Expected Outcomes
- A working serverless API is available through CloudFront/API Gateway with the foundation for user authentication.
