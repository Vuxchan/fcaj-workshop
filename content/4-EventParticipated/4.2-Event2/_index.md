---
title: "Event 2"
date: 2026-06-20
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# Summary Report: AWS Student Community Event #2

## Event Objectives

This event brought together three practical sessions covering AWS certification preparation, AI-powered application security, and cloud monitoring strategies. The objective was to provide participants with practical knowledge that can be directly applied to cloud engineering, DevSecOps, and system operations.

Participants learned how to prepare effectively for the AWS Certified Cloud Practitioner examination, explored how AI agents can automate security assessments throughout the software development lifecycle, and understood why monitoring should focus on customer experience instead of only infrastructure metrics.

---

## Speakers

### 1. Ngo Le Tan Huy
**Topic:** *Inside The Exam: AWS Cloud Practitioner*

### 2. Nguyen Tuan Thinh
**Topic:** *Securing Your Web Apps With AWS Security Agent*

### 3. Nguyen Huynh Son
**Topic:** *SLA and Monitoring – From SLA to Monitoring: What Really Matters*

---

# Session 1
## Inside The Exam: AWS Cloud Practitioner

### Speaker

**Ngo Le Tan Huy**

### Session Overview

The first session provided a comprehensive roadmap for preparing for the AWS Certified Cloud Practitioner (CLF-C02) certification. Rather than memorizing AWS services, the speaker emphasized understanding cloud concepts, recognizing real-world business scenarios, and developing exam strategies based on practical thinking.

### Key Highlights

#### Understanding the Certification

The AWS Certified Cloud Practitioner certification serves as an entry-level certification that validates fundamental cloud knowledge without requiring programming or advanced system administration experience. The session explained the exam structure, including the number of questions, duration, passing score, certification validity, and recertification methods.

Participants also learned how AWS divides the examination into four domains:

- Cloud Concepts
- Security and Compliance
- Cloud Technology and Services
- Billing, Pricing, and Support

Understanding the weighting of each domain allows candidates to allocate study time more effectively.

#### Core AWS Knowledge

The speaker reviewed the most important AWS concepts that frequently appear in the examination.

For Cloud Concepts, emphasis was placed on understanding the benefits of cloud computing, the AWS Well-Architected Framework, and the AWS Cloud Adoption Framework. These concepts help learners understand why organizations migrate workloads to AWS instead of focusing only on technical implementation.

The Security and Compliance section highlighted the Shared Responsibility Model, IAM, Security Groups, Network ACLs, AWS Shield, AWS WAF, and AWS Artifact. Instead of memorizing definitions, participants were encouraged to understand the responsibility boundaries between AWS and customers.

Cloud Technology and Services introduced commonly used AWS services such as Amazon EC2, Amazon S3, Amazon RDS, DynamoDB, Lambda, Amazon VPC, and Route 53, focusing on the purpose and typical use cases of each service.

Billing and Pricing covered EC2 pricing models, AWS Budgets, Cost Explorer, and AWS Support Plans, enabling participants to understand cost optimization and support options available on AWS.

#### Effective Examination Strategies

One of the most valuable parts of the presentation focused on practical preparation strategies.

The speaker recommended associating every AWS service with one or two keywords instead of attempting to memorize every feature. This approach makes it easier to identify the correct service during scenario-based questions.

Another important recommendation was to spend more time reviewing incorrect answers after mock examinations rather than simply completing more practice tests. Understanding why incorrect options are wrong helps develop the reasoning skills required in the real examination.

Hands-on practice using the AWS Free Tier was also strongly encouraged. Building small projects with services such as EC2, IAM, and S3 helps transform theoretical knowledge into practical understanding.

#### Exam Tips

The session concluded with practical advice for taking the examination:

- Eliminate obviously incorrect answers before making a final decision.
- Avoid overthinking questions that are designed to test fundamental cloud knowledge.
- Pay close attention to keywords such as "NOT", "MOST", and "LEAST".
- Prepare identification documents and arrive early when taking the exam at a testing center.
- Use the "Flag for Review" feature to revisit difficult questions after completing easier ones.

### Lessons Learned

This session helped me understand that successfully passing the AWS Cloud Practitioner certification depends on understanding cloud concepts rather than memorizing technical details. I also realized that practical experience and reviewing mistakes are more valuable than simply completing a large number of mock exams.

