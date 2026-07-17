---
title: "Week 9 Worklog"
date: 2026-06-18
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives:
* Implement private connectivity from the VPC to S3 using an **S3 Gateway Endpoint**.
* Verify that traffic to S3 stays within the AWS internal network.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1 | Create an **S3 Gateway Endpoint** in the target AWS Region[cite: 4]. | 12/06/2026 | 12/06/2026 | [Gateway Endpoints for S3](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints-s3.html) |
| 2 | Associate the S3 Gateway Endpoint with the private subnet's Route Table. | 13/06/2026 | 14/06/2026 | - |
| 3 | Log into the private EC2 instance and attempt to resolve S3 DNS queries. | 15/06/2026 | 15/06/2026 | - |
| 4 | Perform S3 operations (upload/download files) from the private instance using AWS CLI. | 16/06/2026 | 17/06/2026 | [AWS CLI S3 Commands](https://docs.aws.amazon.com/cli/latest/reference/s3/) |
| 5 | Analyze trace routes to confirm traffic does not leave the AWS backbone network. | 18/06/2026 | 18/06/2026 | - |

### Week 9 Achievements:
* Configured private routing for VPC resources accessing Amazon S3.
* Verified successful private file transfers to the S3 bucket without utilizing NAT Gateway or Internet Gateway.

### 2. Technical Challenges & Troubleshooting:
* **Challenge:** AWS CLI operations on S3 initially timed out inside the private EC2 instance.
* **Resolution:** Discovered that the private subnet Route Table lacked the prefix-list route to the S3 Gateway Endpoint. Associated the endpoint correctly to automatically inject the route.

### 3. Key Learnings:
* Gateway Endpoints rely on Prefix Lists to modify route tables, ensuring routing internal traffic to S3 is handled at no extra charge.