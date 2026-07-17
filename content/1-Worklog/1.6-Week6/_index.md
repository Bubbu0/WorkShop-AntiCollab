---
title: "Week 6 Worklog"
date: 2026-05-22
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:
* Process business logic without managing operating systems.
* Secure API endpoints.

### Tasks to be carried out this week:
### Detailed Task Description:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1 | **Lab 13:** Develop Python Lambda for event processing. | 05/22/2026 | 05/22/2026 | [Lab 13](https://000013.awsstudygroup.com/) |
| 2 | **Lab 14:** Develop Java Lambda; Configure IAM Execution roles. | 05/23/2026 | 05/23/2026 | [Lab 14](https://000014.awsstudygroup.com/) |
| 3 | **Lab 13/14:** Troubleshoot execution logs in CloudWatch. | 05/24/2026 | 05/24/2026 | [Lab 13/14](https://000013.awsstudygroup.com/) |
| 4 | **Lab 24:** Deploy API Gateway; Secure endpoints via IAM auth. | 05/25/2026 | 05/25/2026 | [Lab 24](https://000024.awsstudygroup.com/) |
| 5 | **Lab 24:** Configure API Usage Plans & Throttling rates. | 05/26/2026 | 05/26/2026 | [Lab 24](https://000024.awsstudygroup.com/) |
| 6 | **Lab 24:** Test API latency and rate-limiting behaviors. | 05/27/2026 | 05/27/2026 | [Lab 24](https://000024.awsstudygroup.com/) |
| 7 | **Review:** Document API security best practices. | 05/28/2026 | 05/28/2026 | - |

### Week 6 Achievements:
* Transitioned to Serverless architecture by running Python/Java code directly on AWS Lambda.
* Protected API endpoints from unauthorized access using IAM authorizers.


### 2. Technical Challenges & Troubleshooting
* **Challenge:** Lambda function timed out during data processing.
* **Troubleshooting:** Inspected execution logs and identified a bottleneck in database connection handling.
* **Resolution:** Increased Lambda timeout limit and optimized the connection pool logic, resulting in faster execution and better resource utilization.

### 3. Key Learnings
* Serverless reduces infrastructure overhead but requires efficient IAM role management for function execution.
* Throttling at the API level is a crucial security measure to prevent DoS attacks on serverless backends.

<!-- ### 4. Evidence
* **API Gateway Endpoint Test:**
![API Test](/images/week6/api-test.png)
* **Lambda Execution Logs:**
![Logs](/images/week6/lambda-logs.png) -->