---
title: "Tự động hóa Deployment lên Amazon ECS Express Mode bằng GitHub Actions"
date: 2026-07-09
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---



Tối ưu hóa quy trình CI/CD là yếu tố sống còn trong DevOps hiện đại. Giải pháp này tập trung vào hai trụ cột: đơn giản hóa vận hành và nâng cao bảo mật khi triển khai lên Amazon ECS.

## 1. Ưu điểm cốt lõi

### Bảo mật thông qua OpenID Connect (OIDC)
Thay vì sử dụng các thông tin xác thực tĩnh (`AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`) lưu trong GitHub Secrets, giải pháp này thiết lập mối quan hệ tin cậy giữa GitHub và AWS thông qua **OIDC**. GitHub Actions tự động giả định (assume) một IAM Role ngắn hạn để thực thi tác vụ, tuân thủ nghiêm ngặt **Nguyên tắc đặc quyền tối thiểu (Least Privilege)**.

### Triển khai tối ưu với ECS Express Mode
Amazon ECS Express Mode tinh giản việc quản lý hạ tầng và cân bằng tải tự động. Khi tích hợp với action "Deploy Express Service" chính thức từ AWS, quá trình cập nhật dịch vụ (rolling update) được thực hiện nhanh chóng và ổn định.

## 2. Quy trình vận hành
Khi có push code hoặc merge Pull Request vào nhánh main:
1. **Kích hoạt Runner:** GitHub Actions khởi chạy runner.
2. **Build & Push:** Runner build Dockerfile thành container image và đẩy lên Amazon Elastic Container Registry (ECR).
3. **Triển khai:** Action "Deploy Express Service" cập nhật cấu hình tác vụ và chuyển hướng lưu lượng sang phiên bản image mới trên ECS Express Mode.

## 3. Các bước triển khai
* **Bước 1:** Cấu hình OIDC Identity Provider trên AWS IAM, liên kết với URL cấu hình từ GitHub (`token.actions.githubusercontent.com`).
* **Bước 2:** Tạo IAM Role chuyên dụng với policy tối giản, chỉ cho phép quyền ghi ECR và cập nhật dịch vụ ECS Express Mode.
* **Bước 3:** Sử dụng GitHub Repository Variables cho các thông tin cấu hình không nhạy cảm (ví dụ: `AWS_REGION`, `ECR_REPOSITORY`, `ECS_SERVICE_NAME`) để dễ bảo trì.
* **Bước 4:** Định nghĩa file cấu hình workflow tại `.github/workflows/deploy.yml`.

## Kết luận
Việc kết hợp GitHub Actions và Amazon ECS Express Mode thông qua OIDC mang lại một giải pháp CI/CD toàn diện. Nó tối ưu hóa tốc độ triển khai trong khi vẫn đáp ứng các tiêu chuẩn bảo mật khắt khe. Bằng cách loại bỏ xác thực tĩnh, mô hình này là tài liệu tham khảo hiệu quả để xây dựng chuỗi cung ứng phần mềm an toàn trên AWS.

![CI/CD Workflow](/WorkShop-AntiCollab/images/3-Blog/ecs-github-actions.png)


---
**Nguồn tham khảo:** [AWS Containers Blog - Automated Deployments with GitHub Actions for ECS Express Mode](https://aws.amazon.com/vi/blogs/containers/automated-deployments-with-github-actions-for-amazon-ecs-express-mode/)