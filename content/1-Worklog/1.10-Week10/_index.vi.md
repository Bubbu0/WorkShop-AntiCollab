---
title: "Worklog Tuần 10"
date: 2026-06-25
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu Tuần 10:
* Thiết lập môi trường mạng giả lập On-Premises để phục vụ kiểm thử kết nối Hybrid.
* Sử dụng hạ tầng dạng mã nguồn (IaC) bằng Terraform để triển khai nhanh tài nguyên Lab.
* Thiết lập giải pháp giám sát, kiểm toán log hoạt động tập trung sử dụng AWS CloudTrail và Amazon Athena.

### Công việc đã thực hiện:
| Ngày | Công việc | Bắt đầu | Hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | Viết các kịch bản Terraform để tự động hóa triển khai VPC, máy chủ EC2 và Security Groups. | 19/06/2026 | 20/06/2026 | [Tài liệu Terraform AWS](https://registry.terraform.io/providers/hashicorp/aws/latest/docs) |
| 2 | Cấu hình định tuyến trên máy chủ ảo đóng vai trò giả lập On-Premises[cite: 4]. | 21/06/2026 | 21/06/2026 | - |
| 3 | Kích hoạt dịch vụ **AWS CloudTrail** để ghi nhận toàn bộ hoạt động gọi API trong tài khoản. | 22/06/2026 | 22/06/2026 | [Tài liệu AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html) |
| 4 | Cấu hình **Amazon Athena** để truy vấn các log thô của CloudTrail được lưu trữ trên S3. | 23/06/2026 | 24/06/2026 | [Truy vấn CloudTrail bằng Athena](https://docs.aws.amazon.com/athena/latest/ug/cloudtrail-logs.html) |
| 5 | Kiểm thử kết nối mạng cơ bản từ máy chủ On-Premises hướng tới môi trường AWS. | 25/06/2026 | 25/06/2026 | - |

### Thành tựu Tuần 10:
* Khởi tạo tự động và đồng bộ tài nguyên mạng bằng các mẫu Terraform IaC.
* Xây dựng thành công hệ thống giám sát và kiểm toán bảo mật thông tin gọi API của tài khoản bằng CloudTrail và Athena.

### 2. Thách thức kỹ thuật & Khắc phục sự cố:
* **Thách thức:** Việc phân tích cấu trúc JSON lồng nhau phức tạp của log CloudTrail trong Athena gặp khó khăn.
* **Xử lý:** Sử dụng mã khởi tạo bảng tiêu chuẩn của CloudTrail cung cấp sẵn để Athena tự động định nghĩa sơ đồ (schema), hỗ trợ truy vấn nhanh bằng SQL.

### 3. Bài học kinh nghiệm:
* Định nghĩa hạ tầng bằng mã nguồn (IaC) giúp giảm thiểu sai sót cấu hình thủ công và đảm bảo tính nhất quán của hệ thống mạng.