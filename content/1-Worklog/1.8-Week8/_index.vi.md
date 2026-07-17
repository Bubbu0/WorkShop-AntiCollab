---
title: "Worklog Tuần 8"
date: 2026-06-11
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu Tuần 8:
* Khởi tạo hạ tầng mạng ảo nền tảng trên AWS (VPC, Subnets).
* Triển khai các máy chủ ảo EC2 làm các nút mạng kiểm thử nội bộ và bên ngoài.

### Công việc đã thực hiện:
| Ngày | Công việc | Bắt đầu | Hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | Khởi tạo VPC tùy chỉnh với các phân vùng mạng Public và Private Subnets trên nhiều Availability Zones[cite: 4]. | 05/06/2026 | 06/06/2026 | [Tài liệu AWS VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html) |
| 2 | Cấu hình Route Tables, Internet Gateways, và thắt chặt quy tắc bảo mật trong Security Groups. | 07/06/2026 | 07/06/2026 | - |
| 3 | Triển khai máy chủ EC2 kiểm thử nằm trong phân vùng Private Subnet của VPC. | 08/06/2026 | 08/06/2026 | [Hướng dẫn sử dụng EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html) |
| 4 | Triển khai một máy chủ EC2 ở phân vùng mạng riêng biệt để đóng vai trò giả lập On-Premises. | 09/06/2026 | 10/06/2026 | - |
| 5 | Kiểm tra tính thông suốt kết nối mạng cơ bản giữa các nút mạng vừa khởi tạo. | 11/06/2026 | 11/06/2026 | - |

### Thành tựu Tuần 8:
* Triển khai thành công hạ tầng mạng cơ bản hỗ trợ cả môi trường AWS Cloud và giả lập On-Premises.
* Khởi tạo thành công các máy chủ ảo EC2 được bảo vệ nghiêm ngặt bằng Security Groups.

### 2. Thách thức kỹ thuật & Khắc phục sự cố:
* **Thách thức:** Cần truy cập dòng lệnh (SSH) vào máy chủ EC2 nội bộ mà không được phép gán IP công cộng hay mở cổng SSH ra internet.
* **Xử lý:** Sử dụng AWS Systems Manager (SSM) Session Manager để truy cập dòng lệnh an toàn thông qua giao diện điều khiển của AWS mà không cần dựng máy chủ Bastion Host.

### 3. Bài học kinh nghiệm:
* Áp dụng nguyên tắc đặc quyền tối thiểu ở lớp mạng đòi hỏi phải cô lập các tài nguyên tính toán vào sâu trong các phân vùng mạng riêng tư (Private Subnets).