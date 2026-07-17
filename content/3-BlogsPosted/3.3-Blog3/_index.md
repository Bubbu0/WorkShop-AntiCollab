---
title: "Automated Deployments to Amazon ECS Express Mode Using GitHub Actions"
date: 2026-07-09
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# Automated Deployments to Amazon ECS Express Mode Using GitHub Actions

Optimizing the CI/CD pipeline for containerized applications is crucial for modern DevOps. This solution focuses on two main pillars: simplifying operations and enhancing security when deploying to Amazon ECS.

## 1. Key Advantages

### Security via OpenID Connect (OIDC)
Instead of relying on static credentials like `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` stored in GitHub Secrets, this solution establishes a trust relationship between GitHub and AWS via **OIDC**. GitHub Actions automatically assumes a short-lived IAM Role to execute tasks, strictly adhering to the **Principle of Least Privilege**.

### Optimized Deployment with ECS Express Mode
Amazon ECS Express Mode streamlines infrastructure management and automatic load balancing. When integrated with the official "Deploy Express Service" action from AWS, rolling updates are executed rapidly and stably.

## 2. Operational Workflow
When a code push or Pull Request merge occurs on the main branch:
1. **Runner Activation:** GitHub Actions triggers the runner.
2. **Build & Push:** The runner builds the Dockerfile into a container image and pushes it to Amazon Elastic Container Registry (ECR).
3. **Deployment:** The "Deploy Express Service" action updates the task configuration and shifts traffic to the new image version on ECS Express Mode.

## 3. Implementation Steps
* **Step 1:** Configure the OIDC Identity Provider on AWS IAM, linking it with the configuration URL from GitHub (`token.actions.githubusercontent.com`).
* **Step 2:** Create a dedicated IAM Role with minimal policies, allowing only ECR write access and ECS Express Mode service updates.
* **Step 3:** Use GitHub Repository Variables for non-sensitive configurations (e.g., `AWS_REGION`, `ECR_REPOSITORY`, `ECS_SERVICE_NAME`) for easier maintenance.
* **Step 4:** Define the complete workflow configuration in `.github/workflows/deploy.yml`.

![CI/CD Workflow](/WorkShop-AntiCollab/images/3-Blog/ecs-github-actions.png)

## Conclusion
Combining GitHub Actions and Amazon ECS Express Mode via OIDC provides a comprehensive CI/CD solution. It optimizes deployment speed while meeting strict enterprise security standards. By eliminating static credentials and reducing the attack surface, this model serves as an effective reference for building secure software supply chains on AWS.

---
**Reference:** [AWS Containers Blog - Automated Deployments with GitHub Actions for ECS Express Mode](https://aws.amazon.com/vi/blogs/containers/automated-deployments-with-github-actions-for-amazon-ecs-express-mode/)