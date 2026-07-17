---
title: "Week 3 Worklog"
date: 2026-05-01
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:
* Build a multi-tier network architecture.
* Implement stateless firewalls and network tracking.

### Detailed Task Description:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1 | **Lab 10:** VPC Design: Define IP CIDR blocks and custom subnet mapping. | 05/01/2026 | 05/01/2026 | [Lab 10](https://000010.awsstudygroup.com/) |
| 2 | **Lab 10:** Configure Route Tables and Internet Gateway (IGW) setup. | 05/02/2026 | 05/02/2026 | [Lab 10](https://000010.awsstudygroup.com/) |
| 3 | **Lab 10:** Deploy NAT Gateway for secure internet access in Private Subnets. | 05/03/2026 | 05/03/2026 | [Lab 10](https://000010.awsstudygroup.com/) |
| 4 | **Lab 19:** Configure Network ACLs (stateless firewall protection). | 05/04/2026 | 05/04/2026 | [Lab 19](https://000019.awsstudygroup.com/) |
| 5 | **Lab 19:** Enable VPC Flow Logs; Stream to CloudWatch. | 05/05/2026 | 05/05/2026 | [Lab 19](https://000019.awsstudygroup.com/) |
| 6 | **Lab 19:** Audit Flow Logs for anomalous traffic patterns. | 05/06/2026 | 05/06/2026 | [Lab 19](https://000019.awsstudygroup.com/) |
| 7 | **Review:** Document network topology and traffic filtering rules. | 05/07/2026 | 05/07/2026 | - |

### Week 3 Achievements:
* Successfully isolated internal resources from the public internet using private subnets.
* Mastered network monitoring and traffic tracing using VPC Flow Logs.

### 2. Technical Challenges & Troubleshooting
* **Challenge:** Instances in the Private Subnet were unable to reach the internet for package updates despite having a NAT Gateway.
* **Troubleshooting:** Investigated the Private Subnet Route Table; found that the route `0.0.0.0/0` was not pointing to the NAT Gateway ID.
* **Resolution:** Updated the Private Subnet's Route Table to include a route targeting the NAT Gateway. Verified connectivity using `ping` (via jump host) and verified OS updates.

### 3. Key Learnings
* **Stateless vs Stateful:** NACLs (stateless) require explicit Inbound and Outbound rules for both request and response traffic, unlike Security Groups (stateful).
* **VPC Visibility:** VPC Flow Logs are essential for network security auditing and detecting unauthorized connection attempts in real-time.

<!-- ### 4. Evidence
* **VPC Architecture Diagram:**
![VPC Architecture](/images/week3/vpc-diagram.png)
* **VPC Flow Logs in CloudWatch:**
![Flow Logs](/images/week3/flow-logs.png) -->