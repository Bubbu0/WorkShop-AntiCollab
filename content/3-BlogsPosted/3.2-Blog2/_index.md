---
title: "Deploying Internal DNS for Internet-facing Load Balancers on AWS Using Event-driven Architecture"
date: 2026-06-06
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---


In my journey with AWS networking, Elastic Load Balancing (ELB) is a foundational service I encounter daily. However, configuring these load balancers comes with a specific DNS challenge that every cloud engineer should be aware of.

## 1. The Challenge
When you deploy an **Internet-facing** Network Load Balancer (NLB) or Application Load Balancer (ALB), AWS provides a random DNS name (e.g., `nlb-123...elb.us-east-1.amazonaws.com`). 

This DNS name resolves solely to the **Public IP addresses** of the load balancer. It does not provide a mechanism to resolve the load balancer's Private IPs. This limitation creates hurdles in specific scenarios:
* **Third-party Firewall Gateways:** When traffic inspection between the ALB/NLB and the Internet Gateway is required based on DNS.
* **On-premises Routing:** When routing traffic from an On-premises network to the Load Balancer via AWS Direct Connect or Site-to-Site VPN.

## 2. The Solution: Event-Driven Automation
To solve this, we can implement an automated solution that manages **Private Hosted Zones** on Amazon Route 53. This system acts as a "source of truth," storing and continuously updating internal DNS records for Internet-facing Load Balancers.

Designed for **Multi-account** environments using AWS Organizations, the solution leverages:
* **CloudTrail & EventBridge:** To capture infrastructure changes.
* **AWS Lambda:** To perform the logic.
* **Amazon DynamoDB:** To store state and prevent API rate-limit issues.

## 3. Architecture Overview

### Shared Services Account
* **Amazon Route 53:** Hosts 2 Private Hosted Zones per region.
    * ALB Suffix: `internal.region.elb.amazonaws.com`
    * NLB Suffix: `internal.elb.region.amazonaws.com`
* **AWS Lambda:**
    * `r53-scavenger`: Scheduled function to initial scan and populate existing IP addresses.
    * `r53-updater`: Event-driven function to maintain DNS records.
* **Amazon DynamoDB:** Stores the state of load balancers and network interfaces to optimize performance.
* **Amazon EventBridge Custom Bus:** Centralizes events from member accounts to trigger the updater.

### Workload Accounts
* **IAM Roles:** Configured to grant the `r53-scavenger` function the necessary cross-account permissions.
* **EventBridge Rule:** Captures relevant events from CloudTrail and forwards them to the central Custom Bus.

## 4. The Event-Driven Workflow
The update process is fully automated through the following steps:

1.  **Event Capture:** CloudTrail records any API calls related to Load Balancer creation/deletion or network interface changes.
2.  **Event Propagation:** The EventBridge Rule in the workload account filters these events and forwards them to the central Custom Bus.
3.  **Data Processing:** The Custom Bus triggers the `r53-updater` Lambda function, which fetches the latest Private IP information of the Load Balancer.
4.  **System Update:** The state is synchronized in DynamoDB, and the corresponding DNS record in Route 53 is automatically created or updated.

![Internal DNS Event-driven Architecture](/WorkShop-AntiCollab/images/3-Blog/internal-dns-arch.png)

## Conclusion
By shifting from manual DNS management to an event-driven model, we solve the connectivity issues for internal environments while ensuring scalability and accuracy. This architecture is a prime example of how AWS services can be orchestrated to solve complex networking problems automatically.

---
<!-- **Reference:** [AWS Networking & Content Delivery Blog - Deploying Internal DNS Zones](https://aws.amazon.com/blogs/networking-and-content-delivery/deploying-internal-dns-zones-for-internet-facing-load-balancers/) -->