---
title: "Triển khai Internal DNS cho Internet-facing Load Balancer trên AWS bằng Kiến trúc Hướng sự kiện (Event-driven)"
date: 2026-06-10
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---



Trong quá trình tìm hiểu về mạng AWS, Elastic Load Balancing (ELB) là dịch vụ nền tảng tôi sử dụng hàng ngày. Tuy nhiên, việc cấu hình các bộ cân bằng tải này đi kèm với một thách thức về DNS mà mọi kỹ sư Cloud cần lưu ý.

## 1. Thách thức
Khi triển khai Network Load Balancer (NLB) hoặc Application Load Balancer (ALB) ở chế độ **Internet-facing**, AWS cung cấp một tên miền DNS ngẫu nhiên (ví dụ: `nlb-123...elb.us-east-1.amazonaws.com`).

Tên miền này chỉ phân giải ra địa chỉ **Public IP** của bộ cân bằng tải. Nó không cung cấp cơ chế để phân giải ra các địa chỉ **Private IP**. Hạn chế này gây ra khó khăn trong các kịch bản cụ thể:
* **Firewall Gateway của bên thứ ba:** Khi cần kiểm tra lưu lượng giữa ALB/NLB và Internet Gateway dựa trên DNS.
* **Định tuyến On-premises:** Khi cần định tuyến lưu lượng từ mạng nội bộ lên Load Balancer thông qua AWS Direct Connect hoặc Site-to-Site VPN.

## 2. Giải pháp: Tự động hóa dựa trên Sự kiện (Event-driven)
Để giải quyết vấn đề này, chúng ta có thể triển khai một giải pháp tự động quản lý các **Private Hosted Zones** trên Amazon Route 53. Hệ thống này đóng vai trò là "nguồn sự thật" (source of truth), lưu trữ và liên tục cập nhật các bản ghi DNS nội bộ cho các Internet-facing Load Balancers.

Được thiết kế cho môi trường **Multi-account** sử dụng AWS Organizations, giải pháp tận dụng:
* **CloudTrail & EventBridge:** Để nắm bắt các thay đổi hạ tầng.
* **AWS Lambda:** Để thực thi logic.
* **Amazon DynamoDB:** Để lưu trữ trạng thái và giảm thiểu giới hạn API.

## 3. Tổng quan Kiến trúc

### Tài khoản Dịch vụ dùng chung (Shared Services Account)
* **Amazon Route 53:** Chứa 2 Private Hosted Zones mỗi region.
    * ALB Suffix: `internal.region.elb.amazonaws.com`
    * NLB Suffix: `internal.elb.region.amazonaws.com`
* **AWS Lambda:**
    * `r53-scavenger`: Hàm chạy định kỳ để quét và khởi tạo bản ghi IP hiện có.
    * `r53-updater`: Hàm hướng sự kiện để duy trì tính chính xác của bản ghi.
* **Amazon DynamoDB:** Lưu trữ trạng thái của load balancers và network interfaces.
* **Amazon EventBridge Custom Bus:** Trung tâm tiếp nhận sự kiện từ các tài khoản thành viên.

### Tài khoản Thực thi (Workload Accounts)
* **IAM Roles:** Được cấu hình để cấp quyền xuyên tài khoản cho hàm `r53-scavenger`.
* **EventBridge Rule:** Bắt các sự kiện từ CloudTrail và chuyển tiếp về Custom Bus trung tâm.

## 4. Luồng hoạt động (Event-driven Workflow)
Quá trình cập nhật diễn ra tự động qua các bước:
1. **Ghi nhận sự kiện:** CloudTrail ghi lại mọi lệnh gọi API liên quan đến việc tạo/xóa Load Balancer hoặc thay đổi giao diện mạng.
2. **Truyền dẫn sự kiện:** EventBridge Rule tại tài khoản thực thi lọc và chuyển tiếp về Custom Bus.
3. **Xử lý dữ liệu:** Custom Bus kích hoạt hàm `r53-updater` để lấy thông tin Private IP mới nhất của Load Balancer.
4. **Cập nhật hệ thống:** Trạng thái được đồng bộ vào DynamoDB, bản ghi DNS trong Route 53 được tạo mới hoặc điều chỉnh tự động.

![Internal DNS Event-driven Architecture](/WorkShop-AntiCollab/images/3-Blog/internal-dns-arch.png)

## Kết luận
Bằng cách chuyển từ quản lý DNS thủ công sang mô hình hướng sự kiện, chúng ta giải quyết được vấn đề kết nối cho môi trường nội bộ mà vẫn đảm bảo khả năng mở rộng và độ chính xác.

---
**Nguồn tham khảo:** [AWS Networking & Content Delivery Blog](https://aws.amazon.com/blogs/networking-and-content-delivery/deploying-internal-dns-zones-for-internet-facing-load-balancers/)