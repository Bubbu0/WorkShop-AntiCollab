---
title: "Worklog Tuần 12"
date: 2026-07-09
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu Tuần 12:
* Thắt chặt quyền kiểm soát truy cập vào S3 sử dụng các chính sách an ninh (Resource-based Policies).
* Đánh giá kiến trúc kết nối Hybrid đã triển khai dựa trên bộ quy chuẩn AWS Well-Architected Framework.
* Hoàn tất viết tài liệu, slide thuyết trình và chuẩn bị bảo vệ báo cáo thực tập cuối khóa.

### Công việc đã thực hiện:
| Ngày | Công việc | Bắt đầu | Hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | Xây dựng và áp dụng chính sách **S3 Bucket Policy** chỉ cho phép truy cập qua các VPC Endpoints chỉ định. | 03/07/2026 | 03/07/2026 | [Tài liệu S3 Bucket Policies](https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucket-policies.html) |
| 2 | Cấu hình **VPC Endpoint Policies** giới hạn các hành động gọi API được phép qua các cổng kết nối. | 04/07/2026 | 04/07/2026 | [Tài liệu Endpoint Policies](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints-access.html) |
| 3 | Thực hiện kiểm thử cố tình truy cập trái phép từ internet công cộng để xác nhận tính năng chặn. | 05/07/2026 | 05/07/2026 | - |
| 4 | Tiến hành đánh giá kiến trúc dựa trên hai trụ cột: Bảo mật (Security) và Độ tin cậy (Reliability) của AWS. | 06/07/2026 | 06/07/2026 | [AWS Well-Architected](https://aws.amazon.com/architecture/well-architected/) |
| 5 | Kiểm thử tích hợp toàn diện đầu-cuối, dọn dẹp các tài nguyên thử nghiệm để tránh phát sinh chi phí. | 07/07/2026 | 07/07/2026 | - |
| 6 | Hoàn tất viết tài liệu kỹ thuật, slide thuyết trình và chuẩn bị tốt nhất cho buổi bảo vệ báo cáo thực tập. | 08/07/2026 | 09/07/2026 | - |

### Thành tựu Tuần 12:
* Bảo vệ an toàn tuyệt đối cho S3 Bucket khỏi internet công cộng trong khi vẫn hỗ trợ truyền dữ liệu mã hóa qua mạng Hybrid
* Đánh giá và bảo vệ thành công các quyết định thiết kế mạng an toàn trước các tiêu chuẩn quốc tế.

### 2. Thách thức kỹ thuật & Khắc phục sự cố:
* **Thách thức:** Cần ngăn chặn tuyệt đối nguy cơ rò rỉ dữ liệu từ tài khoản bị xâm nhập thông qua truy cập trực tiếp bằng thông tin xác thực tĩnh.
* **Xử lý:** Áp dụng điều khoản phủ quyết (explicit Deny) trong S3 Bucket Policy cho bất kỳ kết nối nào không đi qua đúng ID của VPC Gateway Endpoint hoặc Interface Endpoint đã cấu hình, khiến thông tin xác thực tĩnh trở nên vô dụng bên ngoài mạng nội bộ.

### 3. Bài học kinh nghiệm:
* Cô lập dữ liệu trên môi trường điện toán đám mây đòi hỏi mô hình phòng thủ chiều sâu (defense-in-depth): kết hợp chặt chẽ giữa an ninh lớp mạng (Endpoints) và kiểm soát định danh (Bucket & Endpoint Policies).