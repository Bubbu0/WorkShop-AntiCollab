---
title: "Week 10 Worklog"
date: 2026-06-25
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives:
* Simulate a hybrid network architecture representing an On-Premises connection.
* Utilize Infrastructure as Code (IaC) with Terraform to rapidly provision environment resources.
* Set up AWS CloudTrail and Amazon Athena for centralized auditing and security logging.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1 | Write Terraform scripts to automate the deployment of VPC, EC2 nodes, and Security Groups. | 19/06/2026 | 20/06/2026 | [Terraform AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs) |
| 2 | Configure network routing on the simulated On-Premises EC2 instance. | 21/06/2026 | 21/06/2026 | - |
| 3 | Enable **AWS CloudTrail** to capture account-wide API activities. | 22/06/2026 | 22/06/2026 | [CloudTrail User Guide](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html) |
| 4 | Set up **Amazon Athena** tables querying raw CloudTrail logs stored in S3. | 23/06/2026 | 24/06/2026 | [Querying CloudTrail with Athena](https://docs.aws.amazon.com/athena/latest/ug/cloudtrail-logs.html) |
| 5 | Test initial connectivity from the simulated on-premises node to AWS. | 25/06/2026 | 25/06/2026 | - |

### Week 10 Achievements:
* Provisioned network resources dynamically using Terraform IaC templates.
* Configured a centralized logging and auditing framework using CloudTrail and Athena to monitor S3 API calls.

### 2. Technical Challenges & Troubleshooting:
* **Challenge:** Parsing highly nested JSON formats from raw CloudTrail logs in Athena.
* **Resolution:** Used Athena's pre-defined CloudTrail table creation queries to automatically schema-map the JSON structure, allowing efficient SQL-based log queries.

### 3. Key Learnings:
* Managing infrastructure via Terraform ensures consistent environment setups, reducing human configuration errors.