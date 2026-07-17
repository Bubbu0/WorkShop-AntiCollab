---
title: "Worklog Tuần 2"
date: 2024-04-17
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:
* Nắm vững kiến trúc hạ tầng AWS và mô hình chi phí.
* Thiết lập bảo mật tài khoản (Zero-Trust) và chính sách quản lý ngân sách.

### 1. Lịch trình công việc:
| Ngày | Công việc | Bắt đầu | Hoàn thành | Tài liệu |
| :--- | :--- | :--- | :--- | :--- |
| 1 | Giới thiệu hạ tầng AWS và mô hình kinh tế Cloud. | 04/17 | 04/17 | - |
| 2 | Lý thuyết: Mô hình Shared Responsibility và Region/AZ. | 04/18 | 04/18 | - |
| 3 | **Lab 01:** Setup tài khoản: Bảo mật Root, kích hoạt MFA. | 04/19 | 04/19 | [Lab 01](https://000001.awsstudygroup.com/vi/) |
| 4 | **Lab 01:** Cấu hình AWS Budgets & cảnh báo chi phí (SNS). | 04/20 | 04/20 | [Lab 01](https://000001.awsstudygroup.com/vi/) |
| 5 | **Lab 07:** Cấu hình IAM Policies (Nguyên tắc đặc quyền tối thiểu). | 04/21 | 04/21 | [Lab 07](https://000007.awsstudygroup.com/vi/) |
| 6 | **Lab 07:** Setup AWS CLI: Cấu hình credentials và môi trường. | 04/22 | 04/22 | [Lab 07](https://000007.awsstudygroup.com/vi/) |
| 7 | Tổng kết: Tài liệu về bảo mật IAM và quản trị chi phí. | 04/23 | 04/23 | - |

### Thành tựu:
* Xây dựng kiến trúc truy cập tài khoản an toàn, loại bỏ việc dùng tài khoản Root.
* Thiết lập cơ chế kiểm soát chi phí tự động.

### 2. Thách thức kỹ thuật & Khắc phục sự cố:
* **Thách thức:** Gặp lỗi `Access Denied` khi chạy lệnh AWS CLI.
* **Khắc phục:** Kiểm tra JSON của IAM Policy, nhận thấy thiếu quyền `s3:ListBucket`, đã sửa và xác thực lại thành công.

### 3. Bài học kinh nghiệm:
* IAM là xương sống của bảo mật Cloud.
* Kiểm soát chi phí là công việc chủ động, không nên bị động.