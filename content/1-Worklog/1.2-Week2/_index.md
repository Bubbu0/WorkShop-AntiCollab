---
title: "Week 2 Worklog"
date: 2026-04-24
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:
* Safely provision virtual servers on the cloud.
* Monitor and analyze network traffic at the instance level.

### 1. Detailed Task Description:
| Day | Task | Start Date | Completion Date | Reference Material |
| :--- | :--- | :--- | :--- | :--- |
| 1 | **Research:** Theory on EC2 Lifecycle, AMIs, and EBS architecture. | 04/24 | 04/24 | - |
| 2 | **Lab 09:** Provision EC2 (Kali Linux); Generate SSH Key-pairs. | 04/25 | 04/25 | [Lab 09](https://000009.awsstudygroup.com/vi/) |
| 3 | **Lab 09:** Update OS packages and perform mount of EBS volumes. | 04/26 | 04/26 | [Lab 09](https://000009.awsstudygroup.com/vi/) |
| 4 | **Lab 03:** Analyze Network Security; Configure strict Ingress rules (Port 22 only). | 04/27 | 04/27 | [Lab 03](https://000003.awsstudygroup.com/) |
| 5 | **Lab 03:** Define restrictive Egress rules and bind to Elastic IP. | 04/28 | 04/28 | [Lab 03](https://000003.awsstudygroup.com/) |
| 6 | **Lab 03:** Capture traffic packets using Wireshark for analysis. | 04/29 | 04/29 | [Lab 03](https://000003.awsstudygroup.com/) |
| 7 | **Review:** Audit network configurations and instance logs. | 04/30 | 04/30 | - |

### Week 2 Achievements:
* Successfully deployed a Kali Linux environment on AWS for future penetration testing and security analysis.
* Analyzed and controlled low-level network traffic using Wireshark and strict Security Group rules.

### 2. Technical Challenges & Troubleshooting
* **Challenge:** Encountered `Connection Timeout` when attempting to SSH into the Kali Linux EC2 instance.
* **Troubleshooting:** Checked the Security Group settings; found that Port 22 was open to `0.0.0.0/0` but the route table was improperly associated, or the IP was blocked by local ISP.
* **Resolution:** Re-verified Security Group inbound rules to restrict specifically to my current public IP and confirmed the IGW route was correctly attached. SSH connection successful.

### 3. Key Learnings
* **Security Group Logic:** Unlike standard firewalls, Security Groups are stateful; once traffic is allowed in, the response is automatically allowed out.
* **Instance Hardening:** Always restrict SSH access to a specific IP (using `/32` CIDR) to mitigate brute-force attacks.

<!-- ### 4. Evidence
* **Security Group Configuration:**
![Inbound Rules](/images/week2/security-group.png)
* **SSH Connection Success:**
![SSH Terminal](/images/week2/ssh-kali.png) -->