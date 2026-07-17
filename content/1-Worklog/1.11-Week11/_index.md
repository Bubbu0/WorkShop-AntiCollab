---
title: "Week 11 Worklog"
date: 2026-07-02
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Week 11 Objectives:
* Implement private hybrid connectivity to S3 via an **S3 Interface Endpoint** (AWS PrivateLink).
* Configure a simulated DNS environment to route On-Premises S3 traffic locally.
* Deploy AWS WAF and AWS GuardDuty for active security auditing.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1 | Create an **S3 Interface Endpoint** allocating private Elastic Network Interfaces (ENIs). | 26/06/2026 | 27/06/2026 | [Interface Endpoints for S3](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints-s3.html) |
| 2 | Set up DNS simulation on the On-Premises node to override S3 public resolution with the private ENI IPs. | 28/06/2026 | 28/06/2026 | - |
| 3 | Test private S3 access from the simulated on-premises node using the local DNS mapping. | 29/06/2026 | 29/06/2026 | - |
| 4 | Deploy **AWS WAF** rules to defend web resources from Application Layer (Layer 7) threats. | 30/06/2026 | 01/07/2026 | [AWS WAF Developer Guide](https://docs.aws.amazon.com/waf/latest/developerguide/waf-chapter.html) |
| 5 | Enable **Amazon GuardDuty** to monitor and detect malicious activities and network anomalies. | 02/07/2026 | 02/07/2026 | [GuardDuty User Guide](https://docs.aws.amazon.com/guardduty/latest/ug/what-is-guardduty.html) |

### Week 11 Achievements:
* Successfully established secure PrivateLink connectivity from simulated on-premises network to S3.
* Hardened network environments with layer 7 protection (WAF) and active threat monitoring (GuardDuty).

### 2. Technical Challenges & Troubleshooting:
* **Challenge:** Standard DNS queries from the On-Premises node resolved S3 endpoints to public IPs instead of Private ENI IPs.
* **Resolution:** Configured local host/DNS mapping simulation on the On-Premises client to point S3 requests to the private Interface Endpoint IPs, successfully resolving routing conflicts.

### 3. Key Learnings:
* AWS PrivateLink enables private access to services like S3 over VPN/Direct Connect by exposing local IP endpoints within the VPC.