---

# Session 2
## Securing Your Web Apps With AWS Security Agent

### Speaker

**Nguyen Tuan Thinh**  
*DevSecOps/Cloud Engineer – Styl Solutions*

### Session Overview

The second session introduced an AI-powered security approach that automates security reviews throughout the Software Development Lifecycle (SDLC). Instead of relying solely on manual penetration testing, the speaker demonstrated how AWS Security Agent, powered by Amazon Bedrock, can continuously analyze system architecture, source code, and running applications to identify security vulnerabilities earlier and more efficiently.

### Key Highlights

#### Challenges of Traditional Security Assessments

The session began by discussing the limitations of conventional penetration testing.

Traditional security assessments often require experienced security specialists, involve high consulting costs, and usually take several weeks to complete. Furthermore, testing quality depends heavily on the experience and methodology of individual penetration testers, making continuous security validation difficult for rapidly evolving software projects.

These challenges make manual security assessments difficult to integrate into modern DevOps environments where applications are deployed frequently.

#### Introducing AWS Security Agent

The speaker presented AWS Security Agent as an AI-powered solution that automates multiple security activities using Amazon Bedrock.

Unlike conventional AI chatbots that simply generate recommendations, the security agent can plan security tasks, perform vulnerability assessments, and verify security findings by attempting controlled exploitation techniques.

The solution supports several stages of the application lifecycle, including:

- Architecture design review
- Source code security analysis
- Active penetration testing
- Continuous security validation

This approach enables security to become an integrated part of software development rather than a final verification step.

#### Security Throughout the Development Lifecycle

One of the most valuable concepts introduced during the presentation was shifting security earlier into the development process.

The security agent can review architecture documents and Infrastructure as Code before implementation begins, allowing design weaknesses to be identified at an early stage.

During development, the agent integrates with GitHub or GitLab to automatically scan Pull Requests, detect vulnerabilities or exposed secrets, and even recommend secure code modifications.

After deployment, the agent continues evaluating running applications by performing automated security testing, helping organizations continuously identify exploitable weaknesses before attackers do.

#### Practical Benefits

Compared with traditional penetration testing, the automated approach offers several practical advantages:

- Faster security assessments.
- Continuous vulnerability detection.
- Reduced dependency on manual reviews.
- Consistent evaluation standards.
- Better integration with DevSecOps workflows.

The presentation also demonstrated that AI-assisted security reviews allow engineering teams to detect problems much earlier, reducing remediation costs and improving software quality.

#### Practical Considerations

Although AI significantly improves security automation, the speaker emphasized that it does not completely replace human expertise.

Certain authentication mechanisms such as Multi-Factor Authentication (MFA), biometric verification, and mutual TLS remain difficult for automated agents to evaluate.

Business logic vulnerabilities also require deep contextual understanding that cannot always be inferred automatically.

Additionally, automated agents consume computing resources during execution, making monitoring and cost management important considerations when deploying AI-driven security solutions.

### Lessons Learned

This session broadened my understanding of how artificial intelligence can support application security throughout the software development lifecycle. Rather than performing security only before production deployment, organizations can continuously validate architecture, source code, and running applications using automated security agents.

I also learned that while AI greatly improves efficiency and scalability, human expertise remains essential for validating complex business logic and making final security decisions.

---

# Session 3
## SLA and Monitoring – From SLA to Monitoring: What Really Matters

### Speaker

**Nguyen Huynh Son**  
*Infrastructure Support Engineer – Endava*

### Session Overview

The final session focused on one of the most important operational aspects of cloud computing: monitoring systems from a business perspective instead of relying solely on infrastructure metrics. Through practical demonstrations, the speaker explained how effective monitoring helps organizations protect their Service Level Agreements (SLAs), minimize operational risks, and improve customer experience.

### Key Highlights

#### Understanding Service Level Agreements (SLA)

The session began by explaining the purpose of a Service Level Agreement (SLA) as a formal commitment between service providers and customers regarding the expected level of service.

An effective SLA provides:

- Clear service expectations.
- Accountability between providers and customers.
- A framework for managing operational risks.
- Measurable performance indicators.

