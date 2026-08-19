## Bước 1: đọc và phân tích yêu cầu: hiểu về business context và business problem
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

## Bước 2: Xác định stakeholder trong dự án này
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

## Bước 3: Xác định Business Goal


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

 ## Bước 4: Xác định phạm vi hệ thống

Dựa trên yêu cầu khách hàng, phạm vi của **CAB System** có thể chia thành **In Scope** và **Out of Scope**. 

### In Scope

| Phạm vi                         | Nội dung                                                                     |
| ------------------------------- | ---------------------------------------------------------------------------- |
| **Account Management**          | Đăng ký, đăng nhập, cập nhật thông tin Customer/Driver                       |
| **Booking Management**          | Tạo yêu cầu đặt xe, chọn điểm đón, điểm đến và loại xe                       |
| **Driver & Vehicle Management** | Quản lý tài xế, phương tiện, trạng thái hoạt động và vị trí                  |
| **Driver Matching**             | Tìm, đề xuất và phân công tài xế phù hợp                                     |
| **Trip Management**             | Theo dõi và cập nhật trạng thái chuyến đi                                    |
| **Fare Management**             | Tính số tiền cần thanh toán sau chuyến                                       |
| **Payment**                     | Hỗ trợ tiền mặt và tích hợp thanh toán điện tử                               |
| **Notification**                | Thông báo các sự kiện của chuyến cho Customer/Driver                         |
| **Rating**                      | Customer đánh giá Driver sau chuyến                                          |
| **Administration**              | Quản lý Customer, Driver, Vehicle, Trip và Transaction                       |
| **Reporting**                   | Báo cáo chuyến đi, doanh thu, tỷ lệ hoàn thành/hủy, hiệu quả Driver          |
| **Security & Audit**            | Authentication, Authorization, bảo vệ dữ liệu và lưu vết thao tác quan trọng |

### Out of Scope / Chưa được xác định

Tài liệu **không xác định chi tiết** các nội dung sau nên chưa thể đưa vào phạm vi triển khai cụ thể:

* Công thức tính cước chi tiết.
* Thuật toán/tiêu chí ưu tiên Driver cụ thể.
* Thời gian Driver phải phản hồi.
* Chính sách hủy chuyến.
* Xử lý chi tiết khi mất kết nối mạng.
* Thời gian lưu trữ dữ liệu.
* Nhà cung cấp Payment/Notification cụ thể.

Các nội dung này cần **BA làm rõ với stakeholder** trước khi Development Team triển khai. 

**Phạm vi tổng quát:** CAB System quản lý quy trình **Customer đặt xe → tìm Driver → thực hiện Trip → tính cước → Payment → Notification → Rating**, đồng thời hỗ trợ quản trị và báo cáo cho doanh nghiệp.

## Bước 5: Chuyển đổi business requirement
Từ Business Requirement của khách hàng, có thể chuyển thành các System/Functional Requirements chính như sau:
| ID       | Business Requirement                                | System Requirement                                                                              |
| -------- | --------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| **BR01** | Khách hàng cần sử dụng dịch vụ đặt xe               | Hệ thống cho phép Customer đăng ký, đăng nhập và quản lý thông tin cá nhân                      |
| **BR02** | Khách hàng cần đặt xe thuận tiện                    | Hệ thống cho phép nhập điểm đón, điểm đến, chọn loại xe và tạo Booking                          |
| **BR03** | Cần giảm việc phân công tài xế thủ công             | Hệ thống tự động tìm Driver dựa trên vị trí, trạng thái sẵn sàng và tiêu chí vận hành           |
| **BR04** | Khách hàng cần biết tình trạng chuyến               | Hệ thống cho phép Customer theo dõi Driver, ETA và Trip Status                                  |
| **BR05** | Tài xế cần quản lý và thực hiện chuyến              | Driver có thể Accept/Reject Booking và cập nhật trạng thái chuyến                               |
| **BR06** | Doanh nghiệp cần quản lý cước và thanh toán         | Hệ thống tính Fare và hỗ trợ Cash/Electronic Payment                                            |
| **BR07** | Người dùng cần được cập nhật thông tin              | Hệ thống gửi Notification khi có các sự kiện quan trọng của chuyến                              |
| **BR08** | Doanh nghiệp cần quản lý hoạt động tập trung        | Admin quản lý Customer, Driver, Vehicle, Trip và Transaction                                    |
| **BR09** | Ban lãnh đạo cần theo dõi hoạt động                 | Hệ thống cung cấp báo cáo về Trip, Revenue, Cancellation và Driver Performance                  |
| **BR10** | Hệ thống phải phục vụ nhu cầu tăng cao              | Các thành phần cần có khả năng **scale độc lập**                                                |
| **BR11** | Một chức năng lỗi không được làm dừng toàn hệ thống | Payment/Notification failure cần được cô lập khỏi quy trình đặt xe chính                        |
| **BR12** | Dữ liệu và chức năng nhạy cảm cần được bảo vệ       | Hệ thống phải có Authentication, Authorization, Data Protection và Audit Log                    |
| **BR13** | Nền tảng phải phát triển được lâu dài               | Hệ thống cho phép bổ sung Service Type, Payment Method và Notification Provider trong tương lai |

