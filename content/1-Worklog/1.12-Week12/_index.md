---
title: "Week 12 Worklog"
date: 2026-07-09
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Week 12 Objectives:
* Enforce strict security access controls on S3 using resource-based policies.
* Review the deployed hybrid architecture against the AWS Well-Architected Framework pillars.
* Prepare final documentation and presentation slides for the architecture defense.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1 | Author and apply a secure **S3 Bucket Policy** restricting access to designated VPC Endpoints only. | 03/07/2026 | 03/07/2026 | [S3 Bucket Policies Doc](https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucket-policies.html) |
| 2 | Configure **VPC Endpoint Policies** limiting allowed API actions on S3 endpoints. | 04/07/2026 | 04/07/2026 | [Endpoint Policies Doc](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints-access.html) |
| 3 | Test unauthorized access attempts from public networks to verify blocking mechanisms. | 05/07/2026 | 05/07/2026 | - |
| 4 | Conduct a comprehensive Well-Architected Framework review focusing on the Security and Reliability pillars. | 06/07/2026 | 06/07/2026 | [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/) |
| 5 | Perform final integration testing, trace routing analysis, and clean up test resources. | 07/07/2026 | 07/07/2026 | - |
| 6 | Finalize technical documentation, write up reports, and prepare slides for final internship presentation. | 08/07/2026 | 09/07/2026 | - |

### Week 12 Achievements:
* Fully locked down the Amazon S3 Bucket, ensuring zero public exposure while allowing encrypted hybrid access.
* Successfully defended the secure network design decisions during the Well-Architected review.

### 2. Technical Challenges & Troubleshooting:
* **Challenge:** Preventing external corporate entities or compromised accounts from bypassing the S3 access barriers.
* **Resolution:** Implemented explicit "Deny" conditions inside the S3 Bucket Policy for any traffic that does not originate from the specific VPC Gateway or Interface Endpoint IDs, rendering public credentials useless outside the network.

### 3. Key Learnings:
* Data isolation on the cloud requires a defense-in-depth model: combining network security (Endpoints) with identity boundaries (Bucket and Endpoint Policies).