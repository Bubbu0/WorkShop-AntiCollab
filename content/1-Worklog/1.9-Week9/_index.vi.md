---
title: "Worklog Tuần 9"
date: 2026-06-18
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu Tuần 9:
* Triển khai giải pháp kết nối riêng tư từ VPC tới S3 sử dụng **S3 Gateway Endpoint**.
* Xác thực lưu lượng truyền tải đến S3 nằm hoàn toàn bên trong mạng nội bộ AWS.

### Công việc đã thực hiện:
| Ngày | Công việc | Bắt đầu | Hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | Khởi tạo một **S3 Gateway Endpoint** tại khu vực (Region) đang triển khai Lab. | 12/06/2026 | 12/06/2026 | [Tài liệu AWS Gateway Endpoints](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints-s3.html) |
| 2 | Liên kết Gateway Endpoint với bảng định tuyến (Route Table) của phân vùng mạng Private Subnet. | 13/06/2026 | 14/06/2026 | - |
| 3 | Đăng nhập vào máy chủ EC2 nội bộ và thực hiện kiểm tra phân giải DNS của dịch vụ S3. | 15/06/2026 | 15/06/2026 | - |
| 4 | Thực hiện các thao tác upload/download tệp lên S3 bằng AWS CLI từ máy EC2 nội bộ. | 16/06/2026 | 17/06/2026 | [Tài liệu AWS CLI S3](https://docs.aws.amazon.com/cli/latest/reference/s3/) |
| 5 | Phân tích gói tin và tuyến đường đi (traceroute) để đảm bảo dữ liệu không đi ra internet công cộng. | 18/06/2026 | 18/06/2026 | - |

### Thành tựu Tuần 9:
* Cấu hình thành công cơ chế định tuyến nội bộ từ VPC tới dịch vụ Amazon S3.
* Xác thực truyền tải dữ liệu thành công lên S3 từ mạng nội bộ mà không cần NAT Gateway hay Internet Gateway.

### 2. Thách thức kỹ thuật & Khắc phục sự cố:
* **Thách thức:** Thao tác AWS CLI gọi tới S3 ban đầu bị treo (Timeout) bên trong máy chủ EC2 nội bộ.
* **Xử lý:** Phát hiện do bảng định tuyến của Private Subnet chưa được gán chính xác Prefix List của S3 Gateway Endpoint. Tiến hành liên kết lại Endpoint để hệ thống tự động chèn tuyến đường đi phù hợp.

### 3. Bài học kinh nghiệm:
* Gateway Endpoint sử dụng cơ chế Prefix List để cập nhật bảng định tuyến của VPC, cho phép truyền dữ liệu an toàn đến S3 mà không phát sinh thêm chi phí.