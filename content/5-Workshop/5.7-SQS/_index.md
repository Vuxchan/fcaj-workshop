---
title: "Setup Amazon SQS"
date: 2026-07-30
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

# SETTING UP AMAZON SQS FOR CODEXECUTE SUBMISSION QUEUE

In this section, we document how **Amazon Simple Queue Service (SQS)** was configured as the asynchronous submission buffer between the **API Lambda** (`codeexecute-api`) and the **Worker Lambda** (`codeexecute-worker`).

When a user clicks **SUBMIT**, the API Lambda does not execute the code directly. Instead, it pushes a submission job to an SQS queue, returns immediately to the user, and the Worker Lambda is automatically triggered to pick up and grade the submission asynchronously.

```
User clicks SUBMIT
      │
      ▼
codeexecute-api Lambda
  ├─ Saves Submission to DynamoDB (Status: "Pending")
  └─ Pushes job to SQS Queue
              │
              ▼ (SQS Event Source Mapping)
      codeexecute-worker Lambda
        ├─ Reads submission payload from SQS record
        ├─ Fetches testcases from S3
        ├─ Executes code in sandbox container
        └─ Updates Submission result in DynamoDB
```

The SQS message payload pushed by the API contains:
```json
{
  "submission_id": "...",
  "user_id": "...",
  "problem_id": "...",
  "language": "python|cpp|java|javascript",
  "code": "..."
}
```

#### Workshop Sections

1. [Create SQS Queue](5.7.1-create-queue/)
2. [Connect SQS to Lambda Worker (Event Source Mapping)](5.7.2-event-source-mapping/)
