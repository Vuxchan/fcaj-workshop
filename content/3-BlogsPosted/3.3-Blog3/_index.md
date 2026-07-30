---
title: "Blog 3"
date: 2026-29-07
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# OPTIMIZING EC2 COSTS WITH AWS COMPUTE OPTIMIZER RIGHT SIZING

*Rightsizing — adjusting instance types and sizes to match actual workload resource requirements — is one of the most effective ways to improve ROI on EC2 investments. However, doing so manually across hundreds or thousands of instances is time-consuming and error-prone. AWS Compute Optimizer addresses this by analyzing resource utilization patterns and configuration data to deliver data-driven rightsizing recommendations.*

### 1. Operational Problem
Most organizations lack clear visibility into the optimal price-performance ratio for their instances, leading to two extremes:
* **Over-provisioning:** Unnecessary cloud spending and waste.
* **Under-provisioning:** Application performance degradation risks.

AWS Compute Optimizer analyzes up to 93 days of CloudWatch utilization data and categorizes instances into 4 findings: **Over-provisioned** (downsize candidate), **Under-provisioned** (upsize required), **Optimized** (well matched), and **Idle** (terminate or consolidate).

### 2. Metrics Analyzed
Compute Optimizer evaluates metrics across multiple dimensions:
* CPU utilization
* Memory utilization (when CloudWatch Agent is enabled)
* Network I/O
* Disk I/O & EBS throughput/IOPS
* GPU utilization (if applicable)

For each finding, the system proposes up to 3 alternative options, ranked by estimated savings, performance risk, and migration effort (ranging from *Very low* to *High*).

### 3. 5 Key Best Practices
1. **Enable Cost Optimization Hub:** Automatically switches to `AfterDiscounts` mode, factoring in active Savings Plans or Reserved Instance commitments for accurate net savings estimates.
2. **Enable Memory Metrics:** Add RAM metric collection via CloudWatch Agent or 3rd-party APM tools (Datadog, Dynatrace, Instana, New Relic) for precise recommendations on memory-heavy workloads.
3. **Customize Preferences:** Adjust CPU utilization thresholds (P90/P95/P99.5), CPU/memory headroom, and lookback period (14/32/93 days) at organization, account, or region levels.
4. **Evaluate Graviton Recommendations Carefully:** Migrating to Graviton (ARM64) can boost price-performance by up to 40%, but requires architecture compatibility verification and staging testing prior to production deployment.
5. **Establish a Structured Rightsizing Workflow:** Set up recurring review cycles, prioritize high-savings/low-risk candidates, validate with application owners, and track outcomes in Cost Explorer (automation achievable via Step Functions, EventBridge, Lambda).

### 4. Conclusion
AWS Compute Optimizer provides a solid empirical foundation for making scientific rightsizing decisions. Combining comprehensive metrics, custom preferences, and structured review processes helps organizations achieve substantial EC2 cost optimization while preserving application performance.

---

### Images & Diagrams
<div align="center">

![EC2 Rightsizing](/images/3-BlogsPosted/3.3-Blog3/right-sizing.png)

<p style="font-size: 1.15rem; font-weight: 600; margin-top: 8px;">
<i>Figure 1: EC2 Rightsizing</i></br>
<i>Source: <a target="_blank" href="https://blog.easecloud.io/cost-optimization/right-size-ec2-and-eks/">https://blog.easecloud.io/cost-optimization/right-size-ec2-and-eks/</a></i>
</p>

</div>

### Links & References
* **Original AWS Blog Article:** [https://aws.amazon.com/blogs/compute/optimize-ec2-costs-with-aws-compute-optimizer-right-sizing/](https://aws.amazon.com/blogs/compute/optimize-ec2-costs-with-aws-compute-optimizer-right-sizing/)