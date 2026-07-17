---
title: "Worklog Tuần 6"
date: 2026-05-22
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu Tuần 6:
* Xử lý logic nghiệp vụ mà không cần quản lý hệ điều hành (Serverless).
* Bảo mật các API endpoints.

### 1. Mô tả công việc chi tiết:
| Ngày | Công việc | Bắt đầu | Hoàn thành | Tài liệu |
| :--- | :--- | :--- | :--- | :--- |
| 1 | **Lab 13:** Phát triển Python Lambda cho xử lý sự kiện. | 05/22/2026 | 05/22/2026 | [Lab 13](https://000013.awsstudygroup.com/) |
| 2 | **Lab 14:** Phát triển Java Lambda; Cấu hình IAM Execution roles. | 05/23/2026 | 05/23/2026 | [Lab 14](https://000014.awsstudygroup.com/) |
| 3 | **Lab 13/14:** Xử lý lỗi execution logs trong CloudWatch. | 05/24/2026 | 05/24/2026 | [Lab 13/14](https://000013.awsstudygroup.com/) |
| 4 | **Lab 24:** Triển khai API Gateway; Bảo mật endpoint qua IAM auth. | 05/25/2026 | 05/25/2026 | [Lab 24](https://000024.awsstudygroup.com/) |
| 5 | **Lab 24:** Cấu hình API Usage Plans & tốc độ Throttling. | 05/26/2026 | 05/26/2026 | [Lab 24](https://000024.awsstudygroup.com/) |
| 6 | **Lab 24:** Kiểm thử độ trễ API và hành vi giới hạn tốc độ (rate-limiting). | 05/27/2026 | 05/27/2026 | [Lab 24](https://000024.awsstudygroup.com/) |
| 7 | **Tổng kết:** Tài liệu hóa các biện pháp bảo mật API. | 05/28/2026 | 05/28/2026 | - |

### Thành tựu Tuần 6:
* Chuyển đổi sang kiến trúc Serverless bằng cách thực thi mã nguồn Python/Java trực tiếp trên AWS Lambda.
* Bảo vệ các API endpoints khỏi truy cập trái phép bằng cách sử dụng IAM authorizers.

### 2. Thách thức kỹ thuật & Khắc phục sự cố:
* **Thách thức:** Hàm Lambda bị timeout trong quá trình xử lý dữ liệu.
* **Xử lý:** Kiểm tra các execution logs và xác định được điểm nghẽn (bottleneck) trong quá trình xử lý kết nối cơ sở dữ liệu.
* **Giải quyết:** Tăng giới hạn timeout của Lambda và tối ưu hóa logic connection pool, giúp tăng tốc độ thực thi và tối ưu hóa tài nguyên.

### 3. Bài học kinh nghiệm:
* Kiến trúc Serverless giúp giảm bớt gánh nặng quản lý hạ tầng nhưng đòi hỏi kỹ năng quản lý IAM role hiệu quả để thực thi hàm (function execution).
* Giới hạn lưu lượng (Throttling) ở cấp độ API là biện pháp bảo mật quan trọng để ngăn chặn các cuộc tấn công DoS vào hệ thống Serverless backend.

<!-- ### 4. Bằng chứng (Chèn hình ảnh vào static/images/week6/)
* **Kiểm thử API Gateway Endpoint:**
![API Test](/images/week6/api-test.png)
* **Log thực thi Lambda:**
![Logs](/images/week6/lambda-logs.png) -->