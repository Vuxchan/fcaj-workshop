---
title: "Blog 2"
date: 2026-29-07
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# BUILDING AN END-TO-END AGENTIC SRE WITH AWS DEVOPS AGENT

*With modern systems consisting of serverless functions, microservices, and event-driven architectures, incident response is becoming increasingly complex: engineers must manually correlate data across multiple monitoring tools while racing against SLA timers. AWS DevOps Agent aims to revolutionize this operational paradigm — acting as an autonomous, always-on AI agent that investigates incidents as they occur and supports multi-cloud and hybrid environments.*

### 1. Implementation Architecture
The solution is organized across three separate AWS accounts segregated by responsibility:
* **Demo Application Account:** Hosts production infrastructure, integrates CI/CD via CodePipeline, and uses CloudWatch, EventBridge, and a Lambda webhook handler for anomaly detection and incident forwarding.
* **Splunk Account:** Manages centralized log aggregation and analytics, connected privately to the application account via VPC peering.
* **AWS DevOps Agent Account:** Houses the automated investigation engine, receives incident webhooks, correlates data from CloudWatch, Splunk, and GitHub, and posts real-time investigation updates to Slack.

### 2. Incident Handling Workflow
**Automated Workflow:**  
`CloudWatch Alarm → EventBridge → Lambda → DevOps Agent Webhook → Multi-source Investigation (Splunk, GitHub, CloudWatch) → Root Cause + Mitigation Plan → Slack`

When a CloudWatch alarm triggers, EventBridge calls Lambda to send the incident payload to DevOps Agent's webhook. The Agent immediately queries logs via Splunk MCP, fetches deployment history from GitHub, and correlates CloudWatch metrics with deploy events to reconstruct the application topology. From there, the agent analyzes temporal relationships between deployments and operational failures, determines the root cause, and generates a detailed mitigation plan complete with remediation steps, success criteria, and rollback procedures — all posted to Slack so engineers wake up to identified root causes rather than ongoing mysteries.

### 3. Key Configuration Components
* **Agent Space:** Defines the tools and infrastructure scope accessible to the agent, configured via Console or AWS CLI.
* **Splunk Integration:** Enables Splunk MCP Server, configures auth tokens, and uses Better Webhooks to send alerts adhering to DevOps Agent schema.
* **Slack Integration:** Enables direct communication within the SRE team's working channel.
* **GitHub Integration:** Connects via OAuth (read access) allowing the agent to correlate source code changes with incidents.
* **DevOps Agent Skills:** Defines custom investigation rules (e.g., Dynatrace for alarms, Splunk for logs, CloudWatch for serverless).

### 4. From Diagnosis to Remediation
After identifying root causes, the agent generates a 4-phase mitigation plan: **Prepare**, **Pre-Validate**, **Apply**, and **Post-Validate**. For code-level fixes, the agent produces an "agent-ready spec" — a structured instruction set handed off directly to a coding agent (like Kiro) to implement changes in the codebase, fully closing the loop from diagnosis to fix without manual translation.

### 5. Conclusion
By leveraging Agent Space, multi-source integrations, and agent-ready spec handoffs, SRE workflows transform from reactive firefighting to proactive automation, reducing MTTR from hours to minutes.

---

### Images & Diagrams
<div align="center">

![Solution Architecture](/images/3-BlogsPosted/3.2-Blog2/solution_architecture.png)

<p style="font-size: 1.15rem; font-weight: 600; margin-top: 8px;">
<i>Figure 1: Solution Architecture</i>
</p>

</div>

### Links & References
* **Original AWS Blog Article:** [https://aws.amazon.com/blogs/devops/building-an-end-to-end-agentic-sre-using-aws-devops-agent/](https://aws.amazon.com/blogs/devops/building-an-end-to-end-agentic-sre-using-aws-devops-agent/)