| **Business Goal**                         | **Business Requirement**                                                                                     | **Mục đích/giá trị**                                        |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------- |
| **BG1 – Tự động hóa đặt xe**              | **BR01:** Hệ thống cho phép khách hàng tạo yêu cầu đặt xe.                                                   | Giúp khách hàng đặt xe nhanh chóng, giảm thao tác thủ công. |
| **BG1 – Tự động hóa đặt xe**              | **BR02:** Hệ thống tự động tìm và phân công tài xế phù hợp.                                                  | Giảm thời gian tìm tài xế và nâng cao hiệu quả vận hành.    |
| **BG1 – Tự động hóa đặt xe**              | **BR03:** Hệ thống tiếp tục tìm tài xế khác khi tài xế từ chối hoặc không phản hồi.                          | Tăng khả năng tìm được tài xế cho khách hàng.               |
| **BG2 – Nâng cao trải nghiệm khách hàng** | **BR04:** Hệ thống cho phép khách hàng theo dõi trạng thái và vị trí chuyến đi.                              | Khách hàng chủ động nắm được tình trạng chuyến xe.          |
| **BG2 – Nâng cao trải nghiệm khách hàng** | **BR05:** Hệ thống cho phép khách hàng xem lịch sử và đánh giá tài xế.                                       | Nâng cao trải nghiệm và chất lượng dịch vụ.                 |
| **BG3 – Nâng cao hiệu quả vận hành**      | **BR06:** Hệ thống cho phép nhân viên quản lý khách hàng, tài xế, phương tiện và chuyến đi.                  | Quản lý tập trung, giảm công việc thủ công.                 |
| **BG4 – Quản lý thanh toán**              | **BR07:** Hệ thống tính cước và hỗ trợ thanh toán tiền mặt hoặc điện tử.                                     | Quản lý doanh thu và thanh toán thuận tiện.                 |
| **BG5 – Tăng khả năng đáp ứng chuyến**    | **BR08:** Hệ thống lưu vị trí và trạng thái hoạt động của tài xế.                                            | Hỗ trợ tìm tài xế gần khách hàng và rút ngắn thời gian chờ. |
| **BG6 – Ổn định và bảo mật**              | **BR09:** Hệ thống xác thực, phân quyền và bảo vệ dữ liệu người dùng.                                        | Đảm bảo an toàn và bảo mật thông tin.                       ||
**BG7 – Khả năng mở rộng**                | **BR10:** Hệ thống cho phép tích hợp thêm dịch vụ, phương thức thanh toán và kênh thông báo.                 | Giúp hệ thống dễ phát triển trong tương lai.                |
| **BG8 – Hỗ trợ ra quyết định**            | **BR11:** Hệ thống cung cấp báo cáo về số chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả tài xế. | Giúp ban lãnh đạo theo dõi và ra quyết định.                |

