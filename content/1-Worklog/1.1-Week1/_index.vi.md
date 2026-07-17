---
title: "Worklog Tuần 1"
date: 2026-04-17
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1:
* Hiểu về kiến trúc AWS và mô hình chi phí.
* Thiết lập bảo mật tài khoản và quản trị chi phí.

### 1. Weekly Schedule
| Ngày | Công việc | Bắt đầu | Hoàn thành | Tài liệu |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Nghiên cứu AWS Global Infrastructure, Region/AZ. | 04/17 | 04/17 | - |
| 2 | Hardening Root: MFA, chính sách mật khẩu. | 04/18 | 04/18 | [Lab 01](https://000001.awsstudygroup.com/vi/) |
| 3 | Quản trị chi phí: AWS Budgets & SNS Alerts. | 04/19 | 04/19 | [Lab 01](https://000001.awsstudygroup.com/vi/) |
| 4 | IAM: Quản lý Users/Groups & Policy. | 04/20 | 04/20 | [Lab 07](https://000007.awsstudygroup.com/vi/) |
| 5 | Setup AWS CLI: Credentials & Region config. | 04/21 | 04/21 | [Lab 07](https://000007.awsstudygroup.com/vi/) |
| 6 | Audit: Rà soát bảo mật qua Trusted Advisor. | 04/22 | 04/22 | [Lab 01](https://000001.awsstudygroup.com/vi/) |
| 7 | Tổng kết báo cáo tuần 1. | 04/23 | 04/23 | - |

### 2. Technical Challenges & Troubleshooting
* **Thách thức:** Lỗi `Access Denied` khi dùng AWS CLI.
* **Xử lý:** Kiểm tra lại IAM Policy, thêm quyền `s3:ListBucket` và cập nhật lại Access Key.

### 3. Key Learnings
* IAM là xương sống của AWS.
* Cần kiểm soát chi phí ngay từ lúc bắt đầu.

### 4. Achievements/Metrics
* Thiết lập môi trường Zero-Trust cơ bản.
* Kích hoạt cảnh báo ngân sách tự động.