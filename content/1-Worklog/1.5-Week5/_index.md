---
title: "Week 5 Worklog"
date: 2026-05-15
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:
* Operate structured data securely.
* Protect Data at Rest using advanced encryption methods.

### Tasks to be carried out this week:
### Detailed Task Description:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1 | **Lab 24:** Provision RDS (MySQL) within Private Subnet segments. | 05/15/2026 | 05/15/2026 | [Lab 24](https://000024.awsstudygroup.com/) |
| 2 | **Lab 24:** Configure Security Groups and DB Parameter Groups. | 05/16/2026 | 05/16/2026 | [Lab 24](https://000024.awsstudygroup.com/) |
| 3 | **Lab 24:** Setup Multi-AZ for failover & DB Snapshots. | 05/17/2026 | 05/17/2026 | [Lab 24](https://000024.awsstudygroup.com/) |
| 4 | **Lab 57:** Enable Data at Rest Encryption using KMS. | 05/18/2026 | 05/18/2026 | [Lab 57](https://000057.awsstudygroup.com/) |
| 5 | **Lab 57:** Hardening database via custom Parameter Groups (ciphers). | 05/19/2026 | 05/19/2026 | [Lab 57](https://000057.awsstudygroup.com/) |
| 6 | **Lab 57:** Analyze RDS access logs for unauthorized attempts. | 05/20/2026 | 05/20/2026 | [Lab 57](https://000057.awsstudygroup.com/) |
| 7 | **Review:** Document database hardening procedures. | 05/21/2026 | 05/21/2026 | - |

### Week 5 Achievements:
* Mastered Multi-AZ database architecture for disaster recovery.
* Successfully deployed end-to-end data encryption for relational databases.

### 2. Technical Challenges & Troubleshooting
* **Challenge:** Application in EC2 couldn't connect to the newly provisioned RDS instance.
* **Troubleshooting:** Investigated Security Group of RDS; identified that the inbound rule was only allowing the CIDR block instead of the specific Security Group ID of the EC2 instance.
* **Resolution:** Updated RDS Security Group to allow inbound traffic on port 3306 from the specific EC2 Security Group ID to enforce the principle of least privilege.

### 3. Key Learnings
* Understanding the importance of Multi-AZ for high availability in database clusters.
* Data at Rest encryption using KMS is critical for compliance and security hardening.

<!-- ### 4. Evidence
* **RDS Connection Status:**
![RDS Connectivity](/images/week5/rds-connect.png)
* **KMS Encryption:**
![KMS Settings](/images/week5/kms-rds.png) -->