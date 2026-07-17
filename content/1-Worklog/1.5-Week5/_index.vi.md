---
title: "Worklog Tuần 5"
date: 2026-05-15
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu Tuần 5:
* Vận hành dữ liệu có cấu trúc một cách an toàn.
* Bảo vệ dữ liệu ở trạng thái nghỉ (Data at Rest) bằng các phương pháp mã hóa nâng cao.

### 1. Mô tả công việc chi tiết:
| Ngày | Công việc | Bắt đầu | Hoàn thành | Tài liệu |
| :--- | :--- | :--- | :--- | :--- |
| 1 | **Lab 24:** Triển khai Amazon RDS (MySQL) trong Private Subnets. | 05/15 | 05/15 | [Lab 24](https://000024.awsstudygroup.com/) |
| 2 | **Lab 24:** Cấu hình Security Groups và DB Parameter Groups cho database. | 05/16 | 05/16 | [Lab 24](https://000024.awsstudygroup.com/) |
| 3 | **Lab 24:** Thiết lập Multi-AZ để dự phòng lỗi (failover) & sao lưu (Snapshots). | 05/17 | 05/17 | [Lab 24](https://000024.awsstudygroup.com/) |
| 4 | **Lab 57:** Kích hoạt mã hóa dữ liệu ở trạng thái nghỉ (Data at Rest) sử dụng KMS. | 05/18 | 05/18 | [Lab 57](https://000057.awsstudygroup.com/) |
| 5 | **Lab 57:** Hardening (Tăng cường bảo mật) database qua tùy chỉnh Parameter Groups. | 05/19 | 05/19 | [Lab 57](https://000057.awsstudygroup.com/) |
| 6 | **Lab 57:** Phân tích log truy cập RDS để phát hiện các nỗ lực truy cập trái phép. | 05/20 | 05/20 | [Lab 57](https://000057.awsstudygroup.com/) |
| 7 | **Tổng kết:** Tài liệu hóa các quy trình hardening cơ sở dữ liệu. | 05/21 | 05/21 | - |

### Thành tựu Tuần 5:
* Làm chủ kiến trúc cơ sở dữ liệu Multi-AZ để phục hồi sau thảm họa (Disaster Recovery).
* Triển khai thành công mã hóa dữ liệu end-to-end cho cơ sở dữ liệu quan hệ.

### 2. Thách thức kỹ thuật & Khắc phục sự cố:
* **Thách thức:** Ứng dụng trong EC2 không thể kết nối tới instance RDS vừa triển khai.
* **Xử lý:** Kiểm tra Security Group của RDS; phát hiện inbound rule chỉ cho phép traffic theo CIDR block thay vì ID cụ thể của Security Group thuộc EC2.
* **Giải quyết:** Cập nhật RDS Security Group để cho phép traffic inbound trên port 3306 từ chính ID của EC2 Security Group nhằm tuân thủ nguyên tắc đặc quyền tối thiểu (Least Privilege).

### 3. Bài học kinh nghiệm:
* **Tính sẵn sàng cao:** Tầm quan trọng của kiến trúc Multi-AZ trong việc đảm bảo tính sẵn sàng cao cho các cụm cơ sở dữ liệu.
* **Bảo mật dữ liệu:** Mã hóa Data at Rest bằng KMS là yếu tố then chốt cho việc tuân thủ các tiêu chuẩn bảo mật và tăng cường khả năng phòng vệ hệ thống.