---
title: "Worklog Tuần 3"
date: 2026-05-01
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu Tuần 3:
* Xây dựng kiến trúc mạng đa tầng (multi-tier).
* Triển khai tường lửa phi trạng thái (stateless) và theo dõi lưu lượng mạng.

### 1. Mô tả công việc chi tiết:
| Ngày | Công việc | Bắt đầu | Hoàn thành | Tài liệu |
| :--- | :--- | :--- | :--- | :--- |
| 1 | **Lab 10:** Thiết kế VPC: Định nghĩa khối CIDR IP và phân chia Subnet. | 05/01/2026 | 05/01/2026 | [Lab 10](https://000010.awsstudygroup.com/) |
| 2 | **Lab 10:** Cấu hình Route Tables và Internet Gateway (IGW). | 05/02/2026 | 05/02/2026 | [Lab 10](https://000010.awsstudygroup.com/) |
| 3 | **Lab 10:** Triển khai NAT Gateway để truy cập internet an toàn từ Subnet riêng (Private). | 05/03/2026 | 05/03/2026 | [Lab 10](https://000010.awsstudygroup.com/) |
| 4 | **Lab 19:** Cấu hình Network ACLs (tường lửa dạng stateless). | 05/04/2026 | 05/04/2026 | [Lab 19](https://000019.awsstudygroup.com/) |
| 5 | **Lab 19:** Kích hoạt VPC Flow Logs; đẩy log về CloudWatch. | 05/05/2026 | 05/05/2026 | [Lab 19](https://000019.awsstudygroup.com/) |
| 6 | **Lab 19:** Kiểm tra Flow Logs để phát hiện các mẫu lưu lượng bất thường. | 05/06/2026 | 05/06/2026 | [Lab 19](https://000019.awsstudygroup.com/) |
| 7 | **Tổng kết:** Tài liệu hóa sơ đồ mạng và các quy tắc lọc lưu lượng. | 05/07/2026 | 05/07/2026 | - |

### Thành tựu Tuần 3:
* Cô lập thành công các tài nguyên nội bộ khỏi internet công cộng bằng Subnet riêng.
* Nắm vững kỹ thuật giám sát mạng và truy vết lưu lượng sử dụng VPC Flow Logs.

### 2. Thách thức kỹ thuật & Khắc phục sự cố
* **Thách thức:** Các instance trong Private Subnet không thể truy cập internet để cập nhật package dù đã có NAT Gateway.
* **Xử lý:** Kiểm tra Route Table của Private Subnet; phát hiện route `0.0.0.0/0` không trỏ tới ID của NAT Gateway.
* **Giải quyết:** Cập nhật Route Table của Private Subnet để trỏ route `0.0.0.0/0` về NAT Gateway. Xác nhận kết nối thành công bằng lệnh `ping` (thông qua jump host) và thực hiện cập nhật OS thành công.

### 3. Bài học kinh nghiệm
* **Stateless vs Stateful:** NACLs (stateless) yêu cầu các quy tắc tường minh cho cả lưu lượng Inbound và Outbound cho cả yêu cầu và phản hồi, khác với Security Groups (stateful).
* **VPC Visibility:** VPC Flow Logs là công cụ thiết yếu cho việc kiểm toán an ninh mạng và phát hiện các nỗ lực truy cập trái phép theo thời gian thực.