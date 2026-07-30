---
title: "Configure API Gateway for Lambda API"
date: 2026-07-30
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

<!-- # CONFIGURING AMAZON API GATEWAY AS TRIGGER FOR LAMBDA API (`/{proxy+}`) -->

In this section, we will create an **HTTP API Gateway**, configure **Lambda Proxy Integration** using the wildcard proxy route `ANY /{proxy+}` targeting the **AWS Lambda API Handler** (`codeexecute-api`), and configure the `/prod` deployment stage with **Auto-deploy** enabled to serve as the RESTful endpoint for frontend clients.

---

### Overview of Lambda Proxy Integration

In the **CodExecute** Serverless architecture, the **FastAPI** backend framework is packaged and executed inside an AWS Lambda function (`codeexecute-api`).

To allow API Gateway to transparently proxy incoming HTTP requests (URL path, HTTP Method, Query Parameters, Headers, Request Body) directly to the FastAPI application without manually defining every single route, we implement **Lambda Proxy Integration** using the greedy path variable `/{proxy+}` and `ANY` HTTP method.

---

### Step 1: Create HTTP API Gateway

1. Access the **Amazon API Gateway Console**.
2. Locate the **HTTP API** card on the main dashboard and click **Build**.

<div align="center">

<img src="/images/5-Workshop/5.6-APIGateway/ag1.jpg" alt="Select HTTP API Type" style="width: 80%; max-width: 900px; border-radius: 6px;">

<p style="font-size: 1rem; font-weight: 600; margin-top: 8px;">
<i>Figure 5.6.1: Selecting HTTP API as the API Gateway Type</i>
</p>

</div>

---

### Step 2: Configure Stage (`prod` - Auto-deploy: ON)

1. Configure Stage parameters for the API:
   - **Stage name:** Enter `prod`.
   - **Auto-deploy:** Toggle the switch to **ON** so API Gateway automatically publishes route updates immediately without requiring manual deployment steps.

<div align="center">

<img src="/images/5-Workshop/5.6-APIGateway/ag2.jpg" alt="Configure Stage prod" style="width: 80%; max-width: 900px; border-radius: 6px;">

<p style="font-size: 1rem; font-weight: 600; margin-top: 8px;">
<i>Figure 5.6.2: Setting Stage name to prod and enabling Auto-deploy ON</i>
</p>

</div>

---

### Step 3: Review and Create

1. Review all API details, Integrations, and Stage configurations.
2. Click **Create** to initialize the HTTP API Gateway.

<div align="center">

<img src="/images/5-Workshop/5.6-APIGateway/ag3.jpg" alt="Review and Create API Gateway" style="width: 80%; max-width: 900px; border-radius: 6px;">

<p style="font-size: 1rem; font-weight: 600; margin-top: 8px;">
<i>Figure 5.6.3: Reviewing configuration parameters and clicking Create</i>
</p>

</div>

---

### Step 4: Create Route `ANY /{proxy+}` Targeting Lambda API

1. Navigate to the **Routes** panel of the newly created API Gateway.
2. Click **Create** to add a new route:
   - **Method:** Select **ANY**.
   - **Path:** Enter `/{proxy+}`.
3. Attach the Integration pointing directly to the **AWS Lambda API Handler** (`codeexecute-api`).
4. Click **Create** to save route settings.

<div align="center">

<img src="/images/5-Workshop/5.6-APIGateway/ag4.jpg" alt="Create route ANY /{proxy+}" style="width: 80%; max-width: 900px; border-radius: 6px;">

<p style="font-size: 1rem; font-weight: 600; margin-top: 8px;">
<i>Figure 5.6.4: Configuring route ANY /{proxy+} targeting the Lambda API function</i>
</p>

</div>

---

### Verification

At this stage, **Amazon API Gateway** is configured as the active Trigger for the `codeexecute-api` Lambda function. All incoming HTTP requests to `/prod/api/*` are packaged as proxy payloads and forwarded to Lambda to execute FastAPI application logic.