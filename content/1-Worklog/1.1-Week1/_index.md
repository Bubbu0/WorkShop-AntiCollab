---
title: "Week 1 Worklog"
date: 2026-04-17
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives:
* Master foundational AWS Global Infrastructure and Cloud Economics.
* Implement Zero-Trust account setup and strict cost management policies.

### 1. Detailed Task Description:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1 | Onboarding: Introduction to AWS Global Infrastructure & Cloud Economics. | 04/17/2026 | 04/17/2026 | |
| 2 | Theory: Understand Region, AZ models and Shared Responsibility Model. | 04/18/2026 | 04/18/2026 | |
| 3 | **Lab 01:** Setup AWS Account: Root hardening, MFA activation. | 04/19/2026 | 04/19/2026 | [Lab 01](https://000001.awsstudygroup.com/vi/) |
| 4 | **Lab 01:** Implement AWS Budgets & Billing Alarms with SNS notifications. | 04/20/2026 | 04/20/2026 | [Lab 01](https://000001.awsstudygroup.com/vi/) |
| 5 | **Lab 07:** Configure IAM Policies (Least Privilege Principle). | 04/21/2026 | 04/21/2026 | [Lab 07](https://000007.awsstudygroup.com/vi/) |
| 6 | **Lab 07:** Setup AWS CLI: Configure credentials, regions, and output formats. | 04/22/2026 | 04/22/2026 | [Lab 07](https://000007.awsstudygroup.com/vi/) |
| 7 | Documentation: Technical summary on IAM security and cost control. | 04/23/2026 | 04/23/2026 | |

### Week 1 Achievements:
* Established a secure, multi-layered account access architecture, moving away from Root account usage.
* Successfully implemented cost-control mechanisms with proactive billing alerts to prevent unauthorized resource usage.

### 2. Technical Challenges & Troubleshooting
* **Challenge:** Encountered "Access Denied" when running `aws s3 ls`.
* **Resolution:** Audited IAM policy JSON, found missing `s3:ListBucket` permission, corrected policy and re-verified via CLI.

### 3. Key Learnings
* IAM is the foundation of Cloud Security; Principle of Least Privilege must be enforced from day one.
* Proactive cost control is mandatory to prevent surprise billing.

<!-- ### 4. Evidence (Insert images in static/images/week1/)
![MFA Setup](/images/week1/mfa.png)
![Budget Alert](/images/week1/budget.png) -->