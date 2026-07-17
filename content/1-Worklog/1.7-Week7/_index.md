---
title: "Week 7 Worklog"
date: 2026-06-04
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:
* Analyze enterprise requirements for secure, private data storage on Amazon S3.
* Design a secure hybrid network architecture to access S3 privately from both AWS VPC and On-Premises environments .

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1 | Study the differences between Gateway Endpoints and Interface Endpoints (AWS PrivateLink). | 29/05/2026 | 29/05/2026 | [AWS VPC Endpoints Doc](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints.html) |
| 2 | Model security threats regarding public S3 access and data exfiltration. | 30/05/2026 | 30/05/2026 | [S3 Security Best Practices](https://docs.aws.amazon.com/AmazonS3/latest/userguide/security-best-practices.html) |
| 3 | Design the high-level hybrid networking architecture on draw.io. | 31/05/2026 | 01/06/2026 | - |
| 4 | Create a private Amazon S3 Bucket containing sensitive mock corporate data. | 02/06/2026 | 02/06/2026 | [S3 User Guide](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html) |
| 5 | Configure "Block All Public Access" on the S3 bucket and review encryption settings. | 03/06/2026 | 04/06/2026 | - |

### Week 7 Achievements:
* Successfully drafted a comprehensive hybrid S3 access architecture.
* Deployed a fully isolated S3 Bucket with public access blocked and default encryption enabled.

### 2. Technical Challenges & Troubleshooting:
* **Challenge:** Ensuring the S3 Bucket remains absolutely unreachable from the public internet while preparing for future internal endpoints.
* **Resolution:** Enabled S3 Block Public Access at the bucket level and prepared IAM permission structures for endpoint-specific policies.

### 3. Key Learnings:
* S3 is technically public-facing, but it can be effectively isolated using proper bucket-level boundaries and encryption.