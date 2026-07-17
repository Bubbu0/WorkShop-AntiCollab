---
title: "Week 8 Worklog"
date: 2026-06-11
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:
* Provision the foundational network infrastructure on AWS (VPC, Subnets).
* Deploy test EC2 instances acting as internal and external client nodes.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1 | Create a custom VPC with Public and Private Subnets in multiple Availability Zones. | 05/06/2026 | 06/06/2026 | [AWS VPC Setup Guide](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html) |
| 2 | Configure Route Tables, Internet Gateways, and Security Groups with restricted traffic rules. | 07/06/2026 | 07/06/2026 | - |
| 3 | Deploy a test EC2 instance inside the VPC Private Subnet (VPC Client). | 08/06/2026 | 08/06/2026 | [EC2 User Guide](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html) |
| 4 | Deploy an EC2 instance in a separate isolated subnet to simulate an On-Premises node. | 09/06/2026 | 10/06/2026 | - |
| 5 | Verify basic network ping connectivity between the components. | 11/06/2026 | 11/06/2026 | - |

### Week 8 Achievements:
* Deployed the base networking architecture supporting both cloud and simulated on-premises workloads.
* Successfully provisioned isolated EC2 instances with strict security groups.

### 2. Technical Challenges & Troubleshooting:
* **Challenge:** SSH access into the private EC2 instance without exposing it to the public internet.
* **Resolution:** Configured an AWS Systems Manager (SSM) Session Manager to securely log into the private instance without needing an internet-facing Bastion host.

### 3. Key Learnings:
* Implementing the principle of least privilege at the network layer requires isolating computing workloads into private subnets.