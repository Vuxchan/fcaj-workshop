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

**Period:** 22/06/2026 – 28/06/2026
**Theme:** Deploy the frontend to S3 and configure CloudFront CDN

## Weekly Objectives
- Deploy the frontend to S3 and configure CloudFront CDN.
- Continue building CodExecute according to the designed AWS serverless architecture.
- Prioritize Infrastructure as Code, least-privilege security and reproducible environments.

## Daily Plan

| Day | Task |
|---|---|
| Monday (22/06) | Build the frontend for production and identify the static assets that must be uploaded to S3. |
| Tuesday (23/06) | Configure S3 as the frontend origin and use Origin Access Control (OAC) to prevent direct public bucket access. |
| Wednesday (24/06) | Create the CloudFront distribution with HTTPS, caching and a default root object. |
| Thursday (25/06) | Attach AWS WAF to CloudFront for a basic protection layer on the public endpoint. |
| Friday (26/06) | Configure SPA routing/fallback so routes such as `/login`, `/problems` and `/submissions` work correctly after refresh. |

## Expected Outcomes
- The frontend is served through CloudFront, the S3 bucket is not directly public, and SPA routing works correctly.
