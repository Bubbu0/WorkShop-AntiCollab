---
title: "Worklog Tuần 11"
date: 2026-07-02
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu Tuần 11:
* Triển khai giải pháp kết nối bảo mật Hybrid tới S3 qua **S3 Interface Endpoint** (AWS PrivateLink).
* Cấu hình giải pháp giả lập DNS để điều hướng lưu lượng từ On-Premises qua mạng nội bộ.
* Triển khai AWS WAF và AWS GuardDuty để tăng cường bảo vệ an ninh thông tin.

### Công việc đã thực hiện:
| Ngày | Công việc | Bắt đầu | Hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | Khởi tạo **S3 Interface Endpoint**, cấp phát các giao diện mạng ảo (ENIs) mang IP nội bộ của VPC. | 26/06/2026 | 27/06/2026 | [Tài liệu S3 Interface Endpoint](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints-s3.html) |
| 2 | Cấu hình giả lập DNS trên máy chủ On-Premises để chuyển đổi tên miền S3 thành IP nội bộ của ENIs. | 28/06/2026 | 28/06/2026 | - |
| 3 | Thực hiện kiểm thử truy cập dữ liệu S3 từ On-Premises thông qua cơ chế DNS vừa cấu hình. | 29/06/2026 | 29/06/2026 | - |
| 4 | Cấu hình **AWS WAF** thiết lập các bộ quy tắc phòng vệ chống các lỗ hổng bảo mật Web ở Layer 7. | 30/06/2026 | 01/07/2026 | [Tài liệu AWS WAF](https://docs.aws.amazon.com/waf/latest/developerguide/waf-chapter.html) |
| 5 | Kích hoạt **Amazon GuardDuty** để chủ động giám sát và phát hiện các hành vi bất thường trong hệ thống. | 02/07/2026 | 02/07/2026 | [Tài liệu AWS GuardDuty](https://docs.aws.amazon.com/guardduty/latest/ug/what-is-guardduty.html) |

### Thành tựu Tuần 11:
* Triển khai thành công kết nối an toàn sử dụng AWS PrivateLink từ mạng giả lập On-Premises tới S3.
* Nâng cao phòng thủ hệ thống với bảo vệ Web Layer 7 (WAF) và giám sát mối đe dọa chủ động (GuardDuty).

### 2. Thách thức kỹ thuật & Khắc phục sự cố:
* **Thách thức:** Các yêu cầu gọi tới S3 từ On-Premises mặc định vẫn bị phân giải ra địa chỉ Public IP công cộng của AWS.
* **Xử lý:** Cấu hình tệp tin cấu hình DNS/hosts cục bộ trên máy On-Premises để trỏ các yêu cầu S3 về địa chỉ IP nội bộ của Interface Endpoint, giải quyết triệt để xung đột định tuyến.

### 3. Bài học kinh nghiệm:
* AWS PrivateLink giúp các máy chủ bên ngoài (như On-Premises) có thể truy cập tài nguyên đám mây qua kết nối riêng tư (VPN/Direct Connect) bằng cách ánh xạ chúng về các IP nội bộ trong VPC.