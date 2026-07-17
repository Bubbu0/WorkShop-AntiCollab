---
title: "Week 4 Worklog"
date: 2026-05-08
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:
* Automate infrastructure scaling.
* Establish strict storage permissions to prevent data leaks.

### 1. Detailed Task Description:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1 | **Lab 20:** Provision ELB (ALB); Setup Target Groups for EC2. | 05/08/2026 | 05/08/2026 | [Lab 20](https://000020.awsstudygroup.com/) |
| 2 | **Lab 20:** Implement Auto Scaling Launch Templates & scaling policies. | 05/09/2026 | 05/09/2026 | [Lab 20](https://000020.awsstudygroup.com/) |
| 3 | **Lab 20:** Test high availability failover during simulated traffic spike. | 05/10/2026 | 05/10/2026 | [Lab 20](https://000020.awsstudygroup.com/) |
| 4 | **Lab 13:** Provision S3 Buckets; Enforce "Block Public Access". | 05/11/2026 | 05/11/2026 | [Lab 13](https://000013.awsstudygroup.com/) |
| 5 | **Lab 13:** Implement SSE-KMS for server-side encryption. | 05/12/2026 | 05/12/2026 | [Lab 13](https://000013.awsstudygroup.com/) |
| 6 | **Lab 13:** Configure Lifecycle Rules & Versioning for auditing. | 05/13/2026 | 05/13/2026 | [Lab 13](https://000013.awsstudygroup.com/) |
| 7 | **Review:** Report on availability and S3 security controls. | 05/14/2026 | 05/14/2026 | - |

### Week 4 Achievements:
* Ensured High Availability (HA) of services during traffic spikes using Auto Scaling.
* Established a secure storage environment, mitigating the risk of sensitive data exposure on S3.

### 2. Technical Challenges & Troubleshooting
* **Challenge:** ALB Target Group Health Check status remained "Unhealthy" after deployment.
* **Troubleshooting:** Inspected Security Group settings of the EC2 instances; the instance did not allow incoming traffic from the ALB’s Security Group ID.
* **Resolution:** Updated the EC2 Security Group to whitelist the ALB Security Group for HTTP/HTTPS traffic. Health status immediately returned to "Healthy".

### 3. Key Learnings
* **High Availability:** Load balancers are critical for distributing traffic and performing health checks; Auto Scaling ensures the system can handle traffic spikes autonomously.
* **Data Protection:** S3 "Block Public Access" is the most effective first line of defense; Bucket Policies provide granular control over data object accessibility.

<!-- ### 4. Evidence
* **ALB Health Check Status:**
![ALB Healthy](/images/week4/alb-healthy.png)
* **S3 Security Policy Configuration:**
![S3 Policy](/images/week4/s3-policy.png) -->