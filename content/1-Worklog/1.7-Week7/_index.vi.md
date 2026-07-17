---
title: "Worklog Tuần 7"
date: 2026-06-04
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu Tuần 7:
* Phân tích các yêu cầu của doanh nghiệp về việc lưu trữ dữ liệu an toàn, riêng tư trên Amazon S3.
* Thiết kế kiến trúc mạng Hybrid bảo mật để truy cập S3 nội bộ từ cả môi trường AWS VPC và On-Premises.

### Công việc đã thực hiện:
| Ngày | Công việc | Bắt đầu | Hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | Nghiên cứu sự khác biệt giữa Gateway Endpoints và Interface Endpoints (AWS PrivateLink). | 29/05/2026 | 29/05/2026 | [Tài liệu AWS VPC Endpoints](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints.html) |
| 2 | Phân tích các mối đe dọa an ninh mạng liên quan đến truy cập S3 công cộng và rò rỉ dữ liệu. | 30/05/2026 | 30/05/2026 | [Bảo mật S3 Best Practices](https://docs.aws.amazon.com/AmazonS3/latest/userguide/security-best-practices.html) |
| 3 | Vẽ sơ đồ kiến trúc mạng tổng quan của giải pháp trên draw.io. | 31/05/2026 | 01/06/2026 | - |
| 4 | Khởi tạo Amazon S3 Bucket riêng tư chứa dữ liệu giả lập nhạy cảm của doanh nghiệp. | 02/06/2026 | 02/06/2026 | [Hướng dẫn sử dụng S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html) |
| 5 | Cấu hình tính năng "Block All Public Access" và thiết lập mã hóa mặc định cho S3 Bucket. | 03/06/2026 | 04/06/2026 | - |

### Thành tựu Tuần 7:
* Xây dựng thành công sơ đồ kiến trúc mạng truy cập Hybrid an toàn đến S3.
* Triển khai thành công S3 Bucket riêng tư bị cô lập hoàn toàn khỏi Internet.

### 2. Thách thức kỹ thuật & Khắc phục sự cố:
* **Thách thức:** Đảm bảo S3 Bucket không thể truy cập từ internet công cộng nhưng vẫn sẵn sàng tiếp nhận các kết nối nội bộ sau này.
* **Xử lý:** Kích hoạt tính năng Block Public Access ở cấp độ bucket và chuẩn bị cấu trúc quyền IAM để áp dụng Endpoint Policy sau này.

### 3. Bài học kinh nghiệm:
* Bản chất Amazon S3 là dịch vụ hướng ra internet, nhưng có thể cô lập hóa hoàn toàn bằng cách sử dụng các ranh giới bảo mật và mã hóa phù hợp.