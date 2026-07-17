---
title: "Worklog Tuần 4"
date: 2026-05-08
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu Tuần 4:
* Tự động hóa khả năng mở rộng hạ tầng.
* Thiết lập quyền lưu trữ nghiêm ngặt để ngăn chặn rò rỉ dữ liệu.

### 1. Mô tả công việc chi tiết:
| Ngày | Công việc | Bắt đầu | Hoàn thành | Tài liệu |
| :--- | :--- | :--- | :--- | :--- |
| 1 | **Lab 20:** Triển khai ELB (ALB); Thiết lập Target Groups cho EC2. | 05/08/2026 | 05/08/2026 | [Lab 20](https://000020.awsstudygroup.com/) |
| 2 | **Lab 20:** Triển khai Auto Scaling Launch Templates & các chính sách mở rộng. | 05/09/2026 | 05/09/2026 | [Lab 20](https://000020.awsstudygroup.com/) |
| 3 | **Lab 20:** Kiểm thử tính sẵn sàng cao (HA) và dự phòng lỗi khi mô phỏng lưu lượng tăng đột biến. | 05/10/2026 | 05/10/2026 | [Lab 20](https://000020.awsstudygroup.com/) |
| 4 | **Lab 13:** Khởi tạo S3 Buckets; Áp dụng "Block Public Access". | 05/11/2026 | 05/11/2026 | [Lab 13](https://000013.awsstudygroup.com/) |
| 5 | **Lab 13:** Triển khai mã hóa phía máy chủ (Server-side encryption) với SSE-KMS. | 05/12/2026 | 05/12/2026 | [Lab 13](https://000013.awsstudygroup.com/) |
| 6 | **Lab 13:** Cấu hình Lifecycle Rules & Versioning để lưu trữ và kiểm toán dữ liệu. | 05/13/2026 | 05/13/2026 | [Lab 13](https://000013.awsstudygroup.com/) |
| 7 | **Tổng kết:** Báo cáo về tính sẵn sàng và các chính sách bảo mật S3. | 05/14/2026 | 05/14/2026 | - |

### Thành tựu Tuần 4:
* Đảm bảo tính sẵn sàng cao (High Availability) của dịch vụ khi lưu lượng truy cập tăng đột biến nhờ Auto Scaling.
* Thiết lập môi trường lưu trữ an toàn, giảm thiểu rủi ro lộ lọt dữ liệu nhạy cảm trên S3.

### 2. Thách thức kỹ thuật & Khắc phục sự cố:
* **Thách thức:** Trạng thái Health Check của ALB Target Group báo "Unhealthy" sau khi triển khai.
* **Xử lý:** Kiểm tra cài đặt Security Group của các EC2 instance; phát hiện instance không cho phép lưu lượng truy cập từ ID của Security Group thuộc ALB.
* **Giải quyết:** Cập nhật Security Group của EC2 để cho phép (whitelist) lưu lượng HTTP/HTTPS từ Security Group của ALB. Trạng thái Health ngay lập tức trở lại "Healthy".

### 3. Bài học kinh nghiệm:
* **Tính sẵn sàng cao:** Load balancer đóng vai trò quan trọng trong việc phân phối lưu lượng và thực hiện kiểm tra sức khỏe hệ thống; Auto Scaling đảm bảo hệ thống có thể tự động xử lý khi lưu lượng tăng đột biến mà không cần can thiệp thủ công.
* **Bảo mật dữ liệu:** "Block Public Access" trên S3 là tuyến phòng thủ đầu tiên hiệu quả nhất; Bucket Policies cung cấp quyền kiểm soát chi tiết đối với khả năng truy cập đối tượng dữ liệu.