# CAB System API Documentation

Bộ tài liệu API này được xây dựng từ `SRS(1).md` của CAB System.

## Cấu trúc

```text
CAB-System-API/
├── openapi.yaml
├── paths/
│   ├── auth.yaml
│   ├── customers.yaml
│   ├── drivers.yaml
│   ├── vehicles.yaml
│   ├── bookings.yaml
│   ├── trips.yaml
│   ├── fares.yaml
│   ├── payments.yaml
│   ├── ratings.yaml
│   ├── notifications.yaml
│   ├── admin.yaml
│   ├── reports.yaml
│   └── audit.yaml
└── components/
    ├── schemas.yaml
    └── responses.yaml
```

- `openapi.yaml`: file root dạng modular, dùng `$ref` tới các file nhỏ.
- `paths/*.yaml`: endpoint tách theo nhóm chức năng.
- `components/schemas.yaml`: data models/schemas.
- `components/responses.yaml`: response lỗi dùng chung.
- `CAB-System-OpenAPI-Bundled.yaml`: bản tổng hợp một file để import/paste trực tiếp vào Swagger Studio.

## Các điểm SRS chưa chốt

Các chi tiết sau được giữ ở mức TBD thay vì tự đặt quy tắc nghiệp vụ:
- công thức tính cước chi tiết;
- tiêu chí/thuật toán ưu tiên Driver;
- thời gian Driver phải phản hồi;
- chính sách hủy chuyến;
- xử lý mất kết nối;
- thời gian lưu dữ liệu;
- Payment Provider cụ thể;
- Notification Provider/kênh cụ thể;
- cơ chế Authentication cụ thể.

Một số tên endpoint, status code và enum là quyết định API design để biểu diễn các use case trong SRS, không phải câu chữ nguyên văn của yêu cầu khách hàng.
