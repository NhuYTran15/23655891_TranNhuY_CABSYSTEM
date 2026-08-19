##Bước 1: đọc và phân tích yêu cầu: hiểu về business context và business problem
trả lời câu hỏi: khách hàng muốn giải quyết vấn đề gì
vì sao không thể đáp ứng, ai sử dụng hệ thống này,
giá trị sau khi tạo ra
**1. Khách hàng muốn giải quyết vấn đề gì?**
Công ty ABC muốn xây dựng **CAB System** để tự động hóa và quản lý tập trung toàn bộ quy trình đặt xe: **đặt xe → tìm tài xế → thực hiện chuyến → tính cước → thanh toán → đánh giá**. 

**2. Vì sao hệ thống hiện tại không thể đáp ứng?**

* Phân công tài xế chủ yếu **thủ công**.
* Khách hàng khó **theo dõi trạng thái chuyến đi**.
* Thông tin **thanh toán chưa được quản lý tập trung**.
* Khó **mở rộng hệ thống** khi số lượng khách hàng và tài xế tăng. 

**3. Ai sử dụng hệ thống?**

* **Customer:** đặt xe, theo dõi chuyến, thanh toán, đánh giá.
* **Driver:** nhận/từ chối chuyến, cập nhật vị trí và trạng thái chuyến.
* **Operation Staff/Admin:** quản lý khách hàng, tài xế, phương tiện, chuyến đi và báo cáo. 

**4. Giá trị sau khi tạo ra hệ thống?**

* Tự động hóa quy trình đặt và điều phối xe.
* Cải thiện trải nghiệm Customer và Driver.
* Quản lý dữ liệu và hoạt động tập trung.
* Giảm khó khăn cho bộ phận vận hành.
* Có khả năng **scale và mở rộng tính năng** trong tương lai.

##Bước 2: Xác định stakeholder trong dự án này
lập bảng cột đầu stakeholder nào, cột 2 vai trò là gì
vẽ ma trận stakeholder, cho biết mức độ ảnh hưởng của các vai trò trong hệ thống


Dựa trên yêu cầu của CAB System, các stakeholder chính gồm: 

| Stakeholder                 | Vai trò                                                               |
| --------------------------- | --------------------------------------------------------------------- |
| **Ban giám đốc ABC**        | Đưa ra mục tiêu, yêu cầu kinh doanh và định hướng phát triển hệ thống |
| **Customer**                | Đặt xe, theo dõi chuyến, thanh toán và đánh giá tài xế                |
| **Driver**                  | Nhận/từ chối chuyến, thực hiện chuyến và cập nhật trạng thái/vị trí   |
| **Operation Staff / Admin** | Quản lý khách hàng, tài xế, phương tiện, chuyến đi và xử lý sự cố     |
| **Business Analyst (BA)**   | Thu thập, phân tích và làm rõ yêu cầu với các bên liên quan           |
| **Development Team**        | Thiết kế, phát triển, tích hợp và triển khai CAB System               |
| **Payment Provider**        | Cung cấp dịch vụ xử lý thanh toán điện tử                             |
| **Notification Provider**   | Cung cấp kênh gửi thông báo cho Customer và Driver                    |

### Stakeholder Matrix

Có thể phân loại theo **Power (mức độ ảnh hưởng/quyền lực)** và **Interest (mức độ quan tâm đến hệ thống)**:

```text
                     POWER / INFLUENCE
                           HIGH
                            ↑
                            │
       KEEP SATISFIED       │        MANAGE CLOSELY
                            │
    Payment Provider        │    Ban giám đốc ABC
                            │    Operation Staff/Admin
                            │    BA
                            │    Development Team
                            │
LOW INTEREST ───────────────┼──────────────────── HIGH INTEREST
                            │
       MONITOR              │        KEEP INFORMED
                            │
 Notification Provider      │    Customer
                            │    Driver
                            │
                            ↓
                           LOW
```

### Mức độ ảnh hưởng

| Stakeholder               | Mức độ ảnh hưởng  | Lý do chính                                                        |
| ------------------------- | ----------------- | ------------------------------------------------------------------ |
| **Ban giám đốc ABC**      | 🔴 Cao            | Quyết định mục tiêu, phạm vi và yêu cầu kinh doanh                 |
| **Operation Staff/Admin** | 🔴 Cao            | Trực tiếp vận hành và quản lý hệ thống                             |
| **BA**                    | 🔴 Cao            | Làm rõ requirement và kết nối stakeholder với Development Team     |
| **Development Team**      | 🔴 Cao            | Quyết định và triển khai giải pháp kỹ thuật                        |
| **Payment Provider**      | 🟠 Trung bình–Cao | Ảnh hưởng trực tiếp đến chức năng thanh toán điện tử               |
| **Customer**              | 🟠 Trung bình     | Người sử dụng chính, yêu cầu ảnh hưởng lớn đến chức năng đặt xe    |
| **Driver**                | 🟠 Trung bình     | Người trực tiếp tham gia Driver Matching và Trip                   |
| **Notification Provider** | 🟡 Trung bình     | Ảnh hưởng đến Notification nhưng không quyết định toàn bộ hệ thống |

##Bước 3: Tìm Business Goal##


Dựa trên yêu cầu của khách hàng, các **Business Goal** chính của CAB System là: 

| Business Goal                                   | Mục tiêu                                                                           |
| ----------------------------------------------- | ---------------------------------------------------------------------------------- |
| **BG01 – Tự động hóa quy trình đặt xe**         | Giảm xử lý thủ công từ đặt xe, tìm tài xế đến hoàn thành chuyến                    |
| **BG02 – Cải thiện trải nghiệm khách hàng**     | Cho phép khách hàng đặt xe, theo dõi trạng thái, thanh toán và đánh giá thuận tiện |
| **BG03 – Tối ưu điều phối tài xế**              | Tìm và phân công tài xế phù hợp, ưu tiên tài xế gần và sẵn sàng                    |
| **BG04 – Quản lý vận hành tập trung**           | Quản lý Customer, Driver, Vehicle, Trip và Transaction trên một hệ thống           |
| **BG05 – Hỗ trợ theo dõi hoạt động kinh doanh** | Cung cấp báo cáo về chuyến đi, doanh thu, tỷ lệ hoàn thành/hủy và hiệu quả tài xế  |
| **BG06 – Đảm bảo khả năng mở rộng**             | Phục vụ số lượng lớn người dùng và cho phép mở rộng từng thành phần khi tải tăng   |
| **BG07 – Hỗ trợ phát triển lâu dài**            | Dễ bổ sung loại dịch vụ, phương thức thanh toán, kênh thông báo và tính năng mới   |

### Business Goal tổng quát

> **Xây dựng CAB System thành một nền tảng đặt xe tự động, quản lý tập trung, ổn định và có khả năng mở rộng lâu dài, đáp ứng toàn bộ quy trình từ đặt xe đến thanh toán và đánh giá.** 