Rather than viewing SLA as only an availability percentage, the speaker emphasized understanding it as a commitment to maintaining reliable customer services.

#### Monitoring as Risk Management

Monitoring was presented as an essential component of the risk management lifecycle instead of a standalone operational activity.

The complete monitoring cycle includes:

- Identifying potential risks.
- Monitoring metrics, logs, and system events.
- Responding quickly through automated alerts and operational procedures.
- Continuously improving monitoring strategies after incidents.

Detecting abnormal behavior before customers experience service failures significantly reduces business impact and improves service reliability.

#### Looking Beyond Infrastructure Metrics

One of the central messages of the presentation was that healthy infrastructure does not necessarily indicate a healthy application.

Traditional dashboards often display metrics such as CPU utilization, memory consumption, disk usage, and network performance. While these metrics are useful, they cannot fully represent the actual customer experience.

The speaker introduced the Monitoring Pyramid, which prioritizes monitoring across multiple layers:

- Customer Experience
- Business Metrics
- Application Metrics
- Infrastructure Metrics
- Cloud Provider Resources

By monitoring business outcomes such as login success, payment completion, or checkout success, engineers gain much better visibility into overall service quality.

#### Live Demonstration

A practical demonstration illustrated this concept using a web application.

Although the infrastructure remained healthy:

- EC2 instances were operating normally.
- Load Balancer health checks passed successfully.
- CPU and memory utilization remained stable.

Users were still unable to log in because the application could not connect to its database.

This example demonstrated that infrastructure health alone cannot guarantee successful customer interactions.

#### Building Effective Alerting Systems

The session concluded by introducing a simple yet practical monitoring architecture using AWS services.

Application metrics such as login failures were published as custom metrics.

Amazon CloudWatch continuously evaluated those metrics against predefined thresholds. Whenever abnormal behavior was detected, CloudWatch triggered Amazon SNS notifications, allowing engineering teams to receive alerts through Email or Slack before customers reported incidents.

This proactive approach reduces incident response time and helps organizations maintain higher service reliability.

### Lessons Learned

This session fundamentally changed my perspective on cloud monitoring. Instead of concentrating only on server health, I learned that monitoring should begin with customer experience and business outcomes.

The practical demonstration clearly illustrated why application-level metrics are often more valuable than infrastructure metrics when evaluating production systems. I also gained a better understanding of designing monitoring architectures that combine business metrics, CloudWatch Alarms, and Amazon SNS to provide proactive operational visibility.

---

# Overall Key Takeaways

Throughout the event, I gained practical knowledge across three important areas of cloud engineering.

From the AWS Cloud Practitioner session, I learned effective certification preparation strategies and strengthened my understanding of AWS core services and cloud fundamentals.

The DevSecOps session demonstrated how artificial intelligence can automate security assessments across the software development lifecycle, enabling organizations to integrate security into continuous delivery processes.

Finally, the monitoring session highlighted that delivering reliable cloud services requires understanding customer experience, business metrics, and operational risk rather than focusing solely on infrastructure performance.

Together, these sessions reinforced the importance of combining cloud knowledge, security best practices, and operational excellence when building modern cloud solutions.

---

# Applying to Future Projects

The knowledge gained from this event can be directly applied to both academic and professional projects.

For cloud architecture, I will continue strengthening my AWS fundamentals and preparing for professional certifications through practical hands-on experience.

For application security, I plan to incorporate security reviews earlier in the software development lifecycle and explore AI-assisted security tools that improve development efficiency.

For operations, I will design monitoring systems that prioritize business metrics and customer experience while implementing automated alerting with Amazon CloudWatch and Amazon SNS to improve system reliability.

---

# Personal Reflection

This event provided a balanced combination of cloud fundamentals, application security, and operational monitoring. Unlike sessions that focus only on technical implementation, each presentation emphasized practical engineering thinking and demonstrated how AWS services support real business objectives.

The three sessions complemented one another well—from learning how cloud services work, to securing cloud applications, and finally operating those applications reliably in production. This holistic perspective gave me a much clearer understanding of the responsibilities of modern cloud engineers.

---

#### Some event photos

![Event 2 Evidence Photo](/images/4-EventParticipated/4.2-Event2/e2.jpg)
*Photo: Selfie at the event